# 1. Subsystem context diagrams

## PrintService

![PrintService Diagram](https://www.planttext.com/api/plantuml/png/X5BBRi903BplLrXSEF434KA0uD03KjKSUZQ9WIt9RhGsjFcs7lf9_OKwcmJ2G-efyUpCUBpUt--VEGi6EPM56SEATjOHO2O-i8aV6AtBgl0rqGYGeI_wmrUiWoyAMEIbTPObeCAH6H5pDUNJbciMAW5T3buE523pPUKTEM4JA1Dq-uBKCrWdAOMppTgcGm2cqxHtcisCoL5mYqpNAAiEQQKjk5gghZb8DHwfRY0B_aDxmmOTxgdKC7SEcmUnsVgJop7KC7gtBlUVh4FoKNm5BquexB0Btg4NK7qk_-epc7c9xWXfd2egcxejLRF-Ket3eYCq2SRmHWMAzOuFjcBJxmKcazbZswJDfJipSIt_iXxE6i7D6X9OP1ancniqqYvNdcX82PRE1CFbF95ixjZTJfwp1tUJG4hwcjIzvPgvbirR_WC00F__0m00)

### Giải thích:
**PrintService**:
- Đây là hệ thống con chính, đóng vai trò quản lý các tác vụ liên quan đến in bảng lương.
- Được đánh dấu là `<<Subsystem>>`.

**Các thành phần tương tác**:
- **Employee và Payroll Administrator**: Là hai loại người dùng tương tác với hệ thống qua giao diện người dùng.
- **Windows Desktop Interface**: Giao diện chính để người dùng truy cập PrintService.

**Các kho dữ liệu**:
- **Payroll Database**: Chứa dữ liệu về bảng lương và thông tin nhân viên.
- **Project Management Database**: Chứa thông tin về các dự án và mã công việc (charge numbers).

**Hệ thống bên ngoài**:
- **Bank System**: Xử lý việc gửi dữ liệu bảng lương qua ngân hàng.

**Mối quan hệ**:
- Nhân viên và quản trị viên truy cập vào PrintService thông qua Windows Desktop Interface.
- PrintService lấy dữ liệu cần thiết từ hai cơ sở dữ liệu và gửi thông tin giao dịch đến hệ thống ngân hàng.

## ProjectManagementDatabase subsystems

![ProjectManagementDatabase Diagram](https://www.planttext.com/api/plantuml/png/T5FBRi8m4BpdAomkFV43224ezD035O9MFI_EDhZu4NcNLdnR3_sa_a8tSPg6G6xnxCpiUjRv-VgU4qFaaxFPdLfe3f6oY9h15nRLwC6LDfmHHmf8_HtKT5epPxCkTGFd6AnLYzmPRuWZ2ANMrSY0A8PtEQarU2WmqHkiWJewcN1tsjEP69q2dwl01o7euChWqJCDEpifgnKmx87IPJRhrRrujuQNSxqQduTFKYka8uTIFNh6-0OwQHkq1SMd_RuTogxkaHedA26YN0RF0jpEvJc2FXfVN1YaMblgMaX4MxJ09dWwc9AoTcVZyUnwxaaLg3FInpZK47FAqh86s2bCjI0oXNTrvBrjLSB-W9D6e9O7Y29_EhazoZlBhZhKwcen8j4QgRrilRliCheEUOiS3NvWlqD_aexafSo1yTyV6OoLcURey-fl-0K00F__0m00)

### Giải thích:
**Các thành phần chính**:
- **Project Management Database (PMDB)**: Hệ thống con trung tâm lưu trữ thông tin dự án, bao gồm mã charge numbers và các thông tin khác. Được biểu diễn là hình chữ nhật và đánh dấu `<<Subsystem>>`.

**Các tác nhân (Actors)**:
- **Employee**: Gửi thông tin timecard liên kết với charge numbers qua giao diện.
- **Payroll Administrator**: Quản lý việc phân công nhân viên vào dự án.
- **Project Manager**: Thực hiện các thay đổi liên quan đến charge numbers hoặc cập nhật chi tiết dự án.

**Các hệ thống tương tác**:
- **Windows Desktop Interface**: Giao diện để nhân viên và quản trị viên tương tác với PMDB. Đánh dấu là `<<Interface>>`.
- **Payroll System**: Tương tác với PMDB để lấy dữ liệu charge numbers khi xử lý bảng lương. Đánh dấu là `<<Control>>`.
- **Project Tracking System**: Quản lý và cập nhật thông tin liên quan đến dự án trong PMDB. Đánh dấu là `<<Control>>`.

# 2. Analysis class to design element map

| Analysis Class               | Design Element            |
|------------------------------|---------------------------|
| Employee                     | EmployeeEntity            |
| Timecard                     | TimecardEntity            |
| Paycheck                     | PaycheckEntity            |
| Purchase Order               | PurchaseOrderEntity       |
| Payroll Administrator        | PayrollAdminController    |
| Payment Method               | PaymentMethodInterface    |
| Project Management Database  | ProjectManagementDBAdapter|
| Payroll System               | PayrollController         |
| Bank System                  | BankIntegrationService    |
| Windows Desktop Interface    | EmployeeDesktopUI         |
| System Clock                 | SystemClockService        |

# 3. Design element to owning package map

| STT | Design Element             | Owning Package             |
|-----|-----------------------------|----------------------------|
| 1   | EmployeeEntity              | Data Access Layer          |
| 2   | TimecardEntity              | Data Access Layer          |
| 3   | PaycheckEntity              | Data Access Layer          |
| 4   | PurchaseOrderEntity         | Data Access Layer          |
| 5   | PayrollAdminController      | Business Logic Layer       |
| 6   | PayrollController           | Business Logic Layer       |
| 7   | PaymentMethodInterface      | Business Logic Layer       |
| 8   | ProjectManagementDBAdapter  | Data Access Layer          |
| 9   | BankIntegrationService      | External Integration Layer |
| 10  | EmployeeDesktopUI           | User Interface Layer       |
| 11  | SystemClockService          | Utility Layer              |
| 12  | PaymentMethodImplementation | Business Logic Layer       |

# 4. Architectural layers and their dependencies

![Architectural Layers](https://www.planttext.com/api/plantuml/png/T98z3W8X44PxJZ6niV8Anj_2nCvO6Oi9ZYiHSGNMQ8orjRML9_0051QUP4_W5NJLOa6MShxt2FE5fxktZ4LjivLaB4M-n8IWravJAJXQiLOmn3tf6XmOlC-ab4pPiQHqCYCK6GCZqbl1oGJYN-xhFRG8RSuBmXTBYQ_qTvQqGWa3PIdHiTV64F-IiI7zIVKSEGMw7mQY5LBOVMZyfjwITUW-hXnMkJiBs6IeO96x4oGYTpS4NcGoTvUKUUr2ez6CrXQPVLclgKegtaab7dPG3VwjpbgaPiN7UW400F__0m00)

### Giải thích:
**Application Layer**:
- Là lớp cao nhất, chịu trách nhiệm xử lý các yêu cầu từ người dùng và giao tiếp với các lớp khác để thực hiện các chức năng của hệ thống.
- Ví dụ: Giao diện chính mà người dùng tương tác.

**Business Services Layer**:
- Lớp này chứa các logic nghiệp vụ chính của hệ thống. Nó xử lý các quy trình và logic cụ thể để thực hiện các chức năng chính của hệ thống.
- Ví dụ: Các controller hoặc service để xử lý logic tạo bảng lương.

**Data Access Layer**:
- Lớp này chịu trách nhiệm truy cập và quản lý dữ liệu từ các cơ sở dữ liệu hoặc hệ thống lưu trữ dữ liệu khác.
- Ví dụ: Các lớp dùng để kết nối và lấy dữ liệu từ cơ sở dữ liệu.

**External Integration Layer**:
- Lớp này xử lý các kết nối và giao tiếp với các hệ thống bên ngoài như ngân hàng, các hệ thống bên thứ ba.
- Ví dụ: Các API hoặc dịch vụ dùng để gửi dữ liệu bảng lương đến hệ thống ngân hàng.
