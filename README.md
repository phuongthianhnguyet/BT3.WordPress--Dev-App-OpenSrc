# BT3.WordPress--Dev-App-OpenSrc
## Mô tả dự án
Dự án sử dụng Docker Compose để khởi chạy một hệ thống WordPres đầy đủ gồm
- MariaDB: Hệ quản trị csdl
- phpMyAdmin: Công cụ quản lý database trực quan
- WordPres: Nền tảng CMS để tạo website
## Yêu cầu hệ thống
CÀI ĐẶT:
- Docker
- Ubuntu
- Cloudflare
### Kiểm tra phiên bản
docker --version
## Các bước setup
- Cấu hình file .env
- Nội dung .env
```
MYSQL_ROOT_PASSWORD=root123
MYSQL_DATABASE=wordpressdb
MYSQL_USER=wpuser
MYSQL_PASSWORD=wp123
WORDPRESS_PORT=8090
PHPMYADMIN_PORT=8091
```
- Tạo thư mục volumes
- Khởi chạy Docker Compose
```
Chạy tất cả services ở background
docker compose up -d
```
- Kiểm tra các services
```
# Xem trạng thái containers
docker compose ps
# Xem logs (nếu cần debug)
docker compose logs -f wordpress
```
### Trang WordPress
<img width="960" height="540" alt="4" src="https://github.com/user-attachments/assets/0d88a696-bfea-4112-b0cb-4974b6204898" />
### Trang phpMyAdmin
<img width="960" height="537" alt="3" src="https://github.com/user-attachments/assets/aaff5a69-cfa1-48b2-adba-f9db02909cd0" />
### Cài đặt WordPress
1. Mở trình duyệt truy cập: http://192.168.126.131:8090
2. Chọn ngôn ngữ -> Tiếp theo
   
<img width="960" height="540" alt="4" src="https://github.com/user-attachments/assets/0d88a696-bfea-4112-b0cb-4974b6204898" />

4. Điền thông tin:
   - Site Title: Tên website của bạn
   - Username: Tên user admin
   - Password: Tuỳ ý 
   - Email: Email của bạn
   - 
<img width="960" height="540" alt="6" src="https://github.com/user-attachments/assets/7970aa2a-9156-4ff5-9f17-3404fc80d4d9" />

5. Nhấp Install WordPress
6. Đăng nhập vào WordPress với user vừa tạo
   
<img width="960" height="538" alt="7" src="https://github.com/user-attachments/assets/fb833dec-d0d6-4263-ad3e-4c9a4041ec2d" />

 WordPress đã sẵn sàng
 
 <img width="1920" height="972" alt="image" src="https://github.com/user-attachments/assets/cbd22436-a9d1-49d0-bfa6-8b558c626030" />

### Tạo 2 bài viết
Bài viết 1: Giới thiệu bản thân
1. Đăng nhập  WordPress
2. Dashboard -> Posts -> Add New

<img width="1913" height="987" alt="image" src="https://github.com/user-attachments/assets/432cac37-1d77-4068-b8c0-a9d5840ea381" />

3. Tiêu đề: Giới Thiệu Bản Thân
4. Nội dung:
- Thông tin cá nhân (Họ tên, Ngày sinh, MSSV, ...)
- Sở thích, mục tiêu
- Kỹ năng
- Thêm ảnh của bạn (Upload image)
- Thêm video (YouTube embed hoặc upload)
- Thêm audio (nếu có)
- Nhấp Publish

5. Nhấp Publish

  
