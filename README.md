# Bài 4 : Chuẩn hóa quy trình quản lý bệnh án điện tử


# Giải Pháp Hệ Thống Bệnh Án Điện Tử Clinic-Cloud

---

## 📌 1. Phân Tích: Yêu Cầu Chức Năng vs Phi Chức Năng

| Tiêu chí | Functional Requirements (Yêu cầu chức năng) | Non-functional Requirements (Yêu cầu phi chức năng) |
| :--- | :--- | :--- |
| **Bản chất** | Hệ thống **làm được những gì** (Hành vi cụ thể). | Hệ thống **hoạt động tốt ra sao** (Tiêu chuẩn chất lượng/bảo mật). |
| **Mục đích** | Phục vụ trực tiếp quy trình khám chữa bệnh. | Đảm bảo an toàn, bảo mật dữ liệu y tế theo chuẩn. |
| **Ví dụ tại Clinic-Cloud** | - Bác sĩ tạo, chỉnh sửa và ký số bệnh án điện tử.<br>- Kê đơn thuốc online và tra cứu tiền sử bệnh nhân. | - Mã hóa dữ liệu bệnh án theo chuẩn AES-256.<br>- Phân quyền truy cập theo vai trò (RBAC) & sao lưu tự động hàng ngày. |

---

## 🛠️ 2. Triển Khai Hệ Thống Clinic-Cloud

### Word: Cấu Trúc SRS Bảo Mật Bệnh Án (Non-functional Focus)
* **Heading 1:** `1. Yêu Cầu Bảo Mật Dữ Liệu Y Tế (Non-functional Requirements)`
  * **Heading 2:** `1.1 Chuẩn mã hóa lưu trữ và truyền tải (AES-256, TLS 1.3)`
  * **Heading 2:** `1.2 Cơ chế xác thực 2 yếu tố (2FA) cho y bác sĩ`
  * **Heading 2:** `1.3 Kiểm toán hệ thống & Lưu vết truy cập (Audit Logs)`
* Áp dụng đồng bộ qua **Styles Pane** để quản lý mục lục tự động và kiểm soát phân cấp an ninh.

### Excel: Quản Lý 1.000 Hồ Sơ Bệnh Nhân (Xử Lý Bẫy Ô Trống)
* **Nguyên tắc Database:** Không `Merge Cell`, dòng 1 là tiêu đề duy nhất (`A1:E1`).
* **Xử lý bẫy AutoFilter bị ngắt quãng do ô trống:**
  * *Vấn đề:* Bấm `Ctrl + Shift + L` khi đang đứng ở 1 ô lẻ sẽ khiến Excel tự nhận diện vùng dữ liệu; gặp hàng/ô trống lớn sẽ ngắt bộ lọc giữa chừng.
  * *Cách xử lý chuẩn:* 
    1. Bôi đen chính xác toàn bộ vùng dữ liệu hoặc chọn toàn bộ các cột từ đầu đến cuối (ví dụ bấm chọn cả cột `A:E`).
    2. Nhấn tổ hợp phím **`Ctrl + Shift + L`** để bật AutoFilter bao trùm đủ 1.000 dòng.
    3. Điền giá trị mặc định cho các ô trống (như `"Chưa cập nhật"` hoặc `"N/A"`) bằng cách: Bấm `F5` $\rightarrow$ `Special...` $\rightarrow$ chọn `Blanks` $\rightarrow$ nhập `"Chưa cập nhật"` $\rightarrow$ nhấn `Ctrl + Enter`.

### PowerPoint: Donut Chart Tối Giản Trình Bày Dịch Bệnh
* **Tiêu đề kết luận (Assertion Title):**
  > **"Cúm mùa chiếm 68% ca khám, áp đảo hoàn toàn các ca bệnh hô hấp trong tháng 10"**
* **Trực quan hóa (Donut Chart tối giản):**
  * Chỉ chia 2 lát cắt: Lát Cúm mùa (68% - màu Đỏ cam nổi bật) và Lát Các bệnh khác (32% - màu Xám nhạt trung tính).
  * Đục rỗng tâm biểu đồ (Hole size ~60%), đặt con số trọng tâm **`68%`** (Font $\ge$ 36pt, in đậm) ngay giữa tâm Donut.
  * Ghi chú ngắn gọn 1 dòng: *Tập trung dự trữ thuốc hạ sốt và que test cúm A/B cho tuần tiếp theo.*

---

## 🔍 3. Kiểm Thử: Khắc Phục Lỗi Gán Nhầm Heading Bằng `Ctrl + Shift + N`

* **Vấn đề phát sinh:** Khi soạn thảo tài liệu Word, vô tình nhấn nhầm làm một đoạn văn dài bị chuyển thành `Heading 1` hoặc `Heading 2`, dẫn đến đoạn văn đó xuất hiện sai lệch trên cả mục lục tự động (TOC) lẫn thanh Navigation Pane.
* **Quy trình xử lý tức thì:**
  1. Đặt con trỏ chuột hoặc bôi đen toàn bộ đoạn văn bản đang bị lỗi style.
  2. Nhấn tổ hợp phím tắt **`Ctrl + Shift + N`**.
  3. **Kết quả:** Word lập tức xóa bỏ định dạng tiêu đề và trả đoạn văn bản về style văn bản gốc (**Normal Style**). Sau đó chỉ cần chuột phải vào mục lục $\rightarrow$ chọn **Update Field** để mục lục tự làm sạch các mục gán nhầm.
