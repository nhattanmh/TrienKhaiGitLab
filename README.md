# Triển khai GitLab
GitLab là một trang web dựa trên DevOps mã nguồn mở và là một phần mềm có chức năng và nhiệm vụ quản lý phiên bản mã nguồn, cung cấp một trình quản lý Git-repository. Trình quản lý này có các tiện ích như wiki, theo dõi sự cố và tích hợp liên tục. Bên cạnh đó là khả năng triển khai các tính năng pipeline và sử dụng license mã nguồn mở được phát triển bởi GitLab Inc.
# Yêu cầu phần cứng tối thiểu cho 100 user
  1 core CPU
  4GB RAM + 4GB swap
  Dung lượng ổ cứng tùy thuộc vào yêu cầu sử dụng
  Yêu cầu phần cứng khuyến nghị cho 100 user
  2 core CPU
  8GB RAM
  Dung lượng ổ cứng tùy thuộc vào yêu cầu sử dụng
# Yêu cầu phần mềm
  PostgreSQL Database
  Redis: Chưa thông tin phiên làm việc của User và hàng đợi các Task chạy ngầm
  Sidekiq: Xử lý các job chạy ngầm và xử lý đa luồng (multithreaded process)
  Prometheus: Sử dụng để giám sát hoạt động
## Hướng dẫn cài đặt GitLab trên Ubutu
### Update và cài đặt các thư viện cần thiết
