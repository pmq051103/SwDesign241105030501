
## 1.	Đề xuất kiến trúc, giải thích lý do lựa chọn và ý nghĩa từng thành phần trong kiến trúc, vẽ biểu đồ package mô tả kiến trúc. <br>

### 1.1.	Đề xuất kiến trúc :<br>
-	Mô hình MVC (Model-View-Controller) để tổ chức code và tăng tính linh hoạt.<br>

### 1.2.	Lý do lựa chọn  :<br>
-	Phân tách mối quan tâm: MVC giúp phân tách rõ ràng giữa dữ liệu, giao diện và logic xử lý, giúp code dễ đọc, dễ bảo trì và dễ kiểm thử. 
-	Tái sử dụng: Các thành phần trong MVC có thể được tái sử dụng cho các chức năng khác nhau trong hệ thống. 
-	Dễ dàng bảo trì: Việc thay đổi giao diện hoặc logic nghiệp vụ sẽ không ảnh hưởng đến các thành phần khác.<br>

### 1.3.	Ý nghĩa từng thành phần :<br>
-	Model: Biểu diễn dữ liệu và logic nghiệp vụ liên quan đến dữ liệu đó (ví dụ: Employee, Timecard, Order). 
-	View: Hiển thị dữ liệu cho người dùng và xử lý tương tác của người dùng (ví dụ: các cửa sổ giao diện, báo cáo). 
-	Controller: Tiếp nhận yêu cầu từ người dùng, xử lý logic nghiệp vụ và cập nhật Model, sau đó chọn View phù hợp để hiển thị kết quả.<br>

### 1.4.	Biểu đồ package mô tả kiến trúc<br>
![Package](https://www.planttext.com/api/plantuml/png/V99DJiCm48NtSugvG3PTia1L6zX5gW1rFpYZojG_aJq8HLLEne8ZSGMS19mGGXUMx7apVj-J_Vd-iOr2GLwj0OXdxJ3uo02YnJ0Ug0tU67niex350lU6OiHIqocG1MX8dUd4UDJyXXT0L8DUaNRtFjYXX6braBKxsnZVCa_wek616nzaANUJsTuxwQaup2o_IHVQFzxNkqQ0rPuPHULhDdy1LYFz-5x9kmRof2qh2lMliSHGaj0pHSQy6Hl6gNAtkNIpyo7u5rPIaKlObfsKkq7lxnhUhIXkfx0movs48IMCMTCnEqAEr5Spw0sgD9vUFm9isTNzh_e2003__mC0)

## 2.	Cơ chế phân tích :
-	Persistency
Lý do: Hệ thống cần lưu trữ thông tin về nhân viên và các bảng chấm công, hóa đơn mua hàng, báo cáo, phương thức thanh toán, v.v., để có thể truy cập và cập nhật dữ liệu một cách đáng tin cậy. Tính bền vững giúp duy trì dữ liệu lâu dài, bảo đảm rằng dữ liệu của nhân viên không bị mất sau khi hệ thống ngừng hoạt động và đảm bảo rằng các bản ghi lương luôn sẵn sàng khi cần.
-	Legacy Interface (kết nối với hệ thống cũ ):
Lý do: Hệ thống mới cần tích hợp và truy xuất thông tin từ cơ sở dữ liệu quản lý dự án cũ (DB2) trên mainframe IBM mà không làm thay đổi cơ sở dữ liệu hiện tại. Vì lý do chi phí, Acme muốn tận dụng lại hệ thống cũ mà không phải thay thế nó, vì vậy cần một giao diện giúp hệ thống mới tương tác mà không gây ảnh hưởng đến dữ liệu cũ.
-	Security (Bảo mật):
Lý do: Hệ thống phải đảm bảo rằng chỉ nhân viên có quyền mới có thể xem và chỉnh sửa dữ liệu cá nhân của họ. Ngoài ra, cần ngăn chặn truy cập trái phép để bảo vệ thông tin nhạy cảm về nhân viên và tiền lương. Bảo mật giúp duy trì quyền riêng tư, tuân thủ các yêu cầu bảo mật nội bộ và tránh các rủi ro về truy cập trái phép.
  #3.	Phân tích ca sử dụng payment : <br>
## 3. Phân tích ca sử dụng Payment :<br>
### 3.1.	Lớp phân tích :<br>
-	Boundary: PaymentForm, ProjectManagementDatabase 
-	Control: PaymentController 
-	Entity: Employee <br>

### 3.2.	Biểu đồ sequence :<br>
![Sequence]( https://www.planttext.com/api/plantuml/png/b5DBJiCm4Dtx55w2H2_G1UeNr4L4HTK3JEDfCJXsi2ULSZOM78ahC4uSwfQFn3AUzzwyDpFvU7kV109FJMK4QJ8ejxK2Ghc6ja9Bia1wSagEv0PV6xGboeM6WuTA22Z9URciQkDQH0b1RWDwiNEDLU3RGUBE-IeMxxShKJfBtfcXDEy_3Ve8MCy5lsbgppINHQRetJEML8250qQ11H3i87J0nKo8Q42ERcClEPQFqNAW8Cd9fezLfrXL5oj6qCVu7ir54dFNSwRwddfrVOAmFIunO5amu82qidkE1gITdJVUisoADTZlPvThS1XciyPYnXhi2BWJUOr7C3cEip1YD3HByXVkfJuP40fpScmoHFaVcHtsAViHAXrg0sqAzb17U62dQLRTlCTy4XqgVFLmFV1Y7niqlBqmE02h98FHXpCp-HfuogdrojODh-CcFXMWZRQ7gL8UGyWhCx0lqxBaUna8AKsdnaFMyGhEIzs4GsSjzVfZRmdy3PbjjR-qlxRfx5xxAYJanVJF5_d3BXAz6nPtoV1yeR_ifSmuEIEU_GIjuj__4m00__y30000)

### 3.3.	Nhiệm vụ của từng lớp :<br>
-	Boundary : <br>
•	User Interface Class : PaymentForm : Hiển thị UI và các trường input để người dùng nhập <br>
•	System Interface Class : ProjectManagementDatabase : Truy xuất thông tin theo payment method hiện tại để hiển thị lên UI<br>
-	PaymentController : Xử lí các request payment
-	Entity : Employee : Đại diện cho employee, chứa các thông tin và phương thức liên quan đến employee<br>

### 3.4.	Một số thuộc tính và quan hệ của lớp phân tích : <br>
-	**Lớp Timecard:** <br>
  - Thuộc tính:<br>
    - `hoursWorked`: Số giờ làm việc. Kiểu dữ liệu là số thực (float). Thuộc tính này dùng để lưu trữ tổng số giờ làm việc của nhân viên trong một chu kỳ thanh toán cụ thể.<br>
    -	`payPeriod`: Chu kỳ thanh toán (ví dụ: tuần, tháng). Kiểu dữ liệu là chuỗi (string). Thuộc tính này xác định khoảng thời gian mà thẻ chấm công áp dụng. <br>
- Quan hệ<br>
    -	`Liên kết với Employee`: Mỗi Timecard thuộc về một Employee. Đây là mối quan hệ một-nhiều (0..* - 1) từ Timecard đến Employee, nghĩa là một nhân viên có thể có nhiều thẻ chấm công, nhưng mỗi thẻ chấm công chỉ thuộc về một nhân viên duy nhất.
    - `Liên kết với TimecardController`: TimecardController có thể truy cập và quản lý các Timecard. TimecardController chịu trách nhiệm tạo mới, cập nhật, lưu trữ và truy xuất thông tin của các Timecard.<br>
-	**Lớp Employee:** <br>
  - Thuộc tính:<br>
    -	`name`: Tên nhân viên. Kiểu dữ liệu là chuỗi (string).
    -	`employeeId`: Mã nhân viên. Kiểu dữ liệu là số nguyên (integer). Đây là mã định danh duy nhất của mỗi nhân viên trong hệ thống.
    -	`bankInfo`: Thông tin ngân hàng. Kiểu dữ liệu là chuỗi (string). Thuộc tính này có thể lưu trữ thông tin số tài khoản, tên ngân hàng, chi nhánh...
    -	`socialSecurityNumber`: Mã số an sinh xã hội. Kiểu dữ liệu là chuỗi (string).
    -	`address`: Địa chỉ. Kiểu dữ liệu là chuỗi (string).
    -	`phoneNumber`: Số điện thoại. Kiểu dữ liệu là chuỗi (string).
    -	`email`: Email. Kiểu dữ liệu là chuỗi (string).
    -	`paymentMethod`: Phương thức thanh toán. Kiểu dữ liệu là chuỗi (string). 
- Quan hệ:<br>
    -	`Liên kết với Timecard`: Một nhân viên có thể có nhiều thẻ chấm công. Mỗi nhân viên có thể tạo nhiều thẻ chấm công cho các chu kỳ thanh toán khác nhau.
-	**Lớp TimecardForm:** <br>
- Quan hệ:<br>
  -	`Liên kết với TimecardController`: TimecardForm tương tác với TimecardController để hiển thị, nhập liệu và quản lý thông tin thẻ chấm công. TimecardForm đóng vai trò là giao diện người dùng, cho phép người dùng nhập liệu, xem và chỉnh sửa thông tin trên thẻ chấm công. TimecardController sẽ xử lý các yêu cầu từ TimecardForm và cập nhật lại thông tin trên giao diện.
-	**Lớp TimecardController:** <br>
  - Thuộc tính:<br>
    -	`currentTimecard`: Tham chiếu đến thẻ chấm công hiện tại đang được xử lý. Kiểu dữ liệu là Timecard. Thuộc tính này lưu trữ thông tin về thẻ chấm công mà người dùng đang thao tác.<br>
- Quan hệ:<br>
    -	`Liên kết với TimecardForm`: Nhận dữ liệu từ TimecardForm và cập nhật TimecardForm. TimecardController nhận dữ liệu đầu vào từ TimecardForm , xử lý dữ liệu và cập nhật lại thông tin hiển thị trên TimecardForm.<br>
    -	`Liên kết với ProjectManagementDatabase`: Truy cập cơ sở dữ liệu để lấy thông tin. TimecardController có thể truy cập ProjectManagementDatabase để lấy các thông tin cần thiết, ví dụ như danh sách mã tính phí, thông tin nhân viên.<br>
    -	`Liên kết với Timecard`: Quản lý và cập nhật thông tin Timecard. TimecardController thực hiện các chức năng tạo mới, cập nhật, lưu trữ và xóa Timecard.
-	**Lớp ProjectManagementDatabase:** <br>
-	Quan hệ: <br>
    -	`Liên kết với TimecardController`: Cung cấp thông tin cho TimecardController. ProjectManagementDatabase lưu trữ dữ liệu và cung cấp cho TimecardController khi được yêu cầu.<br>

### 3.5.	Biểu đồ lớp : <br>
![Class]( https://www.planttext.com/api/plantuml/png/T5FBJkDG3DtdAxm4YKgiArHHaeuKCOMAnnevYSdSwNraxdMG2kBBMCmdpI_WF9f9Iidk-jZd-DZElu-_bu7HSsrq58MjiXLwD91h3679x5LMCwMvi_VgbU0yYbYn9eWR71A5PPFzx3niS6V8CZm6GJ5G5BKS-_WFvmrSN6IkjWNwtM81Rn78LwXGQTprMRSLAsV3oMcBbSHzV4tyonMfhMh-ZwrHQMNBPL5u2k40l4AxNUQvoF4OwULYPv-LDzYeJP6LzywlXGzB4kHziE7TRyf5qmhGj9GWOoO-ZvaI_TJAK3g1kFPU2dehArDfjoFgB4qakWJfZRtJchnGvzrZoYnsffm3LvFoWbeLA4iRsGxuGiTowwh9F4I6ZlQzIYE2Azuxd07rI9h079JbDcZHa3o3N8qjsqWrPXuWUDkayVNZvWpMo_Jd6IJftIf-U4fMczlxzE6zhSnaVpTV-B3Rw4rjCXdF13AJQnXZOf-qxExO00vFh7C_ljdPxCXYvk3fJqsXcUzNL4g6oStx6N-N-FrTpK7gK8J41ybIXI6w95l8d_e9003__mC0)

## 4.	Phân tích ca sử dụng Maintain Timecard :<br>

### 4.1.	Lớp phân tích :<br>
-	Boundary :<br>
•	User Interface Class : Timecard Form<br>
•	System Interface Class : ProjectManagementDatabase<br>
-	Control : TimecardController
-	Entity : TimeCard, Employee<br>
### 4.2.	Biểu đồ sequence :<br>
![Sequence](https://www.planttext.com/api/plantuml/png/b9H1ReCm44NtFeMNH6eka4KLYQPg5gsggXUOs9E42cmq394uMnSzKgzGOq8CJPmGTZRp_iVVC_n-_omh1kAwo0KejYHNHPdR1b5iR6qqK2C_im8La7wsL0Xb3PFDJvjfjywH11hEE9G7WNUoNwZu5Gpii71bJy2mWGg5Ute_ENySEIsaBT4aCp7S71O5vuNS8QSraPFktoPur5th816GeP37-yNQREr5LiuZteHSav6gyvVS7_-IwTaPTLQLEJJdj82SvSgme_QsfafktTseFT0EfQcBZSjRkYUU7hRiIukwTUh1DyybNk_XADRjpRpObAJhKWFZAUMRMh78xzM9nkyQSfjH0PnP4tMEvjvzXWwvepbc_u5C6Hwm3rrPZTNacDg6z5pQOicrJABJ4L69rj_iqDX1fdNeaFOfNHdT2WxXRgUDy0ZvFmwtHxZ5amdJEcgNkm9e7SQuMBeSsZ_d7m000F__0m00) <br>
### 4.3.	Nhiệm vụ của từng lớp <br>
-	Boundary :<br>
•	User Interface Class: Timecard Form : Hiển thị UI và các trường input để người dùng nhập <br>
•	System Interface Class: ProjectManagementDatabase : Truy xuất thông tin theo Timecard method hiện tại để hiển thị lên UI<br>
-	Control : <br>
•	TimecardController : Xử lí các request Timecard<br>
-	Entity : <br>
•	Timecard : Lưu trữ thông tin chi tiết về số giờ làm việc của nhân viên theo từng giai đoạn trả lương (pay period).<br>
### 4.4.	Một số thuộc tính và quan hệ giữa các lớp phân tích :
-	**Lớp Timecard**:<br>
  -	Thuộc tính: <br>
      -	`hoursWorked`: Số giờ làm việc. Kiểu dữ liệu có thể là số thực (float) hoặc số nguyên (integer).<br>
      -	`payPeriod`: Chu kỳ thanh toán (ví dụ: tuần, tháng). Kiểu dữ liệu có thể là chuỗi (string) hoặc một kiểu liệt kê (enum) xác định các chu kỳ thanh toán hợp lệ.<br>
-	Quan hệ: <br>
      -	`Liên kết với Employee`: Mỗi Timecard thuộc về một Employee. Đây là mối quan hệ một-nhiều (0..* - 1) từ Timecard đến Employee, nghĩa là một nhân viên có thể có nhiều thẻ chấm công.<br>
      -	`Liên kết với TimecardController`: TimecardController có thể truy cập và quản lý các Timecard. Mối quan hệ này được thể hiện qua thuộc tính currentTimecard trong TimecardController.<br>
-	**Lớp Employee:** <br>
  -	Thuộc tính: <br>
      -	`name`: Tên nhân viên. Kiểu dữ liệu là chuỗi (string).<br>
      -	`employeeId`: Mã nhân viên. Kiểu dữ liệu có thể là số nguyên (integer) hoặc chuỗi (string).<br>
      -	`bankInfo`: Thông tin ngân hàng. Kiểu dữ liệu có thể là một lớp riêng biệt hoặc một chuỗi (string) chứa thông tin này.<br>
      -	`socialSecurityNumber`: Mã số an sinh xã hội. Kiểu dữ liệu là chuỗi (string).<br>
      -	`address`: Địa chỉ. Kiểu dữ liệu là chuỗi (string).<br>
      -	`phoneNumber`: Số điện thoại. Kiểu dữ liệu là chuỗi (string).<br>
      -	`email`: Email. Kiểu dữ liệu là chuỗi (string).<br>
      -	`paymentMethod`: Phương thức thanh toán. Kiểu dữ liệu có thể là một kiểu liệt kê (enum) hoặc chuỗi (string).<br>
-	Quan hệ: <br>
      -	`Liên kết với Timecard`: Một nhân viên có thể có nhiều thẻ chấm công.<br>
-	**Lớp TimecardForm:** <br>
  -	Quan hệ: <br>
      -	`Liên kết với TimecardController`: TimecardForm tương tác với TimecardController để hiển thị, nhập liệu và quản lý thông tin thẻ chấm công.<br>
-	**Lớp TimecardController:** <br>
  -	Thuộc tính: <br>
      - `currentTimecard`: Tham chiếu đến thẻ chấm công hiện tại đang được xử lý.<br>
-	Quan hệ: <br>
      -	`Liên kết với TimecardForm`: Nhận dữ liệu từ TimecardForm và cập nhật TimecardForm.<br>
      -	`Liên kết với ProjectManagementDatabase`: Truy cập cơ sở dữ liệu để lấy thông tin về mã tính phí.<br>
      -	`Liên kết với Timecard`: Quản lý và cập nhật thông tin Timecard.<br>
  -	**Lớp ProjectManagementDatabase:** <br>
- Quan hệ: <br>
      -	`Liên kết với TimecardController`: Cung cấp thông tin về mã tính phí cho TimecardController.<br>

### 4.5.	Biểu đồ lớp : <br>
![Class]( https://www.planttext.com/api/plantuml/png/Z5DBJiCm4Dtd5AEk08bIjYYgG7ma5aX8S869FMrCOpiQEw22E1aBZiGLc2PrA6cBM2InP_pclNdZV7rydeU871jRPM5XN8sC5bI58Lp4oAPe8jqgxnxCAy4aozeCF1fB2bdVUBQGvuLld4PUJgVmbW6SW3QXhd09SNtkuB0D-vhSUaak4aFf6mumymogH9uJkCOMn65zoA9nKPvXdO3Fj1bx7-gwz2wohogXo7FLRNfnSugW6cQHC2pSfZebocjAEffQOwH_gxXd_qGgtg73ELcXkSA81GRQPTKEogrs12TLJ4oephONpmlIigt5wPhOUDthskWdAGJZPdvlGptdjQqhloGQSZgq91zAQRCYAz0jshgo3buPh22GU2kmzIWbWLepXR0IMdf7FmcI-LQT_fLBO2cMqeD8-NM_HgSZE6xVs-FDTanyD1cFEqYts3kEly4RV72MBaoAzD0MS9G0oRmiEoUdvP_w1W00__y30000) <br>

## 5. Hợp nhất kết quả phân tích và tài liệu mô tả: <br>
### 5.1. Biểu đồ hợp nhất :
![Class]( https://www.planttext.com/api/plantuml/png/X5JTRjem5BxtKnnnmrOLL6uhL9K2awAD5gtiUZBn0JmIExATJgpga-rYZxHNs4dif0a1Ti6Fp-ztllFPVt__kRUE6vUd2RDxgJ9kU0fnmgsTE6VaEdSOnLezory8DupruK7dId1py45eMVaBItv8KRbFsgGm7gz3qDqTl3808MsMy4E8USgSrCf--4YUBRfWNQ3RQH6fB7ULPy5b8jLs8eH1Qrkk1wxsapYcDkxT7jfCjTf8a_AYIzC-DqQR1LNYMoJx6mlGLpB5c1jn4Jku45LMr1dwqWGS3UnqRYnij85unyqMGUNf6eqVCULIEVgqArZ-WarBZMPfz0-CQNP5C0jYPjpnDRVOXKOyH8gw-b6dkJ4K7kYSfrcY3uYUregs2b-i1LhVjG_4bpCwERtGu4neol4uzeTcU-A-tRZHy8KdKd0IKBsXOkfkN9uLKSVspdukGu7OmsZJV6Bcgjz_zz67kNBI7IkzOfP0OEaF633OendS0gsSJ8gdI0TB5qbjwPmrHwmTyBgCff-_BQzXCOc-NCCi-ZgVhhxFvikdvsZrHdbhKllZKItkrVzOAgtfI5ktfjL-frMbpQOTYvHtGuVuuqczt7zgiqVXfu8CZTGYy5WpN_59T6pq6UfBeYVMwbYMChQi-PGC1dSdb7WBlT6enxgEClpi1IhIXiEhSudrOkiurdeQUgCU3ChlhYBP2P7sReP3d-B_d0LsERdHZv05bLUMEhLCkAeIgb4OkqSbw77_1m00__y30000) <br>

### 5.2. Tài liệu mô tả :
- **Các tác nhân tham gia:** 
  * **Employee**: Ghi nhận thời gian làm việc, tạo đơn hàng bán hàng (nếu có), và chọn phương thức thanh toán.
  * **Payroll Administrato**: Quản lý thông tin nhân viên, thiết lập các thông tin như loại hình thanh toán (theo giờ, cố định, hoặc theo hoa hồng), và tạo báo cáo hành chính.
  * **Project Management Database**: Cơ sở dữ liệu hiện có chứa thông tin về các dự án và mã chi phí, được hệ thống Payroll truy xuất để phục vụ quá trình quản lý chấm công.
- **Các lớp phân tích tham gia** 
  - **Boundary Classes**:
    - **TimecardForm**: giao diện cho nhân viên nhập và quản lý bảng chấm công.
    - **PaymentForm**: giao diện cho nhân viên chọn và thay đổi phương thức thanh toán.
    - **ProjectManagementDatabase**: truy xuất thông tin mã chi phí từ cơ sở dữ liệu dự án.
  - **Control Classes**:
    - **TimecardController**: xử lý dữ liệu từ TimecardForm và truy xuất mã chi phí từ ProjectManagementDatabase.
    - **PaymentController**: xử lý việc chọn và cập nhật phương thức thanh toán của nhân viên.
  - **Entity Classes**:
    - **Employee**: chứa thông tin nhân viên bao gồm loại hình thanh toán, phương thức thanh toán, giờ làm, và thông tin ngân hàng.
    - **Timecard**: ghi nhận thời gian làm việc và số giờ làm cho mỗi nhân viên.


