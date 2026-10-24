# Bắt đầu với Embra

Embra là hosting app và PostgreSQL cho developer và team nhỏ tại Việt Nam: deploy từ GitHub, database riêng có review migration, backup liên tục và restore theo thời điểm. Máy chủ đặt tại TP.HCM.

[Website](https://embra.cloud/) · [Bảng giá](https://embra.cloud/bang-gia/) · [GitHub](https://github.com/embra-labs) · [Hỗ trợ / Báo lỗi](https://github.com/embra-labs/.github/blob/main/SUPPORT.md)

**Beta trả phí từ 25/10/2026.** Embra nhận app production trong giới hạn từng gói. Mỗi khách được onboarding trực tiếp, chưa mở đăng ký tự phục vụ. Beta chưa có SLA.

## Có phù hợp với dự án của bạn?

Bạn đang xây website, web app hoặc API, và người viết code cũng là người cấu hình server và deploy. Embra gom app và database vào một project để bạn không phải tự nối phần vận hành giữa hai thứ. Beta tập trung vào frontend, Node.js / Next.js và PostgreSQL. Bạn có thể bắt đầu từ frontend rồi thêm backend sau.

## Có gì trong beta

- Deploy từ GitHub qua dashboard, Embra tự build từ mã nguồn.
- PostgreSQL riêng. Migration được chạy thử trên bản sao và hiện tác động trước khi bạn duyệt.
- Backup liên tục, restore về thời điểm bất kỳ trong 7 ngày gần nhất ra một bản riêng để kiểm tra.
- Worker, cron và bucket lưu file theo từng gói.
- Domain riêng + HTTPS, log và metrics.
- CLI và MCP (`embra mcp`) sắp có bản phát hành công khai; trong lúc chờ, dashboard đủ để deploy và vận hành. Qua MCP, agent được build, tạo plan, chạy thử migration và đọc log, nhưng không được duyệt, xoá, export hay restore. Deploy production luôn chờ owner duyệt.
- Tự xuất app và dữ liệu trên dashboard (Cài đặt → Export): image, manifest, pg_dump và danh sách object, không kèm giá trị secret.

Chưa có: queue, auth, email, realtime.

## Chọn bước tiếp theo

| Bạn muốn… | Bắt đầu ở đây |
| :--- | :--- |
| Xem giá và giới hạn từng gói | [Bảng giá](https://embra.cloud/bang-gia/): Start 249.000đ, Build 399.000đ, Grow 749.000đ mỗi project mỗi tháng |
| So Embra với Vercel, Supabase, Railway, Render, VPS | [So sánh](https://embra.cloud/so-sanh/) |
| Bắt đầu dùng | Gửi link repository và gói bạn chọn tới [hello@embra.cloud](mailto:hello@embra.cloud), hoặc [đăng ký trên website](https://embra.cloud/#join) |
| Hiểu một lần deploy đi qua những đâu | [Bài kiến trúc](https://embra.cloud/engineering/how-embra-works/) |
| Đọc thử nghiệm kỹ thuật và xem số liệu | [Engineering](https://embra.cloud/engineering/). Kết quả lab, không phải cam kết production |
| Chuẩn bị app có database trước khi deploy | [Hướng dẫn deploy với Postgres](https://embra.cloud/engineering/deploy-with-postgres/), dùng được cả khi tự host |
| Hiểu quyền truy cập dữ liệu, restore và hỗ trợ | [Trước khi bắt đầu](https://embra.cloud/#hoi-dap) |
| Xem Embra vừa cập nhật gì | [Changelog](https://github.com/embra-labs/.github/blob/main/docs/changelog.md) |

## Bắt đầu như thế nào

1. Bạn gửi link repository và gói muốn dùng. Embra trả lời để xác nhận stack và giới hạn.
2. Embra setup cùng bạn, thường trong một buổi. Trước khi chuyển dữ liệu thật, hai bên thử restore trên bản sao database và thống nhất cách lấy dữ liệu ra.
3. Hoá đơn tính từ ngày bắt đầu dùng. Bạn trả bằng chuyển khoản VietQR, và Embra tự xác nhận khi tiền về.

## Những điều cần biết

**Chi phí:** giá niêm yết là số tiền bạn chuyển. Embra chưa có pháp nhân nên chưa xuất hoá đơn VAT. Xem [bảng giá](https://embra.cloud/bang-gia/).

**Phục hồi:** rollback code và restore database là hai việc khác nhau. Restore về mốc cũ có thể bỏ các lần ghi sau mốc đó.

**Dữ liệu ứng dụng:** owner tự xuất app và dữ liệu trên dashboard (Cài đặt → Export). Mỗi lần đội Embra xem log, metrics hay database của bạn để hỗ trợ đều được ghi lại kèm lý do. Bạn chịu trách nhiệm code và logic ứng dụng.

**Dữ liệu đăng ký:** xem [thông báo xử lý dữ liệu](https://embra.cloud/chinh-sach-du-lieu.html). Không gửi mật khẩu, token hoặc dữ liệu khách hàng qua form hay GitHub Issues.

**Hỗ trợ:** qua [hello@embra.cloud](mailto:hello@embra.cloud). Trong beta, người trả lời là người xây Embra. Embra cố gắng phản hồi trong ngày làm việc, nhưng đây chưa phải cam kết SLA.

---

[Xem bảng giá →](https://embra.cloud/bang-gia/)

Cập nhật ngày 25/10/2026.
