## 1. Subsystem context diagrams
### 1.1. Biểu đồ ngữ cảnh của các hệ thống con và giải thích
**BankSystem**
- `Biểu đồ ngữ cảnh`
![Context](https://www.planttext.com/api/plantuml/png/h59BJiCm4DtFAKPT5Ob6PLjPKKNPT8VK4mpE5AmwTcHFAYBWBjo31H8NuWeu3OqSkcKrux7VPvxy_V6vZa91sjg26B6Cj-GEkouArxXh7-BGtHbw35G3Q4inuZrrmLkxyKxwoW6LqiEXB5_WwnqnjAuPNislu0t0EE6m9ysupHIK6kU_m1vRSUEZaJab7Vt4-e0hFBVNc12-fqZ3lcpTteUQn7Xt4XeSJZJYk4SJ_7FtlqeZKYbsAS94dtd8C02NiSsMHN4pMopAePbaiyBA1DPoDeadcOX7Gp39yBKeidqXkqh4ex-_ymjtQtPL-WO_0000__y30000)
- `Giải thích`:
  - Biểu đồ này mô tả cách hệ thống tính lương tương tác với hệ thống ngân hàng (BankSystem) để thực hiện gửi tiền trực tiếp cho nhân viên.
  - PayrollController: Đây là thành phần điều khiển quá trình tính lương, chịu trách nhiệm khởi tạo và thực thi việc gửi tiền.
  - IBankSystem: Giao diện này định nghĩa phương thức deposit() mà PayrollController sẽ sử dụng để gửi tiền.
  - BankSystem: Đây là hệ thống con thực hiện việc gửi tiền. Nó thực hiện giao diện IBankSystem.
  - Paycheck: Chứa thông tin về phiếu lương, bao gồm số tiền cần gửi.
  - BankInformation: Chứa thông tin tài khoản ngân hàng của nhân viên, bao gồm số tài khoản và tên ngân hàng.

**PrintService**
- `Biểu đồ ngữ cảnh`

![Context](https://www.planttext.com/api/plantuml/png/f9B1JeGm48RlVOfcJt20n2iXP8thOMyRUO9QPjd6qf9fLoNgatdmaNm5Ioba6uaUzaIPcV_xEpzyVtvjZMLepvqaLbW9z812sHhmMN2WzVdH3CP2HtU2jSWwGhXanj036r1BMVicSGh08tE2VIH_8vJIVgpSdO0_9Kx5nqEwr1-0W-Xj4fuf-LWSBa5bQPQRzAXVXwgw3Xvc7HYKszlnGkU-wwKU0FRggB5ZLcZrUoW0BniaIeHkRZOqonhzehAiyczHCiNwnUFqolSyHz6UR9v7QP1eoZjveybdfXMqXSbW1vO9QPBqR-7Avfunrs-R1i6CcBMCfeKdKeYde1o1MPW_mp_-Yyf7uwR95bJZVimV0000__y30000)
- `Giải thích`
  - PayrollSystem: Đây là hệ thống tính lương chính, chịu trách nhiệm xử lý dữ liệu lương và yêu cầu in ấn phiếu lương và biên lai.
  - IPrintService: Đây là giao diện định nghĩa các phương thức cần thiết cho việc in ấn, ví dụ như printCheck(Paycheck) và printReceipt(Receipt). Giao diện này giúp tách biệt hệ thống tính lương với hệ thống in ấn cụ thể, cho phép thay đổi hệ thống in dễ dàng hơn.
  - PrintService: Đây là thực thi cụ thể của giao diện IPrintService. Nó nhận yêu cầu in từ PayrollSystem và thực hiện việc in ấn thực tế. Có thể hiểu đây là module/lớp chịu trách nhiệm giao tiếp với máy in, định dạng phiếu lương/biên lai, v.v.
  - Paycheck: Đây là đối tượng chứa thông tin chi tiết về phiếu lương của một nhân viên, bao gồm tên, số tiền, ngày tháng, v.v. Đối tượng này được PayrollSystem tạo ra và truyền vào IPrintService để in.
  - EmployeeInformation: Đây là đối tượng chứa thông tin về nhân viên, như họ tên, địa chỉ, số tài khoản, v.v. Thông tin này có thể được sử dụng để điền vào phiếu lương hoặc biên lai.
  - Receipt: Đây là đối tượng chứa thông tin về biên lai, có thể bao gồm thông tin thanh toán, số tiền, ngày giờ, v.v. Đối tượng này có thể được PayrollSystem hoặc PrintService tạo ra và in ra.

**ProjectManagementDatabase subsystems**
- `Biểu đồ ngữ cảnh`
![Context](https://www.planttext.com/api/plantuml/png/l5AzJiCm4DxlAQnC52aMh2YAAf6b0wXILvPBUdMD_8FiYo02deo1H-8LC2MgWbINJjtik-_k-x6_FZxdaJ5mRmsmPaDY6VmZTNo73XLPSjmWOukHnAflun2Ph6Wqge0Me3COerZY4BmngrqJj6CA6-n8BFAxNa48eOX7nC9jVB38shkBfx7Kp4RCxHQ3ellUjXIcm6vIdy7xNasMjAhYta9YUHdg-Wn29iYa8EdHd8X7J6Rb50X_uXN5TI7ASksVNLdMkri-vfj_dJsuquqTUSxgJSgWrPQbpESF-VbVKpzsfBmi3YHtokoLbEcOyG8m9xTEt_mR003__mC0)
- `Giải thích`
  - PayrollSystem: Hệ thống tính lương chính. Nó cần truy cập thông tin về dự án và mã tính phí từ ProjectManagementDatabase để tính toán lương cho nhân viên (ví dụ, tính lương dựa trên số giờ làm việc cho một dự án cụ thể).
  - IProjectManagementDatabase: Giao diện định nghĩa các phương thức để PayrollSystem yêu cầu dữ liệu từ cơ sở dữ liệu quản lý dự án. Việc sử dụng giao diện giúp PayrollSystem không phụ thuộc vào cấu trúc cụ thể của ProjectManagementDatabase.
  - ProjectManagementDatabase: Thực thi giao diện IProjectManagementDatabase. Đây là thành phần chịu trách nhiệm truy cập và trả về dữ liệu từ cơ sở dữ liệu thực tế (trong trường hợp này là DB2 trên mainframe).
  - ProjectInformation: Đối tượng chứa thông tin chi tiết về một dự án, ví dụ như tên dự án, mã dự án, ngày bắt đầu, ngày kết thúc, v.v. Đối tượng này được ProjectManagementDatabase trả về khi PayrollSystem gọi phương thức getProjectInformation().
  - ChargeNumberInformation: Đối tượng chứa thông tin về mã tính phí, ví dụ như mô tả mã, đơn vị tính phí, v.v. Đối tượng này được ProjectManagementDatabase trả về khi PayrollSystem gọi phương thức getChargeNumberInformation().
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
## 2. Analysis class to design element map
