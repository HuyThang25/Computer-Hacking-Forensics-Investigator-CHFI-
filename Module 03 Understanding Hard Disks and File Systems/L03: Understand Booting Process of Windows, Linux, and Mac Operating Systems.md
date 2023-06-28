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

### Quá trình khởi động UEFI-GPT trên Windows:

Trình quản lý khởi động EFI (EFI boot manager) điều khiển quá trình khởi động UEFI. Nó bắt đầu bằng việc khởi tạo firmware của nền tảng; trình quản lý khởi động tải các trình điều khiển UEFI và các ứng dụng UEFI (bao gồm các trình khởi động hệ điều hành UEFI) để khởi tạo các chức năng của nền tảng. Hệ thống tải trình khởi động hệ điều hành vào giai đoạn cuối cùng, sau đó hệ điều hành bắt đầu khởi động. Khi hệ điều hành nhận được quyền điều khiển, nó dừng dịch vụ khởi động UEFI.

Quá trình khởi động UEFI có năm giai đoạn, mỗi giai đoạn có vai trò riêng của nó.

- Giai đoạn bảo mật (Security phase): Giai đoạn bảo mật hoặc SEC của EFI bao gồm mã khởi tạo được hệ thống thực thi sau khi bật nguồn cho hệ thống EFI. Nó quản lý các sự kiện đặt lại nền tảng và thiết lập hệ thống để tìm, xác thực, cài đặt và chạy các mô-đun khởi tạo trước EFI (PEI).

- Giai đoạn khởi tạo trước EFI (Pre-EFI initialization phase): Giai đoạn PEI khởi tạo CPU, bộ nhớ lưu trữ và ổ đĩa khởi động (BFV). Nó xác định và thực thi các mô-đun khởi tạo trước (PEIMs) có trong BFV để khởi tạo tất cả các phần cứng được tìm thấy trong hệ thống. Cuối cùng, nó tạo một danh sách Block Hand-Off (HOBL) chứa tất cả các tài nguyên và mô tả giao diện tìm thấy và chuyển nó cho giai đoạn tiếp theo, tức là giai đoạn DXE.

- Giai đoạn môi trường thực thi trình điều khiển (Driver Execution Environment phase): Hầu hết quá trình khởi động xảy ra trong giai đoạn này. Sử dụng HOBL, môi trường thực thi trình điều khiển (DXE) khởi tạo toàn bộ bộ nhớ vật lý của hệ thống, các tài nguyên I/O và I/O được ánh xạ vào bộ nhớ (MMIO) và sau đó bắt đầu gửi các trình điều khiển DXE có trong các khối lưu trữ firmware hệ thống (được đưa ra trong HOBL). Nhân DXE tạo ra một tập hợp các dịch vụ khởi động EFI (EFI boot services) và dịch vụ thời gian chạy EFI (EFI runtime services). Các dịch vụ khởi động EFI cấp phát bộ nhớ và tải các hình ảnh thực thi. Các dịch vụ thời gian chạy EFI chuyển đổi địa chỉ bộ nhớ từ vật lý sang ảo, chuyển giao chúng cho kernel và đặt lại CPU cho mã chạy trong môi trường EFI hoặc trong hạt nhân hệ điều hành sau khi CPU tiếp quản quyền điều khiển của hệ thống.

- Giai đoạn Lựa chọn thiết bị khởi động (Boot Device Selection phase): Trong giai đoạn này, Boot Device Selection (BDS) dịch và lựa chọn dữ liệu cấu hình khởi động và chọn chính sách khởi động để thực thi sau đó. Giai đoạn này làm việc với DXE để kiểm tra xem các trình điều khiển thiết bị có yêu cầu xác minh chữ ký hay không. Hệ thống tải mã khởi động MBR vào bộ nhớ cho khởi động BIOS cổ điển hoặc tải chương trình khởi động từ phân vùng EFI cho khởi động UEFI. Nó cũng cung cấp tùy chọn cho người dùng chọn shell EFI hoặc ứng dụng UEFI như một thiết bị khởi động từ menu thiết lập.

- Giai đoạn Thời gian chạy (Runtime phase): Ở giai đoạn này, hệ thống xóa chương trình UEFI khỏi bộ nhớ và chuyển giao nó cho hệ điều hành. Trong quá trình cập nhật UEFI BIOS, hệ điều hành gọi dịch vụ thời gian chạy sử dụng một phần nhỏ bộ nhớ.

## Xác định Bảng phân vùng GUID (GPT)

Một tiêu đề Bảng phân vùng GUID (GPT) giúp người điều tra phân tích cấu trúc đĩa với các chi tiết như vị trí khu vực phân vùng cũng như bảng phân vùng và các bản sao sao lưu của nó. Người điều tra có thể sử dụng các cmdlet được mô tả dưới đây trong Windows PowerShell để xác định sự có mặt của GPT.

### Get-GPT

Lệnh Get-GPT giúp người điều tra phân tích cấu trúc dữ liệu GPT của ổ cứng. Nó yêu cầu sử dụng tham số -path, nhận giá trị không gian thiết bị Win32 (ví dụ: \.\PHYSICALDRIVE1) cho thiết bị mà từ đó nó sẽ phân tích cú pháp GPT.
Trong trường hợp người điều tra sử dụng cmdlet Get-GPT trên một đĩa được định dạng với MBR, một thông báo lỗi sẽ hiển thị, yêu cầu người dùng chạy cmdlet Get-MBR thay thế.

### Phương pháp thay thế:

Mở ứng dụng "Computer Management" và nhấp chuột phải vào "Disk Management" trên thanh bên trái. Chuột phải vào ổ đĩa chính (ở đây là Disk 0) và sau đó nhấp chuột phải vào Properties.

Trong cửa sổ Tính năng Thiết bị, nhấp vào tab "Volumes" để xem kiểu phân vùng.

- Get-BootSector: Lệnh Get-BootSector có thể giúp người điều tra phân tích GPT của cả hai loại ổ cứng bao gồm cả định dạng UEFI và MBR. Lệnh này hoạt động như một sự thay thế cho Get-MBR và Get-GPT. Get-BootSector phân tích từng sector đầu tiên của ổ cứng, xác định loại định dạng được sử dụng và sau đó phân tích cú pháp GPT.
- Get-BootSector chạy trên một ổ đĩa được định dạng bằng sơ đồ phân vùng GPT:
- Get-BootSector chạy trên một ổ đĩa được định dạng bằng sơ đồ phân vùng MBR:
- Get-PartitionTable: Cmdlet này phân tích bảng phân vùng GUID để tìm kiểu chính xác của sector khởi động (MBR hoặc GPT) và hiển thị đối tượng phân vùng.


