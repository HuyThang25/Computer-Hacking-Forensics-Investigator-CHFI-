Hệ thống tệp (file system) là một bộ sưu tập có cấu trúc của các tệp/tiện ích trên một phân vùng hoặc đĩa, và nó cho phép máy tính biết vị trí bắt đầu và kết thúc của một tệp. Phần này trình bày về các loại hệ thống tệp khác nhau có sẵn trên các hệ điều hành Windows, Linux và Mac OS.

## Windows File Systems

Hệ điều hành Windows sử dụng các hệ thống tệp như FAT, FAT32, NTFS, v.v. Hệ thống tệp NTFS lưu trữ siêu dữ liệu của các tệp tin và thư mục trong một tệp hệ thống gọi là Bảng Tệp Tin Chính (MFT). Kiểm tra tệp $MFT cung cấp thông tin như thời gian MAC, tên tệp tin, vị trí tệp tin, v.v., điều này rất quan trọng trong việc pháp y. Những nhà điều tra pháp y cũng cần có kiến thức về cấp phát và xóa tệp tin để giúp khôi phục dữ liệu bị mất trong quá trình điều tra.

### File Allocation Table (FAT)

Hệ thống tệp File Allocation Table (FAT), được thiết kế vào năm 1976, là một hệ thống tệp cho nhiều hệ điều hành như DOS, Windows và OpenDOS. Được thiết kế cho các ổ cứng nhỏ và cấu trúc thư mục đơn giản, hệ thống tệp FAT được đặt theo cách nó tổ chức các thư mục và bảng phân bổ tệp tin, nơi lưu trữ tất cả các tệp tin và nằm ở đầu ổ đĩa.

FAT tạo ra hai bản sao của bảng phân bổ tệp tin để bảo vệ ổ đĩa khỏi hỏng hóc. Bảng phân bổ tệp tin và thư mục gốc được lưu trữ ở một vị trí cố định. Ổ định dạng bằng hệ thống tệp FAT tạo thành một cụm (cluster), và kích thước của ổ đĩa định dạng xác định kích thước cụm.

Hệ thống sử dụng số cụm cho hệ thống tệp FAT với 16 bit, và số cụm này là lũy thừa của hai. Các thiết bị triển khai hệ thống FAT bao gồm bộ nhớ flash, máy ảnh kỹ thuật số và các thiết bị di động khác. Hầu hết các hệ điều hành được cài đặt trên máy tính cá nhân đều triển khai hệ thống tệp FAT.

### FAT File System Layout

Hệ thống tập tin FAT32 điển hình bao gồm các thành phần sau đây:

- Reserved area (Khu vực dành riêng) 

  Số liệu dành riêng đầu tiên là bản ghi khởi động ổ đĩa (VBR), bao gồm Khối Tham số BIOS (BPB) chứa thông tin cơ bản về hệ thống tập tin, như loại hệ thống tập tin và các con trỏ đến vị trí của các phần khác cũng như mã khởi động của hệ điều hành.

- FAT area (Khu vực FAT)

  Khu vực này chứa hai bản sao (có thể thay đổi) của bảng phân bổ tập tin (FAT) để giúp hệ thống kiểm tra các vị trí trống hoặc không hoạt động. Khu vực này chứa thông tin chi tiết về các nhóm và nội dung của chúng, bao gồm các tập tin và thư mục. Các bản sao phụ trong hệ thống tập tin này được đồng bộ hoàn hảo với quá trình ghi và đọc, và chúng sẽ thay thế bảng FAT chính hoặc bản sao đầu tiên khi có vấn đề hoặc hỏng hóc.

- Data area (Khu vực dữ liệu)

  Khu vực này, chiếm phần lớn của một phân vùng, lưu trữ dữ liệu thực tế của tập tin và thư mục. Hệ thống tập tin FAT điền vào các phần không sử dụng hoặc không gian trống bằng một ước lượng nguồn lực 0xF6 dựa trên Bảng Tham số Ổ đĩa (DPT) của INT 1Eh. FAT hỗ trợ thuộc tính chỉ đọc, ẩn, hệ thống và lưu trữ.

### FAT Partition Boot Sector

Boot Sector (sector khởi động) là sector đầu tiên (512 byte) của một hệ thống tập tin FAT. Boot sector của phân vùng FAT chứa dữ liệu được sử dụng bởi hệ thống tập tin để truy cập vào phân vùng hoặc ổ đĩa. Boot sector của phân vùng bao gồm dữ liệu mà hệ thống tập tin sử dụng để truy cập vào phân vùng. Trên các máy tính dựa trên x86, MBR (Master Boot Record - Bản ghi khởi động chính) sử dụng boot sector của phân vùng hệ thống để tải các tệp tin phân vùng hệ điều hành.

Trong UNIX, boot sector của phân vùng được gọi là superblock (siêu khối) và chứa một số thông tin chung.

Dưới đây là một ví dụ về boot sector của phân vùng FAT:

```0000000 eb 3f 90 49 42 4d 20 20 33 2e 33 00 02 01 01 00 0000020 02 e0 00 40 0b f0 09 00 12 00 02 00 00 00 00 00 0000040 00 00 00 00 00 00 00 00 00 00 70 00 ffff 49 42 0000060 4d 42 49 4f 20 20 43 4f 4d 00 50 00 00 08 00 18...```

Các số gồm 2 byte được lưu trữ theo thứ tự little endian.

### FAT Foler Stucture

Hệ thống tập tin FAT có một tập hợp các mục thư có độ dài 32 byte cho mỗi thư mục.

Các mục thư trong hệ thống FAT được cấu thành như sau:

- Tên (tám ký tự cộng ba ký tự)
- Byte thuộc tính (8 bit)
- Thời gian tạo (24 bit)
- Ngày tạo (16 bit)
- Ngày truy cập cuối cùng (16 bit)
- Thời gian sửa đổi lần cuối (16 bit)
- Ngày sửa đổi lần cuối (16 bit)
- Số nhóm bắt đầu trong bảng phân bổ tập tin (16 bit)
- Kích thước tập tin (32 bit)

Tất cả các hệ điều hành hỗ trợ hệ thống tập tin FAT đều sử dụng thông tin có trong thư mục FAT.

### Directory Entries and Cluster Chains (Mục thư mục và chuỗi các nhóm)

Mục thư mục là một cấu trúc dữ liệu (32 byte) được cấp phát cho mỗi tập tin và thư mục. Hệ điều hành sử dụng mục thư mục để lưu trữ các siêu dữ liệu bổ sung như mật khẩu tập tin, quyền truy cập, ID chủ sở hữu và dữ liệu xóa tập tin, cũng như các thuộc tính, kích thước, nhóm bắt đầu, ngày và giờ.

Hệ thống tập tin chia khu vực dữ liệu của ổ đĩa thành các nhóm có kích thước giống nhau, và kích thước nhóm phụ thuộc vào loại hệ thống tập tin FAT được sử dụng và kích thước của phân vùng. Khi người dùng lưu trữ dữ liệu, một tập tin có thể chiếm nhiều hơn một nhóm tùy thuộc vào kích thước của nó. Do đó, một chuỗi các nhóm này đại diện cho một tập tin.

- Mục thư mục là một cấu trúc dữ liệu (32 byte) được cấp phát cho mỗi tập tin và thư mục.
- Nó chứa thông tin về tập tin như các thuộc tính, kích thước, nhóm bắt đầu và ngày giờ.

### Filenames on FAT Volumes

Trên các ổ đĩa FAT, khi người dùng tạo ra một tập tin với tên dài, hệ thống dựa trên Windows sẽ cấp phát một tên gồm tám ký tự cộng ba ký tự cho tập tin đó và tạo ra một hoặc nhiều mục thư mục phụ. Các mục thư mục này lưu trữ một phần tương ứng của tên dài tập tin theo định dạng Unicode. Windows sắp xếp các bit thuộc tính của mục thư mục, chẳng hạn như thuộc tính đĩa, chỉ đọc, hệ thống và ẩn, để đại diện cho các phần của tên tập tin.






