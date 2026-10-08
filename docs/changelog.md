# Cập nhật Embra

Những thay đổi đã được xuất bản, mới nhất ở trên. Ngày theo giờ Việt Nam (UTC+7).

[Bắt đầu với Embra](https://github.com/embra-labs/.github/blob/main/docs/start-here.md) · [Hỗ trợ](https://github.com/embra-labs/.github/blob/main/SUPPORT.md) · [Website](https://embra.cloud/)

Các mục dưới đây là cập nhật tài liệu và trải nghiệm GitHub. **Tại ngày 08/10/2026, Embra vẫn ở closed alpha, onboarding thủ công; CLI chưa có bản phát hành công khai.** Bản phần mềm khi phát hành sẽ có phiên bản và liên kết tới [CLI Releases](https://github.com/embra-labs/cli/releases).

## 08/10/2026 — Demo backfill chạy lại được

- Xuất bản [backfill-demo](https://github.com/embra-labs/backfill-demo): PostgreSQL, app workload, kill executor trước/sau commit và chạy tiếp từ checkpoint.
- Ba ca hợp lệ và hai đối chứng sai, có verifier, kết quả mẫu và CI. Fixture độc lập 1.000 dòng, không phải tái lập benchmark tám triệu dòng hoặc bản phát hành sản phẩm.
- Nối demo từ bài engineering, profile và trang Bắt đầu.

## 08/10/2026 — Engineering trên website

- Mở mục [Engineering](https://embra.cloud/engineering/) và xuất bản [Backfill 8 triệu dòng: dữ liệu đúng, nhưng latency không đạt](https://embra.cloud/engineering/backfill-8m/).
- Bài có sơ đồ, biểu đồ từ số liệu lab, CSV và phương pháp đối chiếu; ghi rõ những phần chưa đạt và giới hạn kiểm chứng.
- Nối bài từ website, profile GitHub và trang Bắt đầu. Đây là cập nhật nội dung, không phải bản phát hành phần mềm.

## 08/10/2026 — Hướng dẫn deploy và báo lỗi

**Tài liệu**

- Xuất bản [hướng dẫn chuẩn bị app có Postgres trước khi deploy](https://github.com/embra-labs/.github/blob/main/docs/deploy-with-postgres.md): kiểm dữ liệu sau khi thay container, khả năng quay lại code cũ và diễn tập restore riêng. Có bảng để ghi kết quả; dùng được cả khi tự host.
- Thêm đường dẫn đến bài hướng dẫn trong trang Bắt đầu.

**Hỗ trợ**

- Thêm [trang hỗ trợ](https://github.com/embra-labs/.github/blob/main/SUPPORT.md), chỉ rõ nơi báo lỗi website, CLI, tài liệu và cách liên hệ riêng.
- Bổ sung mẫu **Báo lỗi / Bug report** dùng chung cho các repo không có mẫu riêng: thông tin môi trường, bước tái hiện, kết quả mong đợi và kết quả thực tế.
- Thêm liên kết hỗ trợ từ trang Bắt đầu; hướng dẫn gửi báo cáo nhạy cảm qua email đã công bố, thay vì issue công khai.

## 07/10/2026 — Trang bắt đầu và profile GitHub

**Bắt đầu sử dụng**

- Xuất bản [Bắt đầu với Embra](https://github.com/embra-labs/.github/blob/main/docs/start-here.md) bằng tiếng Việt: phạm vi hiện tại, cách đăng ký quan tâm alpha và những gì xảy ra sau khi đăng ký.
- Nối trang này từ profile org và README CLI để người mới dễ tìm bước tiếp theo.

**GitHub**

- Thêm banner và phần giới thiệu sản phẩm trên [profile Embra](https://github.com/embra-labs).
- Bổ sung mô tả cho repo CLI và website; README CLI ghi rõ trạng thái phát triển và chưa có bản cài công khai.

---

Muốn hiểu Embra có phù hợp với dự án của bạn? [Xem phạm vi và cách bắt đầu →](https://github.com/embra-labs/.github/blob/main/docs/start-here.md)
