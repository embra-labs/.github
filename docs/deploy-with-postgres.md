# App chạy được rồi: dữ liệu sẽ ở đâu khi deploy lần tiếp theo?

Cập nhật 08/10/2026 · Hướng dẫn dùng được khi tự host hoặc dùng nền tảng khác.

**Bạn sẽ có:** một danh sách kiểm tra dữ liệu, migration và phục hồi trước khi deploy app có Postgres. Thực hành trên môi trường test với dữ liệu tổng hợp; bài này không yêu cầu tài khoản Embra.

Bạn có một app nhận đơn hàng. Trên máy cá nhân, trang web mở được, API ghi đơn
vào Postgres và ảnh được lưu vào một thư mục. Để đưa app lên mạng, hãy xác định
phần nào có thể tạo lại và phần nào phải sống qua lần thay phiên bản tiếp theo.

## Vẽ đường đi của một đơn hàng

```text
Trình duyệt → API → Postgres: mã đơn, trạng thái, tham chiếu ảnh
                 → nơi lưu file: nội dung ảnh
                 → hàng đợi, nếu có → worker gửi thông báo
```

Frontend hiển thị giao diện. API xử lý yêu cầu và quyền truy cập. Database giữ
dữ liệu có cấu trúc. Nơi lưu file giữ nội dung ảnh. Worker làm việc có thể xử lý
sau khi API trả lời. Một ứng dụng nhỏ có thể gộp frontend và API trong một
process; chỉ tách thêm khi công việc cần đến.

## Kiểm tra bốn điều trước lần deploy tiếp theo

**1. Khi thay container, dữ liệu nào còn?**

File trong lớp ghi của container có thể mất khi container bị xóa và tạo lại.
Ảnh người dùng cần nơi lưu bền vững như volume được quản lý hoặc object storage.
Database cũng cần storage bền vững. Việc app hiện tại đọc được ảnh chưa chứng
minh ảnh sẽ còn sau deploy. Thử thay container trong môi trường test rồi đọc
lại cùng một đơn và ảnh đã tạo trước đó. Xem cơ chế lưu trữ trong [tài liệu Docker](https://docs.docker.com/engine/storage/).

**2. Phiên bản mới đang kết nối tới môi trường nào?**

Ghi rõ cấu hình cho test và production: endpoint database, nơi lưu file và các
dịch vụ bên ngoài. Không in mật khẩu hoặc token để kiểm tra. Dùng tên môi
trường và định danh cấu hình đã che dữ liệu nhạy cảm. Kiểm cả cấu hình lúc build
và lúc chạy nếu framework của bạn sử dụng hai giai đoạn đó.

**3. App trả HTTP 200 có nghĩa là tạo được đơn không?**

Một trang health chỉ trả chuỗi “OK” có thể vẫn hoạt động khi database mất kết
nối. Dùng readiness phù hợp để kiểm tra phụ thuộc cần thiết, và một bài thử
tạo/đọc đơn bằng dữ liệu tổng hợp trong môi trường test. Không tạo đơn thật
hoặc gửi email cho khách mỗi lần hệ thống gọi healthcheck.

**4. Nếu phiên bản mới lỗi, quay lại code cũ có đủ không?**

Code cũ phải đọc được schema và dữ liệu hiện tại. Nếu migration đã xóa cột mà
code cũ dùng, quay lại image cũ không tự mang cột đó về. Trước deploy, kiểm tra
tính tương thích của thay đổi dữ liệu và đường phục hồi riêng.

Ví dụ: bản A còn đọc cột `legacy_ref`. Nếu bản B xoá cột đó, quay lại A có thể tiếp tục lỗi. Một hướng triển khai là thêm cấu trúc mới, chuyển code và dữ liệu theo từng bước, xác nhận không còn bản đang chạy nào cần cấu trúc cũ, rồi mới bỏ phần cũ. Đây không phải bảo đảm mọi migration đều không gián đoạn; vẫn cần thử trên dữ liệu có kích thước và tải phù hợp.

## Bài thực hành nhỏ

Trên môi trường test với dữ liệu giả:

1. Tạo một đơn có mã thử riêng, ví dụ `DEPLOY-TEST-001`; ghi lại trạng thái và tổng tiền. Nếu app có upload, lưu một ảnh và checksum của ảnh.
2. Thay container app bằng phiên bản tiếp theo.
3. Đọc lại đúng đơn đó và đối chiếu từng trường; nếu có upload, tải ảnh và so checksum. Không chỉ kiểm tổng số dòng.
4. Thử một phiên bản có readiness lỗi và quan sát có traffic đi vào nó không.
5. Quay lại phiên bản trước nếu schema tương thích, rồi đọc lại dữ liệu.

Bài này kiểm tính liên tục của dữ liệu qua deploy. Để kiểm backup, cần một bài
khác: phục hồi vào môi trường cách ly và đối chiếu dữ liệu. Backup tồn tại và
backup phục hồi được là hai điều cần kiểm riêng.

## Diễn tập phục hồi riêng

Có storage bền vững chưa chứng minh bạn phục hồi được khi mất dữ liệu. Với một bản backup, hãy thử restore vào database riêng, kết nối bản app thử vào đó và đọc lại mã đơn đã ghi nhận. Nếu app lưu ảnh bên ngoài Postgres, kiểm cả file tương ứng: backup database không tự chứa những file đó.

Với SQL dump, cần chuẩn bị các role/quyền phù hợp và kiểm lỗi restore, không chỉ nhìn thấy file backup. Xem [backup và restore bằng SQL dump của PostgreSQL](https://www.postgresql.org/docs/18/backup-dump.html).

Nếu dùng phục hồi theo thời điểm (PITR), cần base backup và chuỗi WAL cần thiết để tới được mốc phục hồi. Chọn rõ mốc thời gian, kiểm dữ liệu trước/sau mốc và ghi lại phần ghi mới không có trong database đã phục hồi. Đọc [hướng dẫn PITR của PostgreSQL](https://www.postgresql.org/docs/18/continuous-archiving.html) cho cách cấu hình và thực hiện; bài này không thay runbook của hệ thống bạn.

## Ghi kết quả trước khi gọi là sẵn sàng

Bảng dưới là mẫu để tự điền, không phải kết quả thử nghiệm của Embra. Ghi ngày, phiên bản app/schema và môi trường cùng kết quả. “Chưa chạy” khác với “đạt”.

| Phép kiểm | Bằng chứng cần lưu | Kết quả của bạn |
| :--- | :--- | :--- |
| Thay container | Đơn thử vẫn có đúng trạng thái/tổng tiền; checksum ảnh khớp nếu có | Chưa chạy |
| Cấu hình môi trường | App trỏ đúng DB/storage thử; không lộ credential | Chưa chạy |
| Phiên bản chưa sẵn sàng | Request không được chuyển sang bản chưa qua readiness | Chưa chạy |
| Quay lại code cũ | Bản cũ chạy được với schema hiện tại trong phạm vi đã thử | Chưa chạy |
| Restore backup | App đọc được đơn thử từ DB phục hồi riêng; file tham chiếu tồn tại nếu có | Chưa chạy |
| Mốc và thời gian phục hồi | Ghi mốc dữ liệu, thời gian thực hiện và phần dữ liệu không được khôi phục | Chưa chạy |

Bộ kiểm này giúp tìm các lỗ hổng thường gặp, chưa chứng minh hệ thống chịu được mọi sự cố hoặc mọi mức tải. Thời gian restore của database thử nhỏ không phải cam kết thời gian cho database production.

## Embra đang xây dựng phần nào?

Embra đang xây dựng luồng deploy cho ứng dụng có Postgres, tập trung vào tác động của migration, bước duyệt và đường phục hồi. Hiện là closed alpha với onboarding thủ công; chưa có dịch vụ self-service hoặc CLI public. Sơ đồ và các phép kiểm trong bài là hướng dẫn chung, không phải danh sách tính năng Embra đã phát hành.

[Xem phạm vi và cách bắt đầu với Embra →](https://github.com/embra-labs/.github/blob/main/docs/start-here.md)
