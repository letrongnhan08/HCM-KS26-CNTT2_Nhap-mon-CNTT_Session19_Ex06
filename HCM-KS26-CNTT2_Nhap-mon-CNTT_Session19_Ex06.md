
# Xây dựng Pre-push Checklist để quét sạch các API Keys bị hardcode:

- **Làm sạch lịch sử Git (nếu vô tình commit thông tin nhạy cảm):**

Dùng git-filter-repo hoặc BFG Repo-Cleaner để xóa vĩnh viễn các file nhạy cảm khỏi toàn bộ lịch sử commit và nhấn git push origin main để cập nhập là xong

 - **Kiểm tra các tệp cấu hình môi trường:**

Dùng tệp .gitignore khai báo tệp .env , để đảm bảo không có tệp .env nào bị theo dõi trong Git qua lệnh git status

# Hướng dẫn team kích hoạt 2FA:
## Thành viên tự kích hoạt 2FA trên tài khoản cá nhân:


- Truy cập GitHub: bấm vào tài khoản avatar -> Setting -> Password and authentication -> kéo xuống tìm Two-factor authentication -> Chọn Enable two-factor authentication.
- Quét mã QR bằng ứng dụng Authenticator và lưu lại những mã code dự phòng xác thực

## Bật tính năng bắt buộc 2FA trên Organization:


- Vào Organization -> Settings -> Chọn Authentication security.
- Tại mục Two-factor authentication -> tích chọn Require two-factor authentication for everyone in (tên) organization.
- Bấm Save và bất kỳ tài khoản nào chưa bật 2FA sẽ tự động bị tước quyền truy cập repo cho đến khi hoàn tất thiết lập 2FA.

### Bản báo cáo đánh giá rủi ro nếu thiếu tệp .gitignore.


- Các DB_USER, DB_PASSWORD bị lộ giúp hacker đăng nhập dễ dàng vào hệ thống.
- Khi không có .gitignore, các file chứa cấu hình nhạy cảm như .env, node_modules sẽ bị đẩy thẳng lên GitHub Public. Hacker sẽ đánh cắp thông tin người dùng hoặc xóa sạch dữ liệu để tống tiền
- API_KEY là mã để xác thực cho phép ứng dụng của mình gọi dịch vụ có phí, thiếu .gitignore thì nó sẽ bị đánh cắp và sẽ bị đào tiền ảo