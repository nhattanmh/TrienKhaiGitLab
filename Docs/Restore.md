 # Restore file backup database
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

 # Restore file cấu hình
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

