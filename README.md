# 🚀 BT3.WordPress--Dev-App-OpenSrc

## 📖 Mô tả dự án
Dự án sử dụng Docker Compose để khởi chạy một hệ thống WordPres đầy đủ gồm:

- 🗄️ MariaDB: Hệ quản trị csdl
- 🛠️ phpMyAdmin: Công cụ quản lý database trực quan
- 🌐 WordPres: Nền tảng CMS để tạo website

---

# ⚙️ Yêu cầu hệ thống

## 📌 CÀI ĐẶT:
- Docker
- Ubuntu
- Cloudflare

## 🔍 Kiểm tra phiên bản

```bash
docker --version
```

---

# 🧩 Các bước setup

## 📁 Cấu hình file

### Nội dung file

```env
MYSQL_ROOT_PASSWORD=root123
MYSQL_DATABASE=wordpressdb
MYSQL_USER=wpuser
MYSQL_PASSWORD=wp123
WORDPRESS_PORT=8090
PHPMYADMIN_PORT=8091
```

---

## 📂 Tạo thư mục volumes

---

## 🚀 Khởi chạy Docker Compose

```bash
# Chạy tất cả services ở background
docker compose up -d
```

---

## 🛠️ Kiểm tra các services

```bash
# Xem trạng thái containers
docker compose ps

# Xem logs (nếu cần debug)
docker compose logs -f wordpress
```

---

# 🌍 Giao diện hệ thống

## 🖥️ Trang WordPress

<img width="960" height="540" alt="4" src="https://github.com/user-attachments/assets/0d88a696-bfea-4112-b0cb-4974b6204898" />

---

## 🗄️ Trang phpMyAdmin

<img width="960" height="537" alt="3" src="https://github.com/user-attachments/assets/aaff5a69-cfa1-48b2-adba-f9db02909cd0" />

---

# ⚡ Cài đặt WordPress

## 🔹 Bước 1
Mở trình duyệt truy cập:

```bash
http://192.168.126.131:8090
```

## 🔹 Bước 2
Chọn ngôn ngữ -> Tiếp theo

<img width="960" height="540" alt="4" src="https://github.com/user-attachments/assets/0d88a696-bfea-4112-b0cb-4974b6204898" />

---

## 🔹 Bước 3
Điền thông tin:

- Site Title: Tên website của bạn
- Username: Tên user admin
- Password: Tuỳ ý
- Email: Email của bạn

<img width="960" height="540" alt="6" src="https://github.com/user-attachments/assets/7970aa2a-9156-4ff5-9f17-3404fc80d4d9" />

---

## 🔹 Bước 4
Nhấp **Install WordPress**

---

## 🔹 Bước 5
Đăng nhập vào WordPress với user vừa tạo

<img width="960" height="538" alt="7" src="https://github.com/user-attachments/assets/fb833dec-d0d6-4263-ad3e-4c9a4041ec2d" />

---

# ✅ WordPress đã sẵn sàng

<img width="1920" height="972" alt="image" src="https://github.com/user-attachments/assets/cbd22436-a9d1-49d0-bfa6-8b558c626030" />

---

# 📝 Tạo 2 bài viết

# 👤 Bài viết 1: Giới thiệu bản thân

## 🔹 Bước 1
Đăng nhập WordPress

## 🔹 Bước 2
Dashboard -> Posts -> Add New

<img width="1913" height="987" alt="image" src="https://github.com/user-attachments/assets/432cac37-1d77-4068-b8c0-a9d5840ea381" />

---

## 🔹 Bước 3
Tiêu đề: **Giới Thiệu Bản Thân**

<img width="1888" height="912" alt="image" src="https://github.com/user-attachments/assets/1bb27cc5-df4c-44a8-b175-bda0cd4566d6" />

---

## 🔹 Bước 4
Nội dung:

- Thông tin cá nhân (Họ tên, Ngày sinh, MSSV, ...)
- Sở thích, mục tiêu
- Kỹ năng
- Thêm ảnh của bạn (Upload image)
- Thêm video (YouTube embed hoặc upload)
- Thêm audio (nếu có)
- Nhấp Publish

---

## 🔹 Bước 5
Nhấp Publish

---

# 🎓 Bài viết 2: Giới thiệu ngành học

<img width="1920" height="856" alt="image" src="https://github.com/user-attachments/assets/2cefb7ef-120a-4fb6-a78c-97e3f0fc6aee" />

---

# ☁️ Public Website với Cloudflare Tunnel

Thay vì cài đặt trực tiếp Cloudflare trên Ubuntu, hệ thống sẽ chạy Tunnel dưới dạng một Docker Container. Giúp:

- 🔄 Dễ backup và deploy
- 🚀 Tự khởi động cùng các service khác
- 🛠️ Dễ quản lí bằng Docker Compose
- 📦 Đồng bộ toàn hệ thống bằng Docker

---

# 🔧 Thêm Service Cloudflared

Mở file:

```yaml
Docker-compose.yml
```

Thêm đoạn sau vào phần services:

```yaml
cloudflared_wp:
    image: cloudflare/cloudflared:latest
    container_name: cloudflared_wp
    restart: always
    command: tunnel --no-autoupdate run --token eyJhIjoiZjczYjFiNjYxMjVjZWQ5NDdmYjdiZTNjNTcxMTI3YjkiLCJ0IjoiY2VjN2JkY2EtNGYwOS00Y2U0LWIyMDYtNDNhOGUwODc4NDMzIiwicyI6Ik5qVXdOek14TW1JdE1HWTJNeTAwWkdaaExXRTFOelF0WlRKbU5HSm1NVGhqTmpGbCJ9
    networks:
      - wp_net
```

---

# 🔑 Thêm Token Cloudflare

## 📌 lấy Tunnel Token Trên Cloudflare

### 🔹 Bước 1: Truy cập Cloudflare Zero Trust

- Đăng nhập Cloudflare: https://dash.cloudflare.com/
- Vào: Zezo -> Networks -> Tunnel

---

### 🔹 Bước 2: Tạo Tunnel

- Chọn: Create a Tunnel
- Đặt tên

---

### 🔹 Bước 3: Chọn Docker

- Cloudflare sẽ hiện lệnh dạng:

```bash
docker run cloudflare/cloudflared:latest tunnel --no-autoupdate run --token xxxxx
```

- Copy phần: `xxxxx`
- Đó chính là `CLOUDFLARE_TOKEN`

<img width="936" height="482" alt="8" src="https://github.com/user-attachments/assets/951f827d-32ce-4b9b-bf54-4cbf65a57385" />

---

# 🚀 Khởi động hệ thống

```bash
# Build và chạy toàn bộ container
docker compose up -d --build
```

---

# 🌍 Tạo Public Hostname

Vào:

```bash
Cloudflare Zero Trust
→ Networks
→ Tunnels
→ Chọn Tunnel
→ Public Hostname
```

Chọn:

```bash
Add a public hostname
```

---

# 🧠 Nhận xét việc sử dụng mã nguồn mở wordpress mã nguồn mở

## 1️⃣ Tính dễ sử dụng

- 🎨 Giao diện: Rất thân thiện, dùng kéo thả (Gutenberg) nên không cần giỏi code vẫn làm được trang đẹp như cậu đã làm.
- ⚡ Làm quen: Cực nhanh (mất khoảng vài tiếng để thành thạo các thao tác cơ bản).

---

## 2️⃣ Tiêu tốn tài nguyên

- 💻 RAM/CPU: Khá tốn kém. WordPress chạy PHP/MySQL nên ngốn RAM hơn web tĩnh (cần ít nhất 512MB RAM để chạy ổn).
- 💾 Disk Space: Tốn dung lượng cho mã nguồn, plugin và database phình to theo thời gian.

### 📌 Tối ưu:
Bắt buộc phải cài plugin Cache và nén ảnh để máy chủ không bị quá tải.

---

## 3️⃣ Ưu điểm

- ✅ Cài đặt nhanh
- ✅ Hỗ trợ SEO tốt
- ✅ Cộng đồng hỗ trợ đông (dễ tìm cách sửa lỗi)

---

## 4️⃣ Nhược điểm

- ⚠️ Bảo mật kém (dễ bị hack qua plugin)
- ⚠️ Tốc độ chậm nếu cài quá nhiều thứ
- ⚠️ Phụ thuộc vào bên thứ ba

---
✨ Hoàn thành hệ thống WordPress Docker + Cloudflare Tunnel
