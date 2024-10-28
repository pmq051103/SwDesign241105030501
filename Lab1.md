1.	Đề xuất kiến trúc, giải thích lý do lựa chọn và ý nghĩa từng thành phần trong kiến trúc, vẽ biểu đồ package mô tả kiến trúc.
1.1.	Đề xuất kiến trúc :
-	Mô hình MVC (Model-View-Controller) để tổ chức code và tăng tính linh hoạt.
1.2.	Lý do lựa chọn  :
-	Phân tách mối quan tâm: MVC giúp phân tách rõ ràng giữa dữ liệu, giao diện và logic xử lý, giúp code dễ đọc, dễ bảo trì và dễ kiểm thử. 
-	Tái sử dụng: Các thành phần trong MVC có thể được tái sử dụng cho các chức năng khác nhau trong hệ thống. 
-	Dễ dàng bảo trì: Việc thay đổi giao diện hoặc logic nghiệp vụ sẽ không ảnh hưởng đến các thành phần khác.
1.3.	Ý nghĩa từng thành phần :
-	Model: Biểu diễn dữ liệu và logic nghiệp vụ liên quan đến dữ liệu đó (ví dụ: Employee, Timecard, Order). 
-	View: Hiển thị dữ liệu cho người dùng và xử lý tương tác của người dùng (ví dụ: các cửa sổ giao diện, báo cáo). 
-	Controller: Tiếp nhận yêu cầu từ người dùng, xử lý logic nghiệp vụ và cập nhật Model, sau đó chọn View phù hợp để hiển thị kết quả.
1.4.	Biểu đồ package mô tả kiến trúc
![Package]( https://www.planttext.com/api/plantuml/png/V5MzajCm4Exr52f3aOOo1NFS6UOe0XaIO2WLQyyHqOzd9UV6mzoJKV18l0AIBTcouvohQFVR_NQ_NId__loziuwXQvGan9w5fcWi4EA4aq1th4KZ9Tstre6YQ_eWcRMq4An2fWYfMNbc5T3l0fxfRq9fsVctJEYF1bLd2fyzcUTWt9S8e5TlDlHY18_E4zDSmZSB-BvqmcYR-L_8aFI3ggLf0IQ9kR2rP6to5U2Oa7P6O9kZ4kuW59GC-SnPUleATWXFWA1BkC7-5Mg3Ri9TWGPa3X9v3vcbZmLw8H-5TGRRPV-ZQT3-C7W6Fk5_6JL-CDg5OG1cIiS1pNpXgz7uPcm4p9jcicoahzsx5MYtIZrus9Cqp2rBlq33E4_UF4d6rTGy4-a6246PomWIsb68Xq_ybO4iL9J64iTnbQgtpzNT6WxoMjWXQwxOabfz4mu5N9AeMt0dmtFmtljrjQnjP5hJQS7Hs4TIpHHCBLv_z6EEnWaphVDJH2IwGrl3G1CEupo7Yv9-J4TLWJiOn-HiPNCX4iINSp255ssrl5VzAAucrsMEurjIByVkqFo2qkKXGK1_gx62puqw0juA_GaC-_9ydQ_GPGKdHOPXXMWQzZkUkoRfQPGc6sfUqoZKbmkWyscx3kP23bjN-6SjF28p8Vq6-mhOaLcWnVtRhgpEG-bWZmfjcVPx7lQXk1znmqkzNh-Rlh0RQchGTeh8Ni7a9vEeF4rsDpT102zwwIp9SemfRs39zViMOjBbt53LTMN90cTUIeQyuXkBo51axAi338FVqDA7UaqyvWuq3_-R_m400F__0m00)

2.	Cơ chế phân tích :
-	Persistency
Lý do: Hệ thống cần lưu trữ thông tin về nhân viên và các bảng chấm công, hóa đơn mua hàng, báo cáo, phương thức thanh toán, v.v., để có thể truy cập và cập nhật dữ liệu một cách đáng tin cậy. Tính bền vững giúp duy trì dữ liệu lâu dài, bảo đảm rằng dữ liệu của nhân viên không bị mất sau khi hệ thống ngừng hoạt động và đảm bảo rằng các bản ghi lương luôn sẵn sàng khi cần.
-	Legacy Interface (kết nối với hệ thống cũ ):
Lý do: Hệ thống mới cần tích hợp và truy xuất thông tin từ cơ sở dữ liệu quản lý dự án cũ (DB2) trên mainframe IBM mà không làm thay đổi cơ sở dữ liệu hiện tại. Vì lý do chi phí, Acme muốn tận dụng lại hệ thống cũ mà không phải thay thế nó, vì vậy cần một giao diện giúp hệ thống mới tương tác mà không gây ảnh hưởng đến dữ liệu cũ.
-	Security (Bảo mật):
Lý do: Hệ thống phải đảm bảo rằng chỉ nhân viên có quyền mới có thể xem và chỉnh sửa dữ liệu cá nhân của họ. Ngoài ra, cần ngăn chặn truy cập trái phép để bảo vệ thông tin nhạy cảm về nhân viên và tiền lương. Bảo mật giúp duy trì quyền riêng tư, tuân thủ các yêu cầu bảo mật nội bộ và tránh các rủi ro về truy cập trái phép.
3.	Phân tích ca sử dụng payment :
3.1.	Lớp phân tích :
-	Boundary: PaymentForm, ProjectManagementDatabase 
-	Control: PaymentController 
-	Entity: Employee 
3.2.	Biểu đồ sequence :
![Sequence]( https://www.planttext.com/api/plantuml/png/b5DBJiCm4Dtx55w2H2_G1UeNr4L4HTK3JEDfCJXsi2ULSZOM78ahC4uSwfQFn3AUzzwyDpFvU7kV109FJMK4QJ8ejxK2Ghc6ja9Bia1wSagEv0PV6xGboeM6WuTA22Z9URciQkDQH0b1RWDwiNEDLU3RGUBE-IeMxxShKJfBtfcXDEy_3Ve8MCy5lsbgppINHQRetJEML8250qQ11H3i87J0nKo8Q42ERcClEPQFqNAW8Cd9fezLfrXL5oj6qCVu7ir54dFNSwRwddfrVOAmFIunO5amu82qidkE1gITdJVUisoADTZlPvThS1XciyPYnXhi2BWJUOr7C3cEip1YD3HByXVkfJuP40fpScmoHFaVcHtsAViHAXrg0sqAzb17U62dQLRTlCTy4XqgVFLmFV1Y7niqlBqmE02h98FHXpCp-HfuogdrojODh-CcFXMWZRQ7gL8UGyWhCx0lqxBaUna8AKsdnaFMyGhEIzs4GsSjzVfZRmdy3PbjjR-qlxRfx5xxAYJanVJF5_d3BXAz6nPtoV1yeR_ifSmuEIEU_GIjuj__4m00__y30000)

3.3.	Nhiệm vụ của từng lớp :
-	Boundary :
•	User Interface Class : PaymentForm :
	Giao diện cho nhân viên nhập thông tin về phương thức thanh toán.
	Hiển thị các yêu cầu thông tin từ hệ thống (ví dụ: yêu cầu nhập địa chỉ hoặc thông tin ngân hàng).
	Xác nhận phương thức thanh toán đã được chọn.
	Hiển thị thông báo xác nhận hoặc lỗi cho nhân viên sau khi thao tác hoàn tất.
•	System Interface Class : DBAdapter : 
	Kết nối với cơ sở dữ liệu để lấy và cập nhật thông tin liên quan đến thanh toán.
	Lưu thông tin về phương thức thanh toán đã chọn của nhân viên.
	Đọc các thông tin chi tiết về lương, thời gian làm việc, và hoa hồng từ cơ sở dữ liệu.
-	Controller :
	Điều khiển luồng xử lý khi nhân viên chọn phương thức thanh toán.
	Xử lý việc cập nhật thông tin thanh toán vào hệ thống và kiểm tra thông tin nhập vào.
	Gửi yêu cầu lấy thông tin từ cơ sở dữ liệu thông qua DBAdapter.
	Tạo các đối tượng Payroll mới khi thanh toán được xác nhận.
-	Entity
•	Employee
	Đại diện cho employee, chứa các thông tin và phương thức liên quan đến employee
3.4.	Một số thuộc tính và quan hệ của lớp phân tích
-	Lớp Timecard:
•	Thuộc tính:
	hoursWorked: Số giờ làm việc. Kiểu dữ liệu là số thực (float). Thuộc tính này dùng để lưu trữ tổng số giờ làm việc của nhân viên trong một chu kỳ thanh toán cụ thể.
	payPeriod: Chu kỳ thanh toán (ví dụ: tuần, tháng). Kiểu dữ liệu là chuỗi (string). Thuộc tính này xác định khoảng thời gian mà thẻ chấm công áp dụng, ví dụ "Tuần 1 tháng 10/2024" hoặc "Tháng 10/2024".
•	Quan hệ:
	Liên kết với Employee: Mỗi Timecard thuộc về một Employee. Đây là mối quan hệ một-nhiều (0..* - 1) từ Timecard đến Employee, nghĩa là một nhân viên có thể có nhiều thẻ chấm công, nhưng mỗi thẻ chấm công chỉ thuộc về một nhân viên duy nhất.
	Liên kết với TimecardController: TimecardController có thể truy cập và quản lý các Timecard. TimecardController chịu trách nhiệm tạo mới, cập nhật, lưu trữ và truy xuất thông tin của các Timecard.
-	Lớp Employee:
•	Thuộc tính:
	name: Tên nhân viên. Kiểu dữ liệu là chuỗi (string). Ví dụ: "Nguyễn Văn A".
	employeeId: Mã nhân viên. Kiểu dữ liệu là số nguyên (integer). Đây là mã định danh duy nhất của mỗi nhân viên trong hệ thống. Ví dụ: 12345.
	bankInfo: Thông tin ngân hàng. Kiểu dữ liệu là chuỗi (string). Thuộc tính này có thể lưu trữ thông tin số tài khoản, tên ngân hàng, chi nhánh... Ví dụ: "1234567890 - Vietcombank - Chi nhánh Hà Nội".
	socialSecurityNumber: Mã số an sinh xã hội. Kiểu dữ liệu là chuỗi (string). Ví dụ: "123456789".
	address: Địa chỉ. Kiểu dữ liệu là chuỗi (string). Ví dụ: "123 đường ABC, Quận 1, TP.HCM".
	phoneNumber: Số điện thoại. Kiểu dữ liệu là chuỗi (string). Ví dụ: "0987654321".
	email: Email. Kiểu dữ liệu là chuỗi (string). Ví dụ: "nguyenvana@email.com".
	paymentMethod: Phương thức thanh toán. Kiểu dữ liệu là chuỗi (string). Ví dụ: "Chuyển khoản ngân hàng".
•	Quan hệ:
	Liên kết với Timecard: Một nhân viên có thể có nhiều thẻ chấm công. Mỗi nhân viên có thể tạo nhiều thẻ chấm công cho các chu kỳ thanh toán khác nhau.
-	Lớp TimecardForm:
•	Quan hệ: 
	Liên kết với TimecardController: TimecardForm tương tác với TimecardController để hiển thị, nhập liệu và quản lý thông tin thẻ chấm công. TimecardForm đóng vai trò là giao diện người dùng, cho phép người dùng nhập liệu, xem và chỉnh sửa thông tin trên thẻ chấm công. TimecardController sẽ xử lý các yêu cầu từ TimecardForm và cập nhật lại thông tin trên giao diện.
-	Lớp TimecardController:
•	Thuộc tính:
	currentTimecard: Tham chiếu đến thẻ chấm công hiện tại đang được xử lý. Kiểu dữ liệu là Timecard. Thuộc tính này lưu trữ thông tin về thẻ chấm công mà người dùng đang thao tác.
•	Quan hệ:
	Liên kết với TimecardForm: Nhận dữ liệu từ TimecardForm và cập nhật TimecardForm. TimecardController nhận dữ liệu đầu vào từ TimecardForm (ví dụ: số giờ làm việc, chu kỳ thanh toán), xử lý dữ liệu và cập nhật lại thông tin hiển thị trên TimecardForm (ví dụ: hiển thị thông báo thành công, thông báo lỗi).
	Liên kết với ProjectManagementDatabase: Truy cập cơ sở dữ liệu để lấy thông tin. TimecardController có thể truy cập ProjectManagementDatabase để lấy các thông tin cần thiết, ví dụ như danh sách mã tính phí, thông tin nhân viên.
	Liên kết với Timecard: Quản lý và cập nhật thông tin Timecard. TimecardController thực hiện các chức năng tạo mới, cập nhật, lưu trữ và xóa Timecard.
-	Lớp ProjectManagementDatabase:
•	Quan hệ: 
	Liên kết với TimecardController: Cung cấp thông tin cho TimecardController. ProjectManagementDatabase lưu trữ dữ liệu và cung cấp cho TimecardController khi được yêu cầu.
3.5.	Biểu đồ lớp :
![Class]( https://www.planttext.com/api/plantuml/png/T5FBJkDG3DtdAxm4YKgiArHHaeuKCOMAnnevYSdSwNraxdMG2kBBMCmdpI_WF9f9Iidk-jZd-DZElu-_bu7HSsrq58MjiXLwD91h3679x5LMCwMvi_VgbU0yYbYn9eWR71A5PPFzx3niS6V8CZm6GJ5G5BKS-_WFvmrSN6IkjWNwtM81Rn78LwXGQTprMRSLAsV3oMcBbSHzV4tyonMfhMh-ZwrHQMNBPL5u2k40l4AxNUQvoF4OwULYPv-LDzYeJP6LzywlXGzB4kHziE7TRyf5qmhGj9GWOoO-ZvaI_TJAK3g1kFPU2dehArDfjoFgB4qakWJfZRtJchnGvzrZoYnsffm3LvFoWbeLA4iRsGxuGiTowwh9F4I6ZlQzIYE2Azuxd07rI9h079JbDcZHa3o3N8qjsqWrPXuWUDkayVNZvWpMo_Jd6IJftIf-U4fMczlxzE6zhSnaVpTV-B3Rw4rjCXdF13AJQnXZOf-qxExO00vFh7C_ljdPxCXYvk3fJqsXcUzNL4g6oStx6N-N-FrTpK7gK8J41ybIXI6w95l8d_e9003__mC0)



4.	Phân tích ca sử dụng Maintain Timecard :
4.1.	Lớp phân tích :
-	Boundary :
•	User Interface Class : Timecard Form
•	System Interface Class : ProjectManagementDatabase
-	Control : TimecardController
-	Entity : TimeCard, Employee
4.2.	Biểu đồ sequence :
![Sequence]( https://www.planttext.com/api/plantuml/png/V5MzajCm4Exr52f3aOOo1NFS6UOe0XaIO2WLQyyHqOzd9UV6mzoJKV18l0AIBTcouvohQFVR_NQ_NId__loziuwXQvGan9w5fcWi4EA4aq1th4KZ9Tstre6YQ_eWcRMq4An2fWYfMNbc5T3l0fxfRq9fsVctJEYF1bLd2fyzcUTWt9S8e5TlDlHY18_E4zDSmZSB-BvqmcYR-L_8aFI3ggLf0IQ9kR2rP6to5U2Oa7P6O9kZ4kuW59GC-SnPUleATWXFWA1BkC7-5Mg3Ri9TWGPa3X9v3vcbZmLw8H-5TGRRPV-ZQT3-C7W6Fk5_6JL-CDg5OG1cIiS1pNpXgz7uPcm4p9jcicoahzsx5MYtIZrus9Cqp2rBlq33E4_UF4d6rTGy4-a6246PomWIsb68Xq_ybO4iL9J64iTnbQgtpzNT6WxoMjWXQwxOabfz4mu5N9AeMt0dmtFmtljrjQnjP5hJQS7Hs4TIpHHCBLv_z6EEnWaphVDJH2IwGrl3G1CEupo7Yv9-J4TLWJiOn-HiPNCX4iINSp255ssrl5VzAAucrsMEurjIByVkqFo2qkKXGK1_gx62puqw0juA_GaC-_9ydQ_GPGKdHOPXXMWQzZkUkoRfQPGc6sfUqoZKbmkWyscx3kP23bjN-6SjF28p8Vq6-mhOaLcWnVtRhgpEG-bWZmfjcVPx7lQXk1znmqkzNh-Rlh0RQchGTeh8Ni7a9vEeF4rsDpT102zwwIp9SemfRs39zViMOjBbt53LTMN90cTUIeQyuXkBo51axAi338FVqDA7UaqyvWuq3_-R_m400F__0m00)
4.3.	Nhiệm vụ của từng lớp 
-	Boundary :
•	User Interface Class: Timecard Form
	Giao diện để nhân viên nhập, cập nhật, và quản lý thông tin về thời gian làm việc.
	Hiển thị các form nhập liệu để nhân viên thêm hoặc chỉnh sửa các bản ghi thời gian làm việc (TimeCard).
	Hiển thị thông báo xác nhận khi cập nhật thành công hoặc thông báo lỗi khi xảy ra sự cố.
•	System Interface Class: ProjectManagementDatabase
	Kết nối với cơ sở dữ liệu quản lý dự án để lưu trữ và truy xuất thông tin liên quan đến thời gian làm việc của nhân viên.
	Lưu thông tin mới về thời gian làm việc hoặc cập nhật lại thông tin thời gian đã chỉnh sửa.
	Đọc thông tin chi tiết về thời gian làm việc của nhân viên từ cơ sở dữ liệu.
-	Control : 
•	TimecardController
	Điều khiển luồng xử lý khi nhân viên thêm, chỉnh sửa hoặc xóa thông tin về thời gian làm việc.
	Kiểm tra tính hợp lệ của thông tin nhập từ Timecard Form và xử lý các yêu cầu lưu trữ vào cơ sở dữ liệu thông qua ProjectManagementDatabase.
	Xử lý các yêu cầu truy xuất dữ liệu từ cơ sở dữ liệu để hiển thị lại cho nhân viên
-	Entity :
•	Timecard
	Lưu trữ thông tin chi tiết về số giờ làm việc của nhân viên theo từng giai đoạn trả lương (pay period).
	Cung cấp các phương thức để lưu và cập nhật thời gian làm việc.
4.4.	Một số thuộc tính và quan hệ giữa các lớp phân tích :
-	Lớp Timecard:
•	Thuộc tính: 
	hoursWorked: Số giờ làm việc. Kiểu dữ liệu có thể là số thực (float) hoặc số nguyên (integer).
	payPeriod: Chu kỳ thanh toán (ví dụ: tuần, tháng). Kiểu dữ liệu có thể là chuỗi (string) hoặc một kiểu liệt kê (enum) xác định các chu kỳ thanh toán hợp lệ.
•	Quan hệ: 
	Liên kết với Employee: Mỗi Timecard thuộc về một Employee. Đây là mối quan hệ một-nhiều (0..* - 1) từ Timecard đến Employee, nghĩa là một nhân viên có thể có nhiều thẻ chấm công.
	Liên kết với TimecardController: TimecardController có thể truy cập và quản lý các Timecard. Mối quan hệ này được thể hiện qua thuộc tính currentTimecard trong TimecardController.
-	Lớp Employee:
•	Thuộc tính: 
	name: Tên nhân viên. Kiểu dữ liệu là chuỗi (string).
	employeeId: Mã nhân viên. Kiểu dữ liệu có thể là số nguyên (integer) hoặc chuỗi (string).
	bankInfo: Thông tin ngân hàng. Kiểu dữ liệu có thể là một lớp riêng biệt hoặc một chuỗi (string) chứa thông tin này.
	socialSecurityNumber: Mã số an sinh xã hội. Kiểu dữ liệu là chuỗi (string).
	address: Địa chỉ. Kiểu dữ liệu là chuỗi (string).
	phoneNumber: Số điện thoại. Kiểu dữ liệu là chuỗi (string).
	email: Email. Kiểu dữ liệu là chuỗi (string).
	paymentMethod: Phương thức thanh toán. Kiểu dữ liệu có thể là một kiểu liệt kê (enum) hoặc chuỗi (string).
•	Quan hệ: 
	Liên kết với Timecard: Một nhân viên có thể có nhiều thẻ chấm công.
-	Lớp TimecardForm:
•	Quan hệ: 
	Liên kết với TimecardController: TimecardForm tương tác với TimecardController để hiển thị, nhập liệu và quản lý thông tin thẻ chấm công.
-	Lớp TimecardController:
•	Thuộc tính: 
	currentTimecard: Tham chiếu đến thẻ chấm công hiện tại đang được xử lý.
•	Quan hệ: 
	Liên kết với TimecardForm: Nhận dữ liệu từ TimecardForm và cập nhật TimecardForm.
	Liên kết với ProjectManagementDatabase: Truy cập cơ sở dữ liệu để lấy thông tin về mã tính phí.
	Liên kết với Timecard: Quản lý và cập nhật thông tin Timecard.
-	Lớp ProjectManagementDatabase:
•	Quan hệ: 
	Liên kết với TimecardController: Cung cấp thông tin về mã tính phí cho TimecardController.
4.5.	Biểu đồ lớp : 
![Class]( https://www.planttext.com/api/plantuml/png/Z5DBJiCm4Dtd5AEk08bIjYYgG7ma5aX8S869FMrCOpiQEw22E1aBZiGLc2PrA6cBM2InP_pclNdZV7rydeU871jRPM5XN8sC5bI58Lp4oAPe8jqgxnxCAy4aozeCF1fB2bdVUBQGvuLld4PUJgVmbW6SW3QXhd09SNtkuB0D-vhSUaak4aFf6mumymogH9uJkCOMn65zoA9nKPvXdO3Fj1bx7-gwz2wohogXo7FLRNfnSugW6cQHC2pSfZebocjAEffQOwH_gxXd_qGgtg73ELcXkSA81GRQPTKEogrs12TLJ4oephONpmlIigt5wPhOUDthskWdAGJZPdvlGptdjQqhloGQSZgq91zAQRCYAz0jshgo3buPh22GU2kmzIWbWLepXR0IMdf7FmcI-LQT_fLBO2cMqeD8-NM_HgSZE6xVs-FDTanyD1cFEqYts3kEly4RV72MBaoAzD0MS9G0oRmiEoUdvP_w1W00__y30000)


