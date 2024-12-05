# Hướng dẫn chạy dự án

## Yêu cầu hệ thống

- **SQL Server**: Để chạy file script cơ sở dữ liệu.
- **.NET Core SDK**: .Net 8 .

## Các bước thực hiện

### Bước 1: Cấu hình cơ sở dữ liệu
1. Mở **SQL Server Management Studio**.
2. Chạy file script SQL được cung cấp trong dự án để tạo cơ sở dữ liệu và bảng.

### Bước 2: Cập nhật chuỗi kết nối
1. Mở file `appsettings.json` trong hai dự án:
   - **AuthorizationServer**
   - **Resource**
2. Tìm mục `"ConnectionStrings"` và chỉnh sửa chuỗi kết nối thành thông tin server SQL trên máy tính của bạn.  
   Ví dụ:
   ```json
   "ConnectionStrings": {
       "DefaultConnection": "Server=`YOUR_SERVER_NAME`;Database=SOA1;Trusted_Connection=yes;MultipleActiveResultSets=true;TrustServerCertificate=Yes"
   }
### Bước 3: Lấy token
1. Chạy **AuthorizationServer** .
2. Đăng nhập bằng **email** và **password** để lấy **JWT token**.

### Bước 4: Sử dụng token để xác thực
1. Chạy **Resouce**
2. Thêm **Bearer Token** vào mục `Authorize`.
   ```text
   Bearer <token>
   ```
### Bước 5: Thực hiện thao tác với API
