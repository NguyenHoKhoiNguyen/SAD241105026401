# Phân tích kiến trúc

## 1. Đề xuất kiến trúc

Hệ thống Payroll sẽ áp dụng kiến trúc **Layered Architecture (Kiến trúc phân lớp)**, chia thành các lớp sau:

1. **Presentation Layer**
   - Giao diện người dùng (Windows-based desktop application).
   - Cho phép nhân viên và Payroll Administrator tương tác với hệ thống (nhập thông tin timecard, xem báo cáo, thay đổi phương thức thanh toán).

2. **Application Layer**
   - Xử lý logic nghiệp vụ như tính toán lương, hoa hồng, và xử lý timecard.
   - Đảm bảo tính toàn vẹn của dữ liệu và tính bảo mật trong các hành động của người dùng.

3. **Integration Layer**
   - Cầu nối giữa hệ thống Payroll và các hệ thống bên ngoài:
     - **Project Management Database** (DB2 trên IBM mainframe).
     - **Bank Systems** (hỗ trợ giao dịch chuyển khoản).

4. **Data Access Layer**
   - Truy cập và quản lý dữ liệu liên quan đến nhân viên, timecard, thông tin thanh toán, và các đơn đặt hàng.

5. **Database Layer**
   - Lưu trữ thông tin của hệ thống Payroll, bao gồm dữ liệu nhân viên, timecard, đơn đặt hàng, và thông tin chi trả.

---

## 2. Lý do lựa chọn kiến trúc Layered

- **Tách biệt trách nhiệm:**  
  Giảm sự phụ thuộc giữa các thành phần, giúp dễ bảo trì và nâng cấp hệ thống.
- **Tính mở rộng:**  
  Có thể dễ dàng bổ sung thêm chức năng hoặc tích hợp với các hệ thống mới.
- **Tái sử dụng:**  
  Các lớp (như Data Access) có thể được tái sử dụng khi phát triển các module khác.
- **An toàn và kiểm soát:**  
  Hạn chế truy cập trái phép thông qua lớp Application và Integration.

---

## 3. Ý nghĩa từng thành phần

- **Presentation Layer:**  
  Hiển thị thông tin và nhận dữ liệu từ người dùng (nhân viên, Payroll Administrator).

- **Application Layer:**  
  Xử lý logic chính như tính lương, xử lý timecard, và điều phối giữa Presentation và Integration Layers.

- **Integration Layer:**  
  Đảm bảo sự tương thích với các hệ thống kế thừa (Project Management Database) và giao dịch ngân hàng.

- **Data Access Layer:**  
  Đóng vai trò làm trung gian giữa logic nghiệp vụ và Database Layer.

- **Database Layer:**  
  Lưu trữ dữ liệu, đảm bảo tính nhất quán và tính toàn vẹn.

---

## 4. Biểu đồ package mô tả kiến trúc

![Biểu đồ](https://www.planttext.com/api/plantuml/png/X9HDJiCm48NtEONL3QjkM5TLqnQXIaL450umEAFMr3_Hs46AK4_6WYDn1Toq9JPnYfHDvhtCV6C_vVlpQsOTaAkLp2hWUzWY6nNGa96IRHhhK8tOHyQOVpgTqA9su8JHR0qDqid369TWBRjJbJGDuiigAEQb4hgj7BAmsRosGgCthCrMy5IxCyu6wLrm38HdeP03bGKPxZiO2hI5KKfOwmaN87ajmKNo4rQ6t3rgfBCIKot10SivRy66DposiS8tQ19OIR6eYU_0uYELI94Z1ZYTFLjfXriQFEdb_3OleN8OxZO7lS-BLIVqLtlr1DVskdWIMoMaQAUKJkODkNi0xG6KJyulmcGYSGkycKulc3V-QcIxhzs9olfAboOs7a_xQJW7Aot6XTQJIat2DX2WXBEVfOGfcPWhTF_vXdFKdnG11FVJdnKX1Cw1QNsIy9i-T1JNxkNKPYWawLP_Gdx8PgZBur_i1m00__y30000)
