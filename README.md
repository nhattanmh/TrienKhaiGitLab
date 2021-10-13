# 1. GitLab là gì?
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
- sudo apt-get install -y postfix

![image](https://user-images.githubusercontent.com/59860781/136920377-cac4a769-fa87-4660-aa36-1e1666be85cc.png)
- Chọn Internet Site => OK
![image](https://user-images.githubusercontent.com/59860781/136916941-caa49be9-8033-497e-acee-c7c6c34210c2.png)
![image](https://user-images.githubusercontent.com/59860781/136918757-47b819b6-4fd3-4be1-b1bf-a44546f606db.png)
##### Bước 3: Thêm Gitlab Repository
 + Có 2 phiên bản Gitlab Repository
 - Phiên bản Community Editor (Miễn phí)
 - curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
![image](https://user-images.githubusercontent.com/59860781/136919756-a396708e-0110-4ee8-ba58-ff6cb0081b0f.png)
 - Phiên bản thương mại Enterprise Editor (Bản dùng thử 14 ngày)
 - curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | sudo bash
 ##### Bước 4: Cài đặt GitLab
 - sudo EXTERNAL_URL="https://gitlab.nhattanmh.com" apt-get install gitlab-ce
   ![image](https://user-images.githubusercontent.com/59860781/136921368-424c8d40-99ac-4f33-8f63-cb57ceacccb2.png)
 -  Quá trình cài đặt sẽ diễn ra tự động. Sau khi hoàn thành sẽ được kết quả như hình.
    ![image](https://user-images.githubusercontent.com/59860781/136937082-efea1f16-71a6-4a0f-af72-a9d405e30060.png)
 ##### Bước 5: Thiết lập mật khẩu cho tài khoản root.
- Tài khoản mặc định của GitLab là root. Sau khi cài đặt xong GitLab, chúng ta truy cập đường dẫn ip của máy, nó sẽ redirect chúng ta tới trang thiết lập mật khẩu cho tài khoản root.
 - Hoặc reset pwd bằng command line:
  Sudo gitlab-rake “gitlab:password:reset”
  ![image](https://user-images.githubusercontent.com/59860781/136922127-99c5c3b7-8653-4bc1-9834-e4298b156ecc.png)
 #### Tiến hành truy cập vào GitLab bằng địa chỉ IP 
![image](https://user-images.githubusercontent.com/59860781/136922426-a9238d2c-01e4-49f5-a301-c8233bdc0e4a.png)
- Sau khi đăng nhập thành công ta sẽ có giao diện quản lý như hình
![image](https://user-images.githubusercontent.com/59860781/136922490-5ac59503-9005-4bb8-bf90-ef2dd07ad2bf.png)

  # 2. Backup dữ liệu
- Back-up hay (sao lưu) dữ liệu là hình thức bạn copy lại toàn bộ đoạn dữ liệu trong máy tính, máy chủ, server… hay bất cứ thiết bị nào có khả năng nhớ và lưu trữ của bạn và lưu trữ nó ở một hoặc nhiều thiết bị có chức năng lưu trữ khác để làm dữ liệu dự phòng. Khi thiết bị nhớ chính của chúng ta bị mất dữ liệu trong khi hoạt động do hư hỏng, hacker, sập nguồn…. Chúng ta vẫn còn dữ liệu để restore lại, hạn chế thiệt hại và mất mát về nguồn tài nguyên dữ liệu này.
### Back up dữ liệu và database
Bước 1: Tạo một folder để lưu trữ file backup
  - mkdir backup
  
  ![image](https://user-images.githubusercontent.com/59860781/137115796-1bb87a26-5090-4433-93aa-7bea62a21e3f.png)
  
  Bước 2: Gitlab cung cấp lệnh để backup dữ liệu một cách nhanh chóng
  - gitlab-backup create
 
![image](https://user-images.githubusercontent.com/59860781/137116845-d6052e6c-5307-4f04-8517-7d6087310a2d.png)

Sau khi lệnh chạy xong, hệ thống sẽ tạo ra một file backups trong thư mục /var/opt/gitlab/backups.

![image](https://user-images.githubusercontent.com/59860781/137116926-b02696d9-15d1-4bc7-99f1-9288664bfe78.png)
Bước 3: Di chuyển file backups vào thư mục backup tạm thời
- mv /backups ~nhattanmh/backup

![image](https://user-images.githubusercontent.com/59860781/137117234-cbe8407e-8cfe-42bf-b3b3-a175f6537e45.png)
### Back up file cấu hình
Bước 1: Tạo một folder để lưu trữ file backup
- mkdir backup

![image](https://user-images.githubusercontent.com/59860781/137115796-1bb87a26-5090-4433-93aa-7bea62a21e3f.png)
Bước 2: Sao chép toàn bộ thư mục /etc/gitlab vào thư mục backup
- sudo cp -r /etc/gitlab/ ~nhattanmh/backup/

![image](https://user-images.githubusercontent.com/59860781/137118430-6020e8c1-6d84-485b-a479-12bd0f3f5366.png)
### Đóng gói thư mục backup tạm với toàn bộ dữ liệu backup
- tar -cvzf backup.tar.gz ~nhattanmh

![image](https://user-images.githubusercontent.com/59860781/137118939-49756e63-10d9-4e35-95dc-4216ec42bce9.png)

  # 3. Restore file backup database
Khôi phục dữ liệu sẽ thực hiện ngược lại với quá trình backup.
Bước 1: Copy file backup database vào trong thư mục backup của máy chủ Gitlab.
- sudo cp backups/1634121124_2021_10_13_14.3.2_gitlab_backup.tar /var/opt/gitlab/backups/

![image](https://user-images.githubusercontent.com/59860781/137121112-bf49906c-23c5-43e8-a3c9-86ae06dda283.png)

Bước 2: Gán quyền owner file backup cho user git.
- sudo chown git.git /var/opt/gitlab/backups/1634121124_2021_10_13_14.3.2_gitlab_backup.tar 

![image](https://user-images.githubusercontent.com/59860781/137121442-7da6b6ee-ba6d-4019-be0f-b8ebf9c09b5a.png)

Bước 3: Dừng các dịch vụ của Gitlab đang kết nối về database.

![image](https://user-images.githubusercontent.com/59860781/137121842-460246cf-a0ff-4f61-a602-07f6014a693a.png)

Bước 4: Chạy lệnh restore file backup với nhãn thời gian và phiên bản của file.
- sudo gitlab-backup restore 1634121124_2021_10_13_14.3.2

 # 3. Restore file cấu hình
Bước 1: Chuyển thư mục /etc/gitlab hiện tại thành bản cũ.
- sudo mv /etc/gitlab /etc/gitlab_old

![image](https://user-images.githubusercontent.com/59860781/137123683-883d8a0a-ebc9-4265-8fda-43315bb25ddf.png)

Bước 2: Copy thư mục gitlab trong file backup vào thư mục /etc/trên server hiện tại.
- sudo cp -r gitlab /etc/

![image](https://user-images.githubusercontent.com/59860781/137123989-8fe05558-9881-478a-a73e-53dfe82a2580.png)

Kiểm tra lại thư mục backup gitlab vừa copy

![image](https://user-images.githubusercontent.com/59860781/137124095-04e25490-059a-43ab-af6a-55333e4cc646.png)

# Reconfigure hệ thống
Cuối cùng là thực hiện apply lại các cấu hình backup cho hệ thống.
- gitlab-ctl reconfigure
- gitlab-ctl restart
Để kiểm tra quá trình restore diễn ra tốt, dùng lệnh:
- gitlab-rake gitlab:check SANITIZE=true

![image](https://user-images.githubusercontent.com/59860781/137124580-4119b11b-ad41-4206-9cbd-2e42e12aa169.png)


