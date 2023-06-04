Phần này sẽ thảo luận về quá trình khởi động của Windows, bao gồm BIOS-MBR và UEFI-GPT, cách xác định sự có mặt của lược đồ phân vùng MBR hoặc GPT trên ổ đĩa; ngoài ra, sẽ giới thiệu các sơ đồ quy trình khởi động của Linux và macOS.

## Essential Windows System Files

Sau khi cài đặt hệ điều hành, chương trình cài đặt sẽ tạo ra các thư mục và các tệp tin cần thiết trên ổ đĩa hệ thống.

## Windows Boot Process: BIOS-MBR Method

Windows XP, Vista và 7 khởi động và bắt đầu sử dụng phương pháp truyền thống BIOS-MBR, trong khi Windows 8 và các phiên bản sau đó có thể sử dụng cả phương pháp BIOS-MBR truyền thống hoặc phương pháp UEFI-GPT mới hơn tùy thuộc vào sự lựa chọn của người dùng.


Dưới đây là quy trình chi tiết xảy ra trong hệ thống khi nó được bật.

1. Khi người dùng bật hệ thống, CPU gửi tín hiệu Power Good tới bo mạch chủ và kiểm tra firmware BIOS của máy tính.
2. BIOS bắt đầu một bài kiểm tra tự khởi động (POST), kiểm tra xem tất cả phần cứng cần thiết cho khởi động hệ thống có sẵn và tải tất cả cài đặt firmware từ bộ nhớ không bay hơi vào bo mạch chủ.
3. Nếu POST thành công, các bộ chuyển đổi bổ sung thực hiện kiểm tra tự khởi động để tích hợp với hệ thống.
4. Quá trình khởi động trước hoàn tất với POST, phát hiện ổ đĩa khởi động hệ thống hợp lệ.
5. Sau POST, firmware của máy tính quét ổ đĩa khởi động và tải master boot record (MBR), nơi tìm kiếm thông tin khởi động cơ bản trong Boot Configuration Data (BCD).
6. MBR kích hoạt Bootmgr.exe, nơi tìm Windows loader (Winload.exe) trên phân vùng khởi động Windows và kích hoạt Winload.exe.
7. Windows loader tải kernel OS ntoskrnl.exe.
8. Khi Kernel bắt đầu chạy, Windows loader tải hal.dll, các trình điều khiển thiết bị lớp khởi động được đánh dấu là BOOT_START và hive registry SYSTEM vào bộ nhớ.
9. Kernel chuyển quyền kiểm soát quá trình khởi động cho quy trình Quản lý Phiên (SMSS.exe), nơi tải tất cả các hive registry và trình điều khiển cần thiết khác để cấu hình môi trường chạy Win32 subsystem.
10. Quy trình Quản lý Phiên kích hoạt Winlogon.exe, hiển thị màn hình đăng nhập người dùng để xác thực người dùng.
11. Quy trình Quản lý Phiên khởi động Quản lý Điều khiển Dịch vụ, khởi động tất cả các dịch vụ, các trình điều khiển thiết bị không thiết yếu khác, hệ thống bảo mật LSASS.EXE và các kịch bản Chính sách Nhóm.
12. Khi người dùng đăng nhập, Windows tạo một phiên cho người dùng.
13. Quản lý Điều khiển Dịch vụ khởi động explorer.exe và khởi động quy trình Desktop Window Manager (DMW), khởi tạo môi trường desktop cho người dùng.
