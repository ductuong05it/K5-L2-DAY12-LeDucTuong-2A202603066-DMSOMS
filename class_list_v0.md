# Danh sách lớp v0 — Mô hình DMS & OMS

## 1. Lớp OMS (Occupant Monitoring System)
| STT | Tên lớp | Loại | Để làm gì (Mục đích) |
|---|---|---|---|
| 1 | `person` | Rectangle | Nhận diện hành khách trên ghế và kiểm tra trạng thái thắt dây an toàn |
| 2 | `child_seat` | Rectangle | Phát hiện sự hiện diện của ghế trẻ em (loại tựa lưng) ở hàng ghế sau |
| 3 | `infant_seat` | Rectangle | Phát hiện nôi em bé và hướng đặt nôi (quay ngược/quay xuôi) |
| 4 | `object` | Rectangle | Nhận diện đồ vật bỏ quên trên ghế (túi xách, hộp, cốc nước) |
| 5 | `frame_meta` | Tag | Lưu thông tin ánh sáng và phương thức chụp (RGB/IR) của cabin |
| 6 | `seat_occupancy` | Attribute | Phân loại trạng thái ghế trống hay có người/vật để cảnh báo an toàn |

## 2. Lớp DMS (Driver Monitoring System)
| STT | Tên lớp | Loại | Để làm gì (Mục đích) |
|---|---|---|---|
| 1 | `person` | Rectangle | Định vị người lái xe và xác định vị trí ghế lái (`driver`) |
| 2 | `face` | Rectangle | Cắt vùng mặt để phân tích nhắm/mở mắt, đeo kính và vùng nhìn (`gaze_zone`) |
| 3 | `face13` | Skeleton | Trích xuất 13 điểm đặc trưng mặt để tính chỉ số EAR (buồn ngủ) và hướng đầu |
| 4 | `hand` | Rectangle | Nhận diện vị trí bàn tay và kiểm tra tay có đặt trên vô lăng (`on_wheel`) |
| 5 | `phone` | Rectangle | Phát hiện hành vi tài xế sử dụng hoặc cầm điện thoại gây mất tập trung |
| 6 | `seatbelt` | Attribute | Kiểm tra tài xế có thắt dây an toàn đúng quy cách hay không |

## 3. Câu hỏi leo thang (Escalation Questions)
1. **Trường hợp tài xế đeo kính râm tối màu dưới ánh sáng NIR:**
   - *Câu hỏi:* Nên ghi `eye_left/right = unknown` hay cố đoán `open` dựa vào viền mờ tròng đen?
2. **Trường hợp đồ vật nằm trong nôi em bé:**
   - *Câu hỏi:* Nên tách thành 2 box (`infant_seat` + `object`) hay gộp chung và đánh dấu `occupied = yes`?
