# **Thiết kế Hệ thống con: ManageTimecard**

## **Phân phối hành vi của hệ thống con đến các thành phần hệ thống**

Phân tích chức năng chính `manageTimecard()` và phân chia hành vi giữa các thành phần trong hệ thống con như sau:

- **ITimecardService**: Giao diện của hệ thống con, quy định hợp đồng chung để quản lý thẻ chấm công.
- **TimecardServiceImpl**: Cài đặt **ITimecardService** và cung cấp các chức năng cụ thể để quản lý thẻ chấm công.
- **TimecardRepository**: Quản lý việc lưu trữ và truy xuất dữ liệu thẻ chấm công từ cơ sở dữ liệu.
- **ITimecardValidator**: Giao diện định nghĩa hợp đồng kiểm tra tính hợp lệ của thẻ chấm công.
- **TimecardValidator**: Triển khai **ITimecardValidator**, kiểm tra dữ liệu thẻ chấm công trước khi lưu hoặc cập nhật.

---

## **Tài liệu các thành phần của hệ thống con**

#### **1. ITimecardService**

- **Phương thức**:
    - `void addTimecard(Timecard timecard);`
    - `void updateTimecard(Timecard timecard);`
    - `List<Timecard> getTimecardsByEmployee(String employeeID);`

#### **2. TimecardServiceImpl**

- **Thuộc tính**:
    - `TimecardRepository timecardRepository;`
    - `ITimecardValidator timecardValidator;`
- **Phương thức**:
    - `void addTimecard(Timecard timecard);`
    - `void updateTimecard(Timecard timecard);`
    - `List<Timecard> getTimecardsByEmployee(String employeeID);`

#### **3. TimecardRepository**

- **Phương thức**:
    - `void save(Timecard timecard);`
    - `void update(Timecard timecard);`
    - `List<Timecard> findByEmployee(String employeeID);`

#### **4. ITimecardValidator**

- **Phương thức**:
    - `boolean validate(Timecard timecard);`

#### **5. TimecardValidator**

- **Phương thức**:
    - `boolean validate(Timecard timecard);`

---

## **Sơ đồ lớp (Class Diagram)**

![Sơ đồ](https://www.planttext.com/api/plantuml/png/p5H1RiCW4BppYZqcKfmNH55KjGTBFJLLSYPcaw9Yi01Rijg-h8S-gLyegGrs3LKRgOToWjrX6MO7tb_VDiPIRUjI42ujwYCj4F9xNc91DTkYRhWBF14uZqPn1fGndvxv2TX-CXy1wufHYpzYRxcnAvzSmmcjNvYhzgQiX6eHPrkhkJm1zklyUavU22a4DGOcR7E7wHbdFdM7bJBSAjs6uuTG1msNtb717NEb0pH4_gaCYSuDb-XxTr1A89NGT0bC4OaK_Pig8_77HZAqIUwVIlTRoOvSiWiTusqIORkmqnKULAtDNkb7P5sGgVeW4BHZrj48hOsgB61IOG6ZtPzyegUsUbukKuucYTP-mGucJRs7B5id-l4jD3wCR52oypVn0G00__y30000)

---

## **Sơ đồ Tương tác Hệ thống con (Subsystem Interaction Diagram)**

![Sơ đồ](https://www.planttext.com/api/plantuml/png/r5HBQiCm4Dth55gcYrmWYvAKTc78egIVlV1Cme0-PYGRVBOkUgHUeN9YjQ6LS4mMfRlny3xoUqWVR-zh7nI7rcYXwk1OFfX6knvn_7nKFJkjDs38aW-iubA819BBMrazay5QCJmXTrIZN4a5a9QBC0utuXSmad-iggXRvEUmPnAlIXCCnui2tMd63FiRjYpwZtHoTeU-rM7AUeUDynGr-qZsgilvdc7AnhMpUs9pjCwRvWDFTXi0XCbwscR8vgg6YXB_fAJJ-V-gffUZUomgTxiAfHqmfAM_wrF32no7wdvEVHU8pKbpJnOcP2xADUMpZLdCoPKnj6o__aY8DLeOdhHF0000__y30000)

---

## **Mối quan hệ phụ thuộc giữa các hệ thống con (Subsystem Dependencies)**

![Sơ đồ](https://www.planttext.com/api/plantuml/png/b9B12e9048Rl-nHBTr-WGmZLmKCG6Lt2mwY3BAsxiZj64ZrPXnwfLqWbSKsXEYryFnypyxFF-yEt18RANB82aXDao6SRKFMx5pacO58Ubh6jB64-urV6-J7eaX3DMIGOyOP-m20lPEJo0qYH0cape3iij1KrhI9sO_qAAo28mU9eU1SijLAOaD1gAAulX4Q1x4NxDhTG6IrbsC9MchZ4ynRJf_0vBorQDXqEjFxIFoIdY97bPgqqKS8FeuO5r89GX9a1SZLd-QyIyr6bpSzv0G00__y30000)
