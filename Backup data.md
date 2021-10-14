Backup dữ liệu
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
