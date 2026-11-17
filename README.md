# Quản Lý Bán Hàng Thi Đạt

Phần mềm một file HTML (`index.html`) cho Công ty TNHH Thi Đạt (MST 0312510655), dùng được trên điện thoại và iPad.
Bản đang chạy là artifact "Quản Lý Bán Hàng Thi Đạt" trên claude.ai. Dữ liệu lưu trong cơ sở dữ liệu đám mây của artifact (kiểu Firestore), nhiều người dùng chung.

## Phạm vi

Chỉ quản lý dữ liệu **ngân hàng** và **hóa đơn vào/ra** lấy từ eHoadon, BKAV, cổng thuế GDT và thư mục OneDrive "THI DAT".
Báo giá và Hợp đồng là các mô-đun trống chờ dữ liệu thật. Khách hàng, Nhà cung cấp lấy theo MST trên hóa đơn; Nhân sự lấy bảng công từ phần mềm Chấm Công Công Trình. Không có dữ liệu mẫu.

| Menu | Nội dung |
|---|---|
| Tổng quan, Cảnh báo | Hóa đơn 2026, tiền vào/ra theo ngân hàng, thẻ cập nhật dữ liệu; công nợ khách hàng / NCC, thanh toán nghi trùng |
| Hóa đơn | Đầu vào, Đầu ra (tab Tổng quát / Chi tiết), Danh mục hàng hóa (tạm, gom tên giống nhau từ HĐ đầu vào), Mã hàng, Xuất nhập tồn |
| Ngân hàng | Công ty, Cá nhân, Tổng |
| Khác | Báo giá, Hợp đồng, Khách hàng, Nhà cung cấp, Nhân sự (bảng công lấy từ phần mềm Chấm Công Công Trình, kèm phân quyền) |

## Quy tắc dữ liệu

- Khóa hóa đơn: `chiều|ký hiệu|số|MST`. Bỏ qua hóa đơn trạng thái BTT, ĐH, hủy, bị thay thế.
- Sao kê: bỏ qua giao dịch trùng cùng tài khoản, ngày, số tiền.
- Thanh toán nghi trùng: chi ra từ 200.000 đ, cùng số tiền trong 3 ngày, cùng số hóa đơn hoặc cùng đối tác. Giao dịch xác nhận trùng bị loại khỏi báo cáo.
- Mã hàng `MH0001…` gộp các tên hàng khác nhau của nhà cung cấp; quy đổi đơn vị theo hệ số (có mẫu ống đồng kg / cuộn 15 m / m).
- Phân quyền: Quản trị và Kế toán nạp dữ liệu; người khác chỉ xem.

## An toàn

- Không lưu mật khẩu, OTP hay số tài khoản đầy đủ. Tài khoản ngân hàng chỉ lưu 4 số cuối.
- Không đưa file dữ liệu thật (sao kê, hóa đơn, gói `pack2026.json`) vào repo này. Dữ liệu chỉ nằm trong cơ sở dữ liệu của artifact.
- Phần mềm chỉ đọc thư mục OneDrive "THI DAT", không đổi tên hay di chuyển các thư mục QLBH, NGÂN HÀNG, KIOTVIET.
