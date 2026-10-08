# Bắt đầu với Embra

Hosting cho developer và team nhỏ tại Việt Nam, tập trung vào ứng dụng có Postgres.

[Website](https://embra.cloud/) · [Đăng ký alpha](https://embra.cloud/#join) · [GitHub](https://github.com/embra-labs) · [Hỗ trợ / Báo lỗi](https://github.com/embra-labs/.github/blob/main/SUPPORT.md)

**Closed alpha · onboarding thủ công.** Embra đang được xây dựng. Hiện chưa có dịch vụ để bạn tự đăng ký và deploy ngay, chưa nhận app production và chưa phát hành CLI công khai.

## Chọn bước tiếp theo

| Bạn muốn… | Bắt đầu ở đây |
| :--- | :--- |
| Xem Embra vừa cập nhật gì | [Changelog](https://github.com/embra-labs/.github/blob/main/docs/changelog.md) |
| Đọc thử nghiệm kỹ thuật và xem số liệu | [Engineering: backfill 8 triệu dòng](https://embra.cloud/engineering/backfill-8m/) — kết quả lab, không phải cam kết production |
| Tự chạy ví dụ checkpoint và backfill | [backfill-demo](https://github.com/embra-labs/backfill-demo) — Docker Compose, có CI và đối chứng sai; fixture riêng 1.000 dòng |
| Hiểu Embra đang làm gì | [Phạm vi và tiến độ](https://embra.cloud/#trang-thai) |
| Xem cách luồng deploy dự kiến hoạt động | [Demo tương tác trên website](https://embra.cloud/) — minh hoạ, không chạy trên app thật |
| Chuẩn bị app có database trước khi deploy | [Hướng dẫn deploy với Postgres](https://github.com/embra-labs/.github/blob/main/docs/deploy-with-postgres.md) — dùng được cả khi tự host |
| Thử Embra với dự án của mình | [Đăng ký quan tâm alpha](https://embra.cloud/#join) |
| Tìm CLI và bản phát hành | [Repo CLI](https://github.com/embra-labs/cli) · [Releases](https://github.com/embra-labs/cli/releases) — hiện chưa có bản cài |
| Trao đổi trước khi đăng ký | [hello@embra.cloud](mailto:hello@embra.cloud) |

## Embra tập trung vào điều gì?

Một lần deploy có thể thay đổi cả code lẫn dữ liệu mà code phụ thuộc vào. Embra đang thiết kế luồng làm việc để bạn hiểu tác động của migration trước khi chạy, duyệt thay đổi rõ ràng và biết cách phục hồi khi có sự cố.

Phạm vi triển khai đầu tiên tập trung vào **CLI, ứng dụng đóng gói thành container image và PostgreSQL**. Build trực tiếp từ source, dashboard, MCP và domain riêng của khách chưa nằm trong đợt triển khai đầu. Phạm vi dùng thử thực tế sẽ được ghi trong lời mời.

## Sau khi đăng ký alpha

1. Bạn mô tả dự án muốn thử qua form trên website.
2. Khi có đợt thử nghiệm phù hợp, Embra liên hệ để xác nhận stack, giới hạn tài nguyên, thời gian thử, chi phí và cách hỗ trợ.
3. Trước khi bắt đầu, bạn nhận hướng dẫn truy cập, phiên bản CLI được hỗ trợ và cách lấy dữ liệu ra khi kết thúc.

Đăng ký là yêu cầu được liên hệ, chưa phải quyền truy cập ngay. Ngày mở đợt tiếp theo chưa được công bố.

## Những điều cần biết

**Chi phí:** chưa có bảng giá thương mại được chốt. Các con số trong demo là ví dụ; chi phí dùng thử phải được xác nhận trước khi chạy tài nguyên.

**Phục hồi:** rollback code và restore database là hai việc khác nhau. Restore về mốc cũ có thể bỏ các lần ghi sau mốc đó. Demo và kết quả lab không phải cam kết cho mọi ứng dụng.

**Dữ liệu đăng ký:** xem [thông báo xử lý dữ liệu](https://embra.cloud/chinh-sach-du-lieu.html), bao gồm việc email đi qua Gmail. Không gửi mật khẩu, token hoặc dữ liệu khách hàng qua form hay GitHub Issues.

**Liên hệ:** [hello@embra.cloud](mailto:hello@embra.cloud). Phạm vi và thời gian hỗ trợ sẽ được xác nhận trong lời mời alpha.

---

[Đăng ký quan tâm alpha →](https://embra.cloud/#join)

Cập nhật ngày 08/10/2026.
