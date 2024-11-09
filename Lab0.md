# Quản Lý Khách Sạn

## Giới Thiệu
Hệ thống quản lý khách sạn giúp tối ưu hóa việc quản lý phòng, khách hàng, dịch vụ, và hóa đơn. Nó giúp khách sạn vận hành hiệu quả hơn, nâng cao trải nghiệm khách hàng và quản lý các hoạt động hằng ngày một cách chính xác.

## Sơ đồ
### Sơ đồ lớp
![Sơ đồ lớp](https://www.planttext.com/api/plantuml/png/X5DBJiCm4Dtx5AEiKgGkkaMeQe45I8W55GTmdMbhrP_ATYfLY9Enu4XS0JiPvrCeP64xxtbcdj_ONn-V2n-u2xLMJ2ZkFJpOW0hU6CHl2glWfDc2uHh72AygXzuJ-2Hzk7cnLi_1nN44hz0TfS0v-7RHaf0of8Wo3KtKf2SefgGvXqxOEoEPJLHMAKreCZpNUerkB3IS3bbwPUkrGZYuc8gWjRKAkG7fbqSk5OyygH0x57i2fPBXL4wkytRQ4l_spH6oyer39A0JUbVxO3Mw_oqzxAp1tuumz1f0yptUnigHAMbkbCHvK3OpkUez3z76rEgq6e9egW7KoHMq8BphKhR7cerqEWl93WXk1AeUxVJaJbvsuKTt06gF-IOCKZsQenscEZFXpxltwh4QrmisSBNKjZQ1gcxHe8kEK9ssTFiiYba1LzCf59gRKz6OmZh7paYInHhd4cSJD-k9Iu5KbsNBBj1i4JkNtkqt0000__y30000)
### Sơ đồ ca sử dụng
![Sơ đồ ca sử dụng](https://www.planttext.com/api/plantuml/png/T99DJiGm38NtEONL_TnXe0jWmMP6h949faJa1oLkfH7YP2mu4bUWQU9HKyrqrRptFITsylVpg_Q9CVBeh4BD8KBNZuc3ezW19j1r8UQ1D7so2TuaNe2u4WHwH8z3BU3Alr8poEW7It0Vc6nX77a-dXAJWoy5ypScqfW8kjiGFk0GWbkgFFNFMSZh5klHQxAGJUC7OOjQnKtWdNGf33SJ6eilnXe-dPFPNXjjkfmQP4JmuD-2H8idLdRQx1rvYiWqXwPWD4bEz2fVtF18SPgzrEubgbeoSbMmsrtlP0CrGzqMQ8Qu4ElBhjILhY-GspuNhZwFfjYvhM-bzkHVyzly1m00__y30000)
### Sơ đồ gói
![Sơ đồ gói](https://www.planttext.com/api/plantuml/png/V94n3i8m34NtdCBA0JW0OgXWWO65dY0K0r6J62K6X10dO-18N06ta0eAmbFYlF_zhTolDrKaDf7ttgcTgMgpGT1JOdGmDq5k7WD3UKgCNiDPWLJ7BOZy6vRVcwgSIGaQeDSQ4zKsRDhkHNtwJVQ9oMFywvcXdmubneEjyA_1Y_cf7rld9DstQ1OEr1Ersuy6WxmI3457JE9ks5BGBTIjr0ENSanF96TkYDUObf0ek88rnIUMnJrCmb5b3GjwjBpLIj8L65RDXpu0003__mC0)

## Các Chức Năng Chính

### 1. Quản Lý Phòng
   - **Thêm mới phòng**: Cho phép thêm phòng mới vào hệ thống với các thông tin như số phòng, loại phòng, giá, và trạng thái phòng (trống hoặc đã đặt).
   - **Cập nhật trạng thái phòng**: Cho phép thay đổi trạng thái phòng khi có khách đặt hoặc trả phòng.
   - **Tìm kiếm phòng**: Tìm phòng dựa trên các tiêu chí như loại phòng, giá, hoặc trạng thái.

### 2. Quản Lý Khách Hàng
   - **Lưu trữ thông tin khách hàng**: Bao gồm họ tên, số điện thoại, địa chỉ và các yêu cầu đặc biệt.
   - **Tra cứu khách hàng**: Tìm kiếm khách hàng theo mã khách hàng hoặc thông tin liên hệ.
   - **Lịch sử đặt phòng**: Xem lại các giao dịch đặt phòng của khách hàng trong quá khứ.

### 3. Quản Lý Đặt Phòng
   - **Đặt phòng**: Tạo đặt phòng mới với các thông tin chi tiết về khách hàng, phòng đặt, ngày nhận và ngày trả phòng.
   - **Hủy đặt phòng**: Hủy đặt phòng nếu khách hàng có yêu cầu, bao gồm chính sách hoàn tiền nếu cần.
   - **Xác nhận đặt phòng**: Xác nhận đặt phòng cho khách hàng và cập nhật trạng thái phòng.

### 4. Quản Lý Dịch Vụ
   - **Thêm dịch vụ mới**: Nhập các dịch vụ mới của khách sạn như spa, giặt là, đưa đón sân bay.
   - **Cập nhật dịch vụ**: Cập nhật giá và thông tin dịch vụ.
   - **Quản lý sử dụng dịch vụ của khách hàng**: Ghi nhận các dịch vụ khách hàng đã sử dụng và tính phí tương ứng.

### 5. Quản Lý Hóa Đơn
   - **Tạo hóa đơn**: Tạo hóa đơn thanh toán cho khách hàng bao gồm chi phí phòng và các dịch vụ.
   - **In hóa đơn**: In hóa đơn chi tiết cho khách hàng khi thanh toán.
   - **Quản lý thanh toán**: Cập nhật trạng thái thanh toán và lưu trữ thông tin thanh toán.

## Mô Hình Lớp
Các lớp chính trong hệ thống quản lý khách sạn bao gồm:

- **Hotel**: Quản lý tổng thể thông tin khách sạn, bao gồm danh sách phòng, dịch vụ.
- **Room**: Lớp đại diện cho phòng khách sạn, bao gồm thông tin số phòng, loại phòng và giá.
- **Customer**: Lớp lưu trữ thông tin khách hàng.
- **Booking**: Lớp quản lý thông tin đặt phòng, bao gồm khách hàng, phòng và thời gian đặt.
- **Service**: Lớp quản lý dịch vụ của khách sạn.
- **Invoice**: Quản lý thông tin hóa đơn thanh toán cho khách hàng.

## Kết Luận
Hệ thống quản lý khách sạn giúp tối ưu hóa và tự động hóa các quy trình quản lý, từ đặt phòng đến thanh toán, giúp tăng cường hiệu quả hoạt động của khách sạn và cải thiện dịch vụ khách hàng.


