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

# 2. **Cơ chế phân tích**

Dưới đây là các cơ chế cần giải quyết trong hệ thống Payroll và lý do tại sao chúng quan trọng:

## 2.1. **Cơ chế xử lý và tính toán lương**

*   **Mô tả:**  
    Hệ thống phải có cơ chế tính toán chính xác lương cho các nhân viên theo các loại hình (hourly, salaried, commissioned). Lương của nhân viên sẽ được tính theo thời gian làm việc (với hệ số tính lương ngoài giờ cho nhân viên hourly) hoặc theo doanh thu bán hàng (với nhân viên commissioned).
*   **Lý do:**  
    Đây là cơ chế cốt lõi của hệ thống, giúp đảm bảo nhân viên nhận lương chính xác và đúng hạn.

## 2.2. **Cơ chế quản lý và kiểm soát thông tin thời gian làm việc (Timecard)**

*   **Mô tả:**  
    Cần có cơ chế để nhân viên có thể ghi nhận và chỉnh sửa thời gian làm việc của mình trong hệ thống. Hệ thống phải đảm bảo rằng mỗi nhân viên chỉ có thể chỉnh sửa thời gian của chính mình, trong khi nhân viên quản trị chỉ có thể thay đổi thông tin của tất cả người dùng.
*   **Lý do:**  
    Đảm bảo tính chính xác của dữ liệu và bảo mật thông tin cá nhân. Mỗi nhân viên chỉ có thể thay đổi dữ liệu của mình, tránh trường hợp sửa đổi sai lệch thông tin.

## 2.3. **Cơ chế xác nhận và xử lý giao dịch ngân hàng (Direct Deposit)**

*   **Mô tả:**  
    Hệ thống phải có cơ chế giao tiếp với hệ thống ngân hàng để xử lý việc chuyển khoản lương qua direct deposit cho nhân viên. Hệ thống cần cung cấp phương thức nhập tài khoản ngân hàng và đảm bảo bảo mật trong quá trình giao dịch.
*   **Lý do:**  
    Cung cấp phương thức thanh toán nhanh chóng và an toàn cho nhân viên, giảm chi phí và thời gian cho các phương thức thanh toán truyền thống.

## 2.4. **Cơ chế bảo mật và phân quyền**

*   **Mô tả:**  
    Hệ thống cần có cơ chế bảo mật chặt chẽ để bảo vệ dữ liệu cá nhân và thông tin lương của nhân viên. Phân quyền người dùng cần rõ ràng: nhân viên chỉ có quyền truy cập và chỉnh sửa dữ liệu của chính mình, còn Payroll Administrator có thể chỉnh sửa tất cả thông tin liên quan đến nhân viên.
*   **Lý do:**  
    Đảm bảo tính bảo mật và quyền riêng tư cho nhân viên, đồng thời cho phép quản lý hệ thống an toàn và hiệu quả.

## 2.5. **Cơ chế tích hợp với hệ thống quản lý dự án (Project Management Database)**

*   **Mô tả:**  
    Hệ thống Payroll cần kết nối và truy xuất dữ liệu từ hệ thống quản lý dự án (Project Management Database) để lấy thông tin liên quan đến mã số công việc và thời gian làm việc của nhân viên. Tuy nhiên, hệ thống Payroll chỉ có quyền đọc dữ liệu từ hệ thống này mà không có quyền chỉnh sửa.
*   **Lý do:**  
    Cần duy trì tính nhất quán và đồng bộ thông tin giữa các hệ thống, giúp quản lý chi tiết về công việc và các chi phí liên quan.

## 2.6. **Cơ chế báo cáo và tra cứu thông tin cho nhân viên**

*   **Mô tả:**  
    Hệ thống cần cung cấp cơ chế cho nhân viên truy vấn thông tin về số giờ làm việc, tổng số tiền lương đã nhận, số ngày nghỉ còn lại, và các báo cáo liên quan đến công việc của họ.
*   **Lý do:**  
    Đảm bảo tính minh bạch trong quá trình tính toán lương và giúp nhân viên theo dõi công việc cũng như các quyền lợi của mình.

## 2.7. **Cơ chế quản lý phương thức thanh toán**

*   **Mô tả:**  
    Cần có cơ chế cho phép nhân viên thay đổi phương thức thanh toán của mình (chuyển khoản qua ngân hàng, nhận tại văn phòng hoặc nhận qua bưu điện). Hệ thống phải lưu lại các thông tin thay đổi này để thực hiện thanh toán đúng cách.
*   **Lý do:**  
    Đảm bảo sự linh hoạt và tiện ích cho nhân viên khi lựa chọn phương thức thanh toán, đồng thời giảm thiểu sai sót trong quá trình thanh toán.

## 2.8. **Cơ chế tự động hóa quy trình thanh toán**

*   **Mô tả:**  
    Cần có cơ chế tự động hóa quy trình thanh toán vào các ngày đã định (mỗi thứ Sáu và vào ngày cuối tháng), hệ thống sẽ tự động tính toán và xử lý thanh toán cho các nhân viên mà không cần sự can thiệp thủ công.
*   **Lý do:**  
    Giảm thiểu sai sót và tiết kiệm thời gian cho nhân viên và các quản trị viên trong việc xử lý thủ công.

---

### Tóm tắt các cơ chế cần giải quyết:

1.  Cơ chế xử lý và tính toán lương.
2.  Cơ chế quản lý và kiểm soát thông tin timecard.
3.  Cơ chế xác nhận và xử lý giao dịch ngân hàng (Direct Deposit).
4.  Cơ chế bảo mật và phân quyền.
5.  Cơ chế tích hợp với hệ thống quản lý dự án (Project Management Database).
6.  Cơ chế báo cáo và tra cứu thông tin cho nhân viên.
7.  Cơ chế quản lý phương thức thanh toán.
8.  Cơ chế tự động hóa quy trình thanh toán.

# Phân tích ca sử dụng Maintain Timecard

## 1. Các lớp phân tích cho ca sử dụng Maintain Timecard

Trong ca sử dụng **Maintain Timecard**, hệ thống cần cho phép nhân viên nhập thông tin về thời gian làm việc của họ trong một kỳ lương cụ thể, đồng thời cập nhật và lưu trữ các thay đổi này.

### 1.1. Lớp `Employee`

- **Nhiệm vụ:**  
  Lớp này đại diện cho nhân viên và là lớp tương tác chính trong việc nhập thời gian làm việc (timecard). Nhân viên có thể điều chỉnh thời gian làm việc của mình cho một ngày, tuần hoặc kỳ lương.
  
- **Thuộc tính:**  
  - `employeeID`: Mã nhân viên (ID duy nhất).
  - `name`: Tên nhân viên.
  - `timecards`: Danh sách các timecard của nhân viên trong các kỳ lương.

- **Quan hệ:**  
  - **1-N**: Mỗi nhân viên có thể có nhiều timecard cho mỗi kỳ lương.

### 1.2. Lớp `Timecard`

- **Nhiệm vụ:**  
  Lớp này đại diện cho một bản ghi thời gian của nhân viên trong một kỳ lương cụ thể. Timecard chứa thông tin về giờ làm việc của nhân viên trong một ngày.
  
- **Thuộc tính:**  
  - `date`: Ngày làm việc.
  - `hoursWorked`: Số giờ làm việc trong ngày.
  - `employeeID`: Mã nhân viên liên quan đến timecard.
  - `status`: Trạng thái của timecard (đã phê duyệt, chưa phê duyệt, cần sửa đổi).

- **Quan hệ:**  
  - **1-1**: Mỗi timecard chỉ liên kết với một nhân viên.

### 1.3. Lớp `PayrollSystem`

- **Nhiệm vụ:**  
  Lớp này chịu trách nhiệm chính trong việc quản lý và xử lý các timecard, bao gồm việc duy trì và phê duyệt thời gian làm việc của nhân viên. Lớp này sẽ xác minh thời gian làm việc và cập nhật thông tin cho các nhân viên.
  
- **Thuộc tính:**  
  - `payrollDate`: Ngày thanh toán của kỳ lương.
  - `payrollRecords`: Danh sách các timecard đã được xác nhận và phê duyệt.

- **Quan hệ:**  
  - **1-N**: Một PayrollSystem có thể chứa nhiều timecard được xác nhận từ nhiều nhân viên.

### 1.4. Lớp `TimecardManager`

- **Nhiệm vụ:**  
  Lớp này có trách nhiệm xác nhận và phê duyệt các timecard của nhân viên, bao gồm việc kiểm tra số giờ làm việc và trạng thái của các timecard, từ đó đưa ra quyết định phê duyệt hay yêu cầu sửa chữa.
  
- **Thuộc tính:**  
  - `managerID`: Mã quản lý.
  - `assignedEmployees`: Danh sách nhân viên mà quản lý có trách nhiệm phê duyệt timecard.

- **Quan hệ:**  
  - **1-N**: Một TimecardManager có thể quản lý và phê duyệt nhiều timecard của các nhân viên.

## 2. Mô tả hành vi của các lớp trong ca sử dụng Maintain Timecard

### Bước 1: Nhân viên nhập thông tin thời gian làm việc

- **Employee** sẽ nhập thời gian làm việc của mình vào hệ thống qua giao diện người dùng, tạo ra một **Timecard** mới.
- **Timecard** sẽ lưu lại thông tin về ngày làm việc và số giờ làm việc.

### Bước 2: Lưu trữ và kiểm tra tính hợp lệ

- **PayrollSystem** sẽ nhận các timecard từ nhân viên và kiểm tra tính hợp lệ (số giờ làm việc có hợp lý không).
- **PayrollSystem** sẽ lưu trữ các timecard của nhân viên vào cơ sở dữ liệu của hệ thống.

### Bước 3: Quản lý và phê duyệt timecard

- **TimecardManager** sẽ phê duyệt hoặc yêu cầu chỉnh sửa các timecard. Quản lý sẽ kiểm tra các thời gian làm việc đã nhập, xác minh với các chính sách của công ty và quyết định phê duyệt.
- Nếu timecard hợp lệ, **TimecardManager** sẽ phê duyệt và ghi nhận vào hệ thống.

### Bước 4: Cập nhật thông tin cho kỳ lương

- Sau khi timecard được phê duyệt, **PayrollSystem** sẽ lưu thông tin timecard đã phê duyệt vào các bản ghi thanh toán để tính toán lương cho nhân viên trong kỳ lương đó.

## 3. Quan hệ giữa các lớp

- **Employee** và **Timecard** có mối quan hệ **1-N**, vì mỗi nhân viên có thể có nhiều timecard.
- **PayrollSystem** có mối quan hệ **1-N** với **Timecard**, vì hệ thống này quản lý nhiều timecard của nhiều nhân viên.
- **TimecardManager** có mối quan hệ **1-N** với **Employee** và **Timecard**, vì mỗi quản lý có thể phê duyệt nhiều timecard của nhân viên.
