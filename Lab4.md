# Thiết kế use case Maintain Timecard

## 1. Các Lớp và Thuộc Tính/Phương Thức Của Chúng

### Các Lớp:

- **User (Người dùng hệ thống):**
  - **Thuộc tính**: `username`, `password`, `role` (quản trị viên/nhân viên)
  - **Phương thức**: `login()`, `updateProfile()`

- **Timecard (Thẻ chấm công):**
  - **Thuộc tính**: `employeeID`, `hoursWorked`, `rate`
  - **Phương thức**: `enterHours()`, `saveTimecard()`, `updateTimecard()`

- **Payroll (Lương):**
  - **Thuộc tính**: `employeeID`, `salaryAmount`, `paymentDate`
  - **Phương thức**: `calculateSalary()`, `generatePaycheck()`, `distributeSalary()`

- **Admin (Quản trị viên):**
  - **Thuộc tính**: `adminID`, `role`
  - **Phương thức**: `runPayroll()`, `approvePayroll()`

![Diagram](https://www.planttext.com/api/plantuml/png/V9B9JiCm443l_efHJu2K0zSSK8ig1BTAPJbFxQ6rwYNoKXG1NyQ1J-8NiDqqJLgfbyIU9UzDxB-VtwaFw4BKYd65tiEB9mUV3A22c9O6DTMm34wQTGasgUZ3EZ4AEgk6LG3AhgMvkgxXtgOKcXACZS102sVVfQASVBLIi6_MaP-b9evET7JIZR8jqTDyXDhOwFoRTLjA2W_AOjWRf2yVzm1a0hd7NDk3SjZZZWwSKMBlTfRgvHROfY7LPJUF2bqxqpQQC9HhiDL9Q5uSyxCWEIeULTejIrjc7ltNP2ZFbBXyGtmxaXNI9-Wg3bl7kZEXfUbaCQzFJCyEp4NJZJWYOTCukwFJLEAKUr9LNtTx5kjFRt8xWPkgAkzIL0Et9g0qdXt-uh2cRwnXXPu4MCEcP4I-aly0003__mC0)

---

## 2. Đơn Giản Hóa Sơ Đồ Chuỗi Tương Tác Sử Dụng Hệ Thống Con

![Diagram](https://www.planttext.com/api/plantuml/png/T94zJiGm48LxdsAKdWkaGAlWHLG84IumU4TQ2ySEu_5AlWubLw2Ws0Dn1U8WepKHxVFtVaR--lZSHK6MD3c5HW93TtyyltausVExxm0ZxAVPXKoaveMpnixe1RedEv51Fjm6dbRiKcZH1ymSd1jp5FfX6wM5DGe-OwILquDIjHwkhfkE7lPUYE4k98xgygMGUkXXn1FzMg04ApriOnv94diOap4KOzFNx2paQw8eLOORT2Ov51kyQj2wO8bcI_-is8IlCrfoa_h7L1VGSgn3pbj3FQS7RUFiC9S8SoJp0fe4hOjgH_vG_lyR003__mC0)

---

## 3. Định Nghĩa Hành Vi Persistence-Related

| **Analysis Class**     | **Analysis Mechanism(s)** |
|------------------------|---------------------------|
| Timecard               | Persistency, Security     |
| Employee               | Persistency, Security     |
| TimecardController     | Distribution              |

---

## 4. Phân Tích Lớp và Bản Đồ Cơ Chế Kiến Trúc Từ Phân Tích Use-Case

![Diagram](https://www.planttext.com/api/plantuml/png/V91D3e8m44RtFSM4lHTWOH3PcXX_ulgJJanZAQOj2s8ycGkFv1Ki110JS3apxvjvcVVpbJWFwwj2YnloAovCqT6nfGrCA0esFgAx8CerdADcD1GhMIWZ7kARtAAsfTOpuOCgE8ULGwF3VrPay3Z3yJYOfGtIQYsM4tvnu-L4wpD7j4FbVF3lFLfqIZccTMayb0cdWuxecJyyT5vfUAOzD6mzZcHf07OCwGX6qiagpztYX8riNly1003__mC0)

---

## 5. Cải Thiện Mô Tả Quy Trình Sự Kiện

![Diagram](https://www.planttext.com/api/plantuml/png/Z9D1JiCm44NtFiMeUovGAQYK5B52GBc0wmp48h6DCoxA2LYmuW1827P8Y7spOD6Jv0HSWSIjqwP5WkNCl9d_lwDyLr-ZWhWbbsUC2z8M1cVfybN1N2xVrG1u0PFSPBf4PARXf926AuB1bSnHS9iSQqLMPnbQ3s_Att4FXQAF19qWsf_6dFYC5wjfFEuFfoYSbLJwOIWOYoBO2WCghHSV1cvaNJr3jdp9ctvTFGY88XR4uU2mimT3c2X22wVQsO9rxGO96XuHjZG4hK7MzVjdBf6SLG75P0Ll7up73JRbSzoiUQRfzqyTYLkbxpDCRj3pFkM5gnTl2iZMrUCwhF71JLfNJnAIklg4h0thTiDkFfZtUUUme1qFMyXUB2jnp_DUhXCaaVuLRFr6_vIEPT5epnoX1u4qdFEoHNTskgp3DkgrjFbgeJiWjM8ZL4dx1_m0003__mC0)

---

## 6. Thống Nhất Các Lớp và Subsystem

![Diagram](https://www.planttext.com/api/plantuml/png/Z5H1JiCm4Bpd5QkS0AcLkFQ02WG4jqf5SDuwsyQgOqUsKob2l8m3J-8Bs25ndTBGvf0ekyxCxCmgtvzVSsDHsxeKIOLiYnk2T47QS6D9CahXFG5W0es15ruIGvst9O09K5a9rH0zPpDOMitbfciKgjRcJUajvJDu50fjrz1eAQu0aBIad_pvYyiPl2gUTms3E-eP3rfrbJkSaMRrApv3Yr7d8mbZF7IgJuyXiQI3abPYM08GQiEbfxfJhebo87AXrPeBEbEZKnb2M1AhDRVDFma0x51mJnCC76fm2UgcEjyB0AnjuIBXp86EulqTQYWzSxDflgejL_AO_7ibhJDIa0wy1SfSX4WF1Fihxp5fV9e5DXxsTB061UhcjbIrjCC5hR0ftVnPkwV-tj4p5AmMxdtPVkhvuotUa2I_squ1AuXjHyNlFu-T2xccrobSJIRjCsGp0-OCGovDSiJ1wVHclnTESw0QEnpXHeTxxs854UmA3UMWP3XtW7JV-zDv2skbnmJq436_Dxujkct699cJpFqlwGS00F__0m00)
