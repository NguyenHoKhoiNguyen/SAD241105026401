# Phân Tích Ca Sử Dụng: Generate Payroll

## 1. Xác Định Các Lớp Phân Tích

### Các lớp phân tích quan trọng trong ca sử dụng này bao gồm:
- **Employee**: Đại diện cho nhân viên được trả lương.
- **Timecard**: Lưu trữ thông tin số giờ làm việc (đối với nhân viên trả lương theo giờ hoặc lương cứng).
- **PurchaseOrder**: Lưu trữ thông tin doanh số bán hàng (đối với nhân viên có hoa hồng).
- **PayrollProcessor**: Thành phần chính để tính toán lương dựa trên thông tin từ Timecard và PurchaseOrder.
- **Paycheck**: Biểu diễn thông tin thanh toán (lương).
- **PaymentMethod**: Lưu trữ thông tin cách thức nhận lương (chuyển khoản, nhận tại văn phòng, hoặc gửi qua bưu điện).
- **BankSystem**: Thành phần tương tác với ngân hàng để thực hiện thanh toán.
- **SystemClock**: Kích hoạt quá trình tính toán lương tự động vào thời điểm định trước.

---

## 2. Nhiệm Vụ Của Từng Lớp Phân Tích

### **Employee**
- Nhiệm vụ: Lưu thông tin cơ bản và cấu hình phương thức thanh toán.

### **Timecard**
- Nhiệm vụ: Cung cấp dữ liệu về số giờ làm việc của nhân viên (nếu là nhân viên theo giờ hoặc lương cứng).

### **PurchaseOrder**
- Nhiệm vụ: Cung cấp dữ liệu doanh số bán hàng (nếu là nhân viên có hoa hồng).

### **PayrollProcessor**
- Nhiệm vụ: Thành phần trung tâm để tính toán lương cho tất cả các loại nhân viên.
  - Tổng hợp dữ liệu từ các lớp khác để tạo Paycheck.

### **Paycheck**
- Nhiệm vụ: Lưu thông tin về số tiền trả, ngày thanh toán, và chi tiết lương.

### **PaymentMethod**
- Nhiệm vụ: Xác định cách nhân viên nhận lương (chuyển khoản, nhận tại văn phòng, hoặc qua bưu điện).

### **BankSystem**
- Nhiệm vụ: Xử lý các giao dịch chuyển khoản ngân hàng.

### **SystemClock**
- Nhiệm vụ: Kích hoạt quá trình tính lương vào thời điểm đã định.

---

## 3. Xác Định Thuộc Tính và Quan Hệ Giữa Các Lớp

### **Employee**
- Thuộc tính: `id`, `name`, `type`, `salary`, `commissionRate`, `paymentMethod`.
- Quan hệ:
  - 1 Employee -> N Timecards.
  - 1 Employee -> N PurchaseOrders.

### **Timecard**
- Thuộc tính: `id`, `date`, `hoursWorked`, `chargeNumber`.
- Quan hệ: Thuộc về 1 Employee.

### **PurchaseOrder**
- Thuộc tính: `id`, `date`, `amount`.
- Quan hệ: Thuộc về 1 Employee.

### **PayrollProcessor**
- Thuộc tính: Stateless (không lưu trạng thái dài hạn).
- Quan hệ: Kết nối với tất cả các lớp liên quan.

### **Paycheck**
- Thuộc tính: `id`, `amount`, `paymentDate`, `employeeId`.
- Quan hệ: Thuộc về 1 Employee.

### **PaymentMethod**
- Thuộc tính: `type`, `details`.
- Quan hệ: 1 Employee -> 1 PaymentMethod.

### **BankSystem**
- Quan hệ: Nhận yêu cầu chuyển khoản từ PayrollProcessor.

### **SystemClock**
- Thuộc tính: `currentDate`.
- Quan hệ: Kích hoạt PayrollProcessor.

---
## 4. Biểu đồ
![Biểu đồ](https://www.planttext.com/api/plantuml/png/X5CzJyCm4DtpAwnCxT21DGEge5HYe5GKYVc8ZyIgFwApFKI8NyR0J-8la2Pk4giMNPBOT-_TktkNt--VjNL0pYkPbHAiPG-gaQP5P9yPOoicUC64Tlst1eK5EpWIkkelNDl45nOaK5kmhJGmO4gZbB1M6Fq23kUH1bg5sZsXgqrNP3y_PbzPaFCg59P0F267zuIRxjaVQ-F9lXaw8ey4r40LxhnwHngrZlHxJrs2nMVYIDThW39UkpFzn08j6IdtP4gqrWn4Z5MeaJfe22ycicM4BMiiZudYSRNPp3QnAWoMFGRid7kQQIXmuHb71qBQozdSWJuUMkjGXNuSWROVI5klkLqqGNWnjZ3hQi3TInCQEu55LI6TPx4SpF54SJyTmxY1-KtELgjRbk_oSG_IqSZ6H4htZlShpHBwo2xyF6MS8Udeg2yPZVMbK_uj7gjFfansPVFf1tIKdwrHyzCl_mS00F__0m00)
---

## 5. Giải Thích Biểu Đồ Lớp

- **Employee** là trung tâm liên kết với các lớp khác như **Timecard**, **PurchaseOrder**, và **PaymentMethod**.
- **PayrollProcessor** thực hiện mọi logic tính toán lương và quyết định phương thức thanh toán.
- **Timecard** và **PurchaseOrder** cung cấp dữ liệu liên quan đến giờ làm việc và doanh số bán hàng.
- **Paycheck** là kết quả cuối cùng của quá trình tính toán.
- **PaymentMethod** và **BankSystem** đảm bảo lương được gửi đến đúng nơi.

---

# Phân Tích Ca Sử Dụng: Generate Employee Reports

## 1. Xác Định Các Lớp Phân Tích

### Các lớp phân tích chính:
- **Employee**: Đại diện cho nhân viên cần truy vấn dữ liệu báo cáo.
- **Report**: Biểu diễn dữ liệu báo cáo của nhân viên (giờ làm việc, tổng lương, số giờ dành cho dự án, v.v.).
- **Timecard**: Lưu trữ thông tin số giờ làm việc của nhân viên.
- **PurchaseOrder**: Lưu trữ thông tin doanh số bán hàng (nếu có).
- **Vacation**: Lưu thông tin về số ngày nghỉ còn lại của nhân viên.
- **ReportGenerator**: Thành phần chính xử lý việc thu thập dữ liệu và tạo báo cáo.
- **Database**: Thành phần chứa thông tin cần thiết để tạo báo cáo (Timecard, PurchaseOrder, Vacation).

---

## 2. Nhiệm Vụ Của Từng Lớp

### **Employee**
- Nhiệm vụ: Người yêu cầu và nhận báo cáo cá nhân.

### **Report**
- Nhiệm vụ: Biểu diễn dữ liệu báo cáo theo yêu cầu (giờ làm việc, lương, dự án, nghỉ phép).

### **Timecard**
- Nhiệm vụ: Cung cấp dữ liệu về số giờ làm việc.

### **PurchaseOrder**
- Nhiệm vụ: Cung cấp thông tin về doanh số bán hàng (nếu có).

### **Vacation**
- Nhiệm vụ: Lưu trữ và cung cấp dữ liệu về số ngày nghỉ còn lại.

### **ReportGenerator**
- Nhiệm vụ: Thành phần trung tâm để thu thập dữ liệu từ các lớp khác và tạo báo cáo.

### **Database**
- Nhiệm vụ: Thành phần lưu trữ dữ liệu cần thiết (Timecard, PurchaseOrder, Vacation).

---

## 3. Xác Định Thuộc Tính và Quan Hệ Giữa Các Lớp

### **Employee**
- Thuộc tính: `id`, `name`, `department`, `position`.
- Quan hệ:
  - 1 Employee -> N Timecards.
  - 1 Employee -> N PurchaseOrders.
  - 1 Employee -> 1 Vacation.

### **Report**
- Thuộc tính: `type`, `data`, `generationDate`, `employeeId`.

### **Timecard**
- Thuộc tính: `id`, `date`, `hoursWorked`, `chargeNumber`.

### **PurchaseOrder**
- Thuộc tính: `id`, `date`, `amount`.

### **Vacation**
- Thuộc tính: `remainingDays`.

### **ReportGenerator**
- Thuộc tính: Stateless.
- Quan hệ: Kết nối với tất cả các lớp liên quan để thu thập dữ liệu báo cáo.

### **Database**
- Thuộc tính: Lưu trữ tập trung cho các đối tượng liên quan.
---
## 4. Biểu đồ
![Biểu đồ](https://www.planttext.com/api/plantuml/png/X5F1JeGm5Bpp5GsdDP63Lmvc3wl6owxHZPuVy5ogjCNNSY36B_FW9_aBjXIgi8rxeMJUT6RU1Bu_lzRQ09bED4dPWDRiIhIDwX7PUy9OndYLCoxDy2v1OCuU375v680AMtjNe3Gpk5MQ6wva03-IKVmUMqLcb3Pzkv030pFWW189dDG6ZEMwvp30CUJjc2uOxBd04gYAfA_c4hNgI3yfUaNBkMuKU5PP0nrmsua2wJZ_NKUMe7575T9f3n2gSzru-Q3o2EMmr2X0A81BwxE1NX-HVMKtlWdbJTdK3FhfQj77kTLq-FvFmsU_aZOV57QBKUiPJLaxRFNM8VNXGivsnGkMGvRmLQGNASkoIvPkqr1sV3hhAaAnvrH4ibpI4QORqM6mZWtdpZ76lyOUYuwcvf8roihzCpy0003__mC0)
---
## 5. Giải Thích Biểu Đồ Lớp
- **Employee** liên kết trực tiếp với dữ liệu liên quan như **Timecard**, **PurchaseOrder**, và **Vacation**.
- **ReportGenerator** là thành phần trung tâm, tương tác với **Database** và các lớp liên quan để tạo báo cáo theo yêu cầu.
- **Report** lưu trữ kết quả báo cáo được tạo.
- **Database** đóng vai trò là kho dữ liệu, nơi **ReportGenerator** truy vấn thông tin.
- Các lớp như **Timecard**, **PurchaseOrder**, và **Vacation** cung cấp dữ liệu cần thiết cho báo cáo.

