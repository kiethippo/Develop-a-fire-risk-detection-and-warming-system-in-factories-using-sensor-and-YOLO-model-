# 🔥 Hệ thống Cảnh Báo Cháy Sử Dụng YOLO & Cảm Biến

Đồ án phát triển hệ thống giám sát và cảnh báo cháy nổ thông minh trong nhà máy, kết hợp giữa mô hình phát hiện hình ảnh (YOLOv11) và cảm biến (nhiệt độ, chất lượng không khí), triển khai trên nền tảng phần cứng nhúng như Raspberry Pi và ESP32.

## 🎯 Mục Tiêu Dự Án

- Nhận diện sớm nguy cơ cháy (lửa, khói, hành vi hút thuốc...)
- Kết hợp cảm biến và thị giác máy tính để tăng độ chính xác.
- Gửi cảnh báo thời gian thực đến ứng dụng web/mobile.
- Hạn chế thiệt hại tài sản và tính mạng do cháy gây ra.

## 📷 Các Loại Nhận Diện

- `fire`: lửa và ngọn lửa.
- `smoke`: khói.
- `smoking`: hút thuốc lá, điếu thuốc.
- `zippo`: hộp quẹt, thiết bị phát lửa.

## 🧠 Công Nghệ Sử Dụng

| Hạng mục         | Công cụ / Nền tảng           |
|------------------|------------------------------|
| Mô hình AI       | YOLOv11 / YOLOv8             |
| Gán nhãn dữ liệu | Roboflow                     |
| Huấn luyện       | Jupyter Notebook + Python    |
| Phần cứng        | Raspberry Pi 5, ESP32        |
| Cảm biến         | DHT22 (nhiệt độ), MQ-135 (khí) |
| Truyền thông     | MQTT, MongoDB, Socket        |
| Ứng dụng         | Web + Mobile (Realtime)      |

## 🧱 Kiến Trúc Hệ Thống

```
Camera + Cảm biến
     ↓
ESP32 + Raspberry Pi 5
     ↓
Nhận diện YOLO + Tổng hợp dữ liệu cảm biến
     ↓
Lưu trữ MongoDB
     ↓
Hiển thị App/Web và cảnh báo thời gian thực
```

## 🛠️ Phần Cứng Triển Khai

- **Raspberry Pi 5**: máy tính trung tâm chạy AI và gửi dữ liệu.
- **ESP32**: kết nối và xử lý cảm biến nhiệt độ / khí.
- **Camera**: nhận diện khói, lửa, zippo...
- **Cảm biến**: MQ-135 (khí độc), DHT22 (nhiệt độ).

## 📈 Kết Quả Huấn Luyện

- Số lượng ảnh ~500/class.
- Kết quả:
  - `mAP@50 ≈ 1.0`
  - `Precision ≈ 1.0`, `Recall ≈ 1.0`
- Tổng quát hóa tốt, không overfitting.
- Confusion Matrix: tỷ lệ nhầm thấp, một số nhầm lẫn background là fire/smoke.

## ⚖️ So Sánh YOLOv11m vs YOLOv8m

| Chỉ số           | YOLOv11m     | YOLOv8m        |
|------------------|--------------|----------------|
| Tốc độ train     | Nhanh hơn    | Chậm hơn       |
| FPS thực tế      | Thấp hơn     | Cao hơn        |
| Số tham số       | Nhiều hơn    | Ít hơn         |
| Độ chính xác     | Rất tốt      | Ổn định        |

## 📲 Tính Năng Ứng Dụng

- Nhận cảnh báo cháy thời gian thực.
- Xem lại hình ảnh, thời gian xảy ra sự cố.
- Đăng nhập, phân quyền thiết bị theo mã camera.
- Lưu trữ thông tin bằng MongoDB.

## 👨‍💻 Tác Giả

- Huỳnh Ngọc Anh Kiệt – 22520718  
- Nguyễn Thành Nhân – 22521003  
> Giáo viên hướng dẫn: ThS. Đặng Lê Bảo Chương  
> Trường Đại học Công nghệ Thông tin – ĐHQG TP.HCM
