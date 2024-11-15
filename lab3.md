## 1. Subsystem context diagrams
### 1.1. Biểu đồ ngữ cảnh của các hệ thống con và giải thích
**BankSystem**
- `Biểu đồ ngữ cảnh`:
![Context](https://www.planttext.com/api/plantuml/png/h5B1JiCm3BtxAwoTXaGdk4vHDG6NtP3s1I7rjcXfKZdkj0hnB_m71oH-Y5yWNMcLiIidEyz-VizMlZy-Lr4qIrix42kEy47xmwQBGZLksfSuP4zMxrZN0CRf6F5PTnoSUmnU-aYCIfdXKPQlyFMEoArlXgxv3Rm1M2_4Msq8rvc2KXF-I-ov5JKXMfdhf6FsP0wun36znSG8_OW4zc7jju5hBJRuiz3Wy48ZJdiq74xT_ofDJAN8fnEcyPc7Z0DmVRRPtM9nFokASaWkRhF4oZ8P6KtYMIRYqMh8-mgskxqKPROpvELK6Jt-nQyShiXNwIly0000__y30000)
- `Giải thích`:
  - Biểu đồ này mô tả cách hệ thống tính lương tương tác với hệ thống ngân hàng (BankSystem) để thực hiện gửi tiền trực tiếp cho nhân viên.
  - PayrollController: Đây là thành phần điều khiển quá trình tính lương, chịu trách nhiệm khởi tạo và thực thi việc gửi tiền.
  - IBankSystem: Giao diện này định nghĩa phương thức deposit() mà PayrollController sẽ sử dụng để gửi tiền.
  - BankSystem: Đây là hệ thống con thực hiện việc gửi tiền. Nó thực hiện giao diện IBankSystem.
  - Paycheck: Chứa thông tin về phiếu lương, bao gồm số tiền cần gửi.
  - BankInformation: Chứa thông tin tài khoản ngân hàng của nhân viên, bao gồm số tài khoản và tên ngân hàng.

**PrintService**
- `Biểu đồ ngữ cảnh`:
![Context](https://www.planttext.com/api/plantuml/png/f54xZi8m4Etd55D2mGKGYYBjRa67o0cytWbO-1ED1qIqucGKUwIz0WwoeXZeg6pD-yppy__rhuwYM8xEWXYnX1isNXhYaz64pV4xzb78uQTHErOEG5iL8svKpy7QvWv2KX2tAWdMXVmN4B4R9XzxqeTPKkdXCX_dMz9aEfdbSmwNSSFKQBMAOvAEmxclglVCCpSPaq_lJduP-NAT3JtHshU1dH8J_3Cf6qu1A1h1HLLMiKIjh8ModWMRtLuITJg5aZAWEUm3KhtA2g_o3oOvCa1D_YVzzWq00F__0m00)
- `Giải thích`:
  - PayrollSystem: Đại diện cho toàn bộ hệ thống tính lương.
  - IPrintService: Giao diện này định nghĩa các phương thức printCheck() và printReceipt() để in phiếu lương và biên lai.
  - PrintService: Đây là hệ thống con thực hiện việc in ấn. Nó thực hiện giao diện IPrintService.
  - Paycheck: Chứa thông tin về phiếu lương cần in.
  - EmployeeInformation: Chứa thông tin nhân viên, có thể được sử dụng để in trên phiếu lương hoặc biên lai.
  - Receipt: Chứa thông tin biên lai cần in.

**ProjectManagementDatabase subsystems**
- `Biểu đồ ngữ cảnh`:
![Context](https://www.planttext.com/api/plantuml/png/l99BQiCm48RtSmhXLLE8YRSbc42zoQ8Xa1ECrOcY8ib5CuQQqhla7baKSg5SeMfnWmkrk-jszCt_67GvlQzOC4hh7OWLHseRcoVIye013NaAKg5WZKngrzRSiP1NbKKJqGDeXyngYrridDjzFO8DGd6FcjHwNEiLpaUb34cFhCE-YHx5Dk7ckHzLis_e_e3HqARrDSKXgGVp6RnTyupQBfTyBP5iNhgo_9Se0p9bI8ci9EkU6P4SWl3Zn6fUJjtsJg7Mn0mJp3nQSv2aCoLJm8H0sisAFB_DVkdurzuYpujih3V0YiBZvuVy0000__y30000)
- `Giải thích`:
  - PayrollSystem: Đại diện cho toàn bộ hệ thống tính lương.
  - IProjectManagementDatabase: Giao diện này định nghĩa các phương thức getProjectInformation() và getChargeNumberInformation() để truy vấn thông tin từ cơ sở dữ liệu.
  - ProjectManagementDatabase: Đây là hệ thống con cung cấp quyền truy cập vào cơ sở dữ liệu. Nó thực hiện giao diện IProjectManagementDatabase.
  - ProjectInformation: Chứa thông tin về dự án, được trả về bởi getProjectInformation().
  - ChargeNumberInformation: Chứa thông tin về mã tính phí, được trả về bởi getChargeNumberInformation().
  ### 1.2. Mô tả hệ thống con, interface của hệ thống con
  **BankSystem**
- `Hệ thống con`: BankSystem là một hệ thống bên ngoài, chịu trách nhiệm xử lý các giao dịch ngân hàng, đặc biệt là gửi tiền trực tiếp vào tài khoản nhân viên. Hệ thống tính lương của Acme sẽ tương tác với BankSystem để thực hiện các khoản thanh toán cho nhân viên thông qua chuyển khoản ngân hàng.
- `Interface`: IBankSystem định nghĩa phương thức deposit(aPaycheck: Paycheck, intoBank: BankInformation) để gửi một khoản tiền (Paycheck) vào tài khoản ngân hàng được chỉ định (BankInformation). Interface này đóng vai trò trung gian cho phép hệ thống tính lương tương tác với BankSystem mà không cần biết chi tiết về cách thức hoạt động bên trong của hệ thống ngân hàng.

 **PrintService** 
- `Hệ thống con`: PrintService là một hệ thống in ấn bên ngoài, có thể là một máy in mạng hoặc một dịch vụ in ấn đám mây. Hệ thống tính lương sẽ sử dụng PrintService để in phiếu lương giấy cho những nhân viên yêu cầu.
- `Interface`: IPrintService định nghĩa hai phương thức:
  - printCheck(Paycheck): In phiếu lương.
  - printReceipt(Receipt): In biên lai. Interface này cho phép hệ thống tính lương giao tiếp với PrintService mà không cần quan tâm đến loại máy in hay dịch vụ in cụ thể.
**ProjectManagementDatabase subsystems**
- `Hệ thống con`: ProjectManagementDatabase là một hệ thống cơ sở dữ liệu hiện có của Acme, lưu trữ thông tin về các dự án và mã tính phí. Hệ thống tính lương cần truy cập cơ sở dữ liệu này để lấy thông tin về dự án và mã tính phí liên quan đến thời gian làm việc của nhân viên.
- `Interface`: IProjectManagementDatabase định nghĩa hai phương thức:
  - getProjectInformation(projectID): Lấy thông tin về một dự án dựa trên projectID.
  - getChargeNumberInformation(chargeNumber): Lấy thông tin về một mã tính phí dựa trên chargeNumber. Interface này đóng vai trò lớp trừu tượng, che giấu chi tiết về cơ sở dữ liệu (DB2 trên IBM mainframe) và cách thức truy cập dữ liệu.
