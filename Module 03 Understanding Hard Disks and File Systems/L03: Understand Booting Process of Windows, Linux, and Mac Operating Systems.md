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
   
### Phân tích Tiêu đề và Mục nhập GPT

Hầu hết các hệ điều hành hỗ trợ truy cập đĩa GPT đều có một công cụ phân vùng cơ bản, hiển thị chi tiết về bảng phân vùng GPT. Trong Windows, các công cụ như công cụ DiskPart hiển thị thông tin về phân vùng, trong khi hệ thống Mac sử dụng tiện ích Đĩa OS X và Linux sử dụng công cụ GNU Parted.

Lệnh mmls trong The Sleuth Kit có thể giúp người điều tra xem cấu trúc chi tiết của các phân vùng trên đĩa GPT, cùng với thông tin về MBR. Những người điều tra cũng có thể thu thập thông tin về tiêu đề GPT và các mục nhập phân vùng thông qua việc phân tích thủ công của ổ đĩa bằng cách sử dụng tính toán hex hoặc một công cụ chỉnh sửa gọi là hex editor.

## Các Hiện vật GPT

### Các phân vùng GUID bị xóa và ghi đè

#### Trường hợp 1: 

Trên ổ cứng, quá trình chuyển đổi hoặc phân vùng từ MBR sang GPT thông thường ghi đè lên sector số không bằng một MBR bảo vệ, xóa tất cả thông tin về bảng phân vùng cũ. Người điều tra nên tuân theo các phương pháp pháp y chuẩn để tìm kiếm các hệ thống tệp để khôi phục dữ liệu về các phân vùng trước đó được phân vùng theo MBR.

#### Trường hợp 2: 

Khi xảy ra quá trình chuyển đổi hoặc phân vùng từ GPT sang MBR, tiêu đề GPT và bảng vẫn có thể được giữ nguyên dựa trên công cụ được sử dụng. Người điều tra có thể dễ dàng khôi phục hoặc phân tích dữ liệu của các phân vùng đĩa như vậy.

Việc triển khai các công cụ xóa phân vùng chung để xóa một phân vùng trên đĩa GPT có thể chỉ xóa MBR bảo vệ, người điều tra có thể dễ dàng tái tạo bằng cách đơn giản khôi phục lại đĩa.

Theo quy định của UEFI, nếu tất cả các trường trong mục nhập phân vùng có giá trị bằng không, thì mục nhập đó không được sử dụng. Trong trường hợp này, việc khôi phục dữ liệu từ các mục nhập phân vùng GUID bị xóa không khả thi.

#### GUID

- Sơ đồ GPT cung cấp các GUID có giá trị điều tra vì chúng là duy nhất và có thể chứa thông tin về toàn bộ đĩa và từng phân vùng bên trong chúng.

- GUID có chứa thông tin xác định duy nhất cho cả ổ đĩa và từng phân vùng riêng lẻ.

- Người điều tra có thể sử dụng các công cụ như universally unique identifier (UUID) để giải mã các phiên bản khác nhau của GUID/UUID.

#### Thông tin ẩn trên các đĩa GPT

Kẻ xâm nhập có thể ẩn dữ liệu trên các đĩa GPT tương tự như cách họ làm trên các đĩa MBR thông thường bằng cách sử dụng các sơ đồ phân vùng đĩa linh hoạt và mở rộng. Các vị trí trên các đĩa GPT mà dữ liệu có thể bị ẩn đi bao gồm khoảng trống giữa các phân vùng, không gian chưa được phân vùng về cuối đĩa, tiêu đề GPT và các khu vực dành riêng.

Các hiện vật khác có thể bao gồm tiêu đề GPT bị chỉnh sửa tạo ra các vị trí để ẩn dữ liệu, các LBA bắt đầu và kết thúc bị đặt sai vị trí, cũng như các khu vực có các thẻ dành riêng. Các phương pháp và công cụ pháp y hiện tại để thực hiện phân tích GPT không đạt yêu cầu.

### Quá trình khởi động Macintosh
Dưới đây là các bước trong quá trình khởi động Macintosh:

- Quá trình khởi động Macintosh bắt đầu bằng việc kích hoạt BootROM, nơi khởi tạo phần cứng hệ thống và chọn một hệ điều hành để chạy.
- Sau khi hệ thống Macintosh được bật, BootROM thực hiện POST để kiểm tra một số giao diện phần cứng cần thiết để khởi động.
- Trên các máy tính Macintosh dựa trên PowerPC, Open Firmware khởi tạo các giao diện phần cứng còn lại.
- Trên các máy tính Macintosh dựa trên Intel, EFI khởi tạo các giao diện phần cứng còn lại.
- Sau khi khởi tạo các giao diện phần cứng, hệ thống chọn hệ điều hành.
- Nếu hệ thống chứa nhiều hệ điều hành, nó cho phép người dùng chọn một hệ điều hành cụ thể bằng cách giữ phím Option.
- Sau khi hoàn tất quá trình BootROM, quyền điều khiển chuyển sang trình tải khởi động BootX (PowerPC) hoặc boot.efi (Intel), nằm trong thư mục /System/Library/CoreServices.
- Trình tải khởi động tải một phiên bản đã liên kết trước của kernel, nằm tại /System/Library/Caches/com.apple.kernelcaches.
- Nếu kernel đã liên kết trước bị thiếu, trình tải khởi động cố gắng tải tệp cache mkext, chứa một tập hợp các trình điều khiển thiết bị.
- Nếu tệp cache mkext cũng bị thiếu, trình tải khởi động tìm kiếm các trình điều khiển trong thư mục /System/Library/Extensions.
- Sau khi đã tải các trình điều khiển cần thiết, trình tải khởi động bắt đầu khởi tạo kernel, cấu trúc dữ liệu Mach và BSD, cũng như I/O kit.
- I/O kit sử dụng cây thiết bị để liên kết các trình điều khiển đã tải với kernel.
- Quá trình launchd, đã thay thế quá trình mach_init, chạy các mục khởi động và chuẩn bị hệ thống cho người dùng.

### Quá trình khởi động Linux

Quá trình khởi động Linux bắt đầu với BIOS, nơi tìm kiếm các thiết bị hoạt động và có thể khởi động. Hệ thống khởi động Linux từ thiết bị lưu trữ chính mà trong đó MBR chứa trình tải khởi động chính.

Quá trình khởi động Linux bao gồm ba giai đoạn sau:
- Giai đoạn BIOS
- Giai đoạn trình tải khởi động (bootloader)
- Giai đoạn kernel

#### Giai đoạn BIOS

Giai đoạn đầu tiên của quá trình khởi động Linux là giai đoạn BIOS. Nó khởi tạo phần cứng hệ thống trong quá trình khởi động. BIOS lấy thông tin được lưu trữ trong chip bộ nhớ bán dẫn metal–oxide semiconductor (CMOS), một chip bộ nhớ hoạt động bằng pin trên bo mạch chủ chứa thông tin về cấu hình phần cứng của hệ thống. Trong quá trình khởi động, BIOS thực hiện POST để đảm bảo rằng tất cả các thành phần phần cứng của hệ thống hoạt động. Sau khi POST thành công, BIOS bắt đầu tìm kiếm ổ đĩa hoặc đĩa chứa hệ điều hành theo một chuỗi tiêu chuẩn. Nếu thiết bị được liệt kê đầu tiên không có sẵn hoặc không hoạt động, nó sẽ kiểm tra các thiết bị tiếp theo và tiếp tục như vậy. Một ổ đĩa chỉ có thể khởi động nếu nó có MBR trong sector đầu tiên được gọi là sector khởi động. Ổ đĩa cứng của hệ thống hoạt động như ổ đĩa khởi động chính, và ổ đĩa quang hoạt động như ổ đĩa khởi động phụ để khởi động hệ điều hành trong trường hợp ổ đĩa khởi động chính gặp sự cố.

#### Giai đoạn trình tải khởi động (bootloader)

Giai đoạn trình tải khởi động bao gồm việc tải kernel Linux và RAM disk ban đầu tùy chọn. Kernel cho phép CPU truy cập RAM và đĩa cứng. Phần mềm tiền đề thứ hai là một hình ảnh của hệ thống tệp ảo tạm thời được gọi là hình ảnh initrd hoặc initial RAMdisk. Bây giờ, hệ thống chuẩn bị triển khai hệ thống tệp gốc thực tế. Sau đó, nó phát hiện thiết bị chứa hệ thống tệp và tải các module cần thiết. Bước cuối cùng của giai đoạn trình tải khởi động là tải kernel vào bộ nhớ.

#### Giai đoạn kernel

Khi điều khiển chuyển từ giai đoạn trình tải khởi động sang giai đoạn kernel, hệ thống tệp gốc ảo được tạo ra bởi hình ảnh initrd thực thi chương trình Linuxrc. Chương trình này tạo ra hệ thống tệp thực sự cho kernel và sau đó loại bỏ hình ảnh initrd. Sau đó, kernel tìm kiếm phần cứng mới và tải bất kỳ trình điều khiển thiết bị phù hợp nào được tìm thấy. Sau đó, nó gắn kết hệ thống tệp gốc thực tế và thực hiện quá trình khởi tạo (init). Quá trình init đọc tệp "/etc/inittab" và sử dụng tệp này để tải các tiến trình hệ thống còn lại. Điều này chuẩn bị hệ thống và người dùng có thể đăng nhập và sử dụng nó. Các trình tải khởi động phổ biến cho Linux là Linux Loader (LILO) và Grand Unified Bootloader (GRUB). Những trình tải khởi động này cho phép người dùng chọn kernel hệ điều hành mà họ muốn tải trong quá trình khởi động.




