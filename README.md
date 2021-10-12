# GitLab là gì?
GitLab là một trang web dựa trên DevOps mã nguồn mở và là một phần mềm có chức năng và nhiệm vụ quản lý phiên bản mã nguồn, cung cấp một trình quản lý Git-repository. Trình quản lý này có các tiện ích như wiki, theo dõi sự cố và tích hợp liên tục. Bên cạnh đó là khả năng triển khai các tính năng pipeline và sử dụng license mã nguồn mở được phát triển bởi GitLab Inc.
### Yêu cầu phần cứng tối thiểu cho 100 user
  1 core CPU
  4GB RAM + 4GB swap
  Dung lượng ổ cứng tùy thuộc vào yêu cầu sử dụng
  Yêu cầu phần cứng khuyến nghị cho 100 user
  2 core CPU
  8GB RAM
  Dung lượng ổ cứng tùy thuộc vào yêu cầu sử dụng
### Yêu cầu phần mềm
  PostgreSQL Database
  Redis: Chưa thông tin phiên làm việc của User và hàng đợi các Task chạy ngầm
  Sidekiq: Xử lý các job chạy ngầm và xử lý đa luồng (multithreaded process)
  Prometheus: Sử dụng để giám sát hoạt động
## Hướng dẫn cài đặt GitLab trên Ubuntu
##### Bước 1: Update và cài đặt các thư viện cần thiết
- sudo apt-get update
- sudo apt-get install -y curl openssh-server ca-certificates
![image](https://user-images.githubusercontent.com/59860781/136916051-bd10d39b-eaa5-4375-8494-38b3a01ed61d.png)
##### Bước 2: Cài đặt Postfix Mail Server
Sử dụng Postfix để gửi notification email, tuy nhiên có thể bỏ qua bước này nếu sử dụng 1 SMTP Mail Server khác như Gmail SMTP chẳng hạn.
- sudo apt-get install -y
![image](https://user-images.githubusercontent.com/59860781/136916617-c63d21ac-c4e3-4657-9469-91d6facf2eec.png)
- Chọn Internet Site => OK
![image](https://user-images.githubusercontent.com/59860781/136916941-caa49be9-8033-497e-acee-c7c6c34210c2.png)
![image](https://user-images.githubusercontent.com/59860781/136918757-47b819b6-4fd3-4be1-b1bf-a44546f606db.png)
##### Bước 3: Thêm Gitlab Repository.
 + Có 2 phiên bản Gitlab Repository
 - Phiên bản Community Editor (Miễn phí)
 - curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
![image](https://user-images.githubusercontent.com/59860781/136919756-a396708e-0110-4ee8-ba58-ff6cb0081b0f.png)
 - Phiên bản thương mại Enterprise Editor (Dùng thử 14 ngày) thì thay bằng câu lệnh bên dưới
x
x

