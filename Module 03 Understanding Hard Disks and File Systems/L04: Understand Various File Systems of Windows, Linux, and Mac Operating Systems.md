Hệ thống tệp (file system) là một bộ sưu tập có cấu trúc của các tệp/tiện ích trên một phân vùng hoặc đĩa, và nó cho phép máy tính biết vị trí bắt đầu và kết thúc của một tệp. Phần này trình bày về các loại hệ thống tệp khác nhau có sẵn trên các hệ điều hành Windows, Linux và Mac OS.

## Windows File Systems

Hệ điều hành Windows sử dụng các hệ thống tệp như FAT, FAT32, NTFS, v.v. Hệ thống tệp NTFS lưu trữ siêu dữ liệu của các tệp tin và thư mục trong một tệp hệ thống gọi là Bảng Tệp Tin Chính (MFT). Kiểm tra tệp $MFT cung cấp thông tin như thời gian MAC, tên tệp tin, vị trí tệp tin, v.v., điều này rất quan trọng trong việc pháp y. Những nhà điều tra pháp y cũng cần có kiến thức về cấp phát và xóa tệp tin để giúp khôi phục dữ liệu bị mất trong quá trình điều tra.

### File Allocation Table (FAT)

Hệ thống tệp File Allocation Table (FAT), được thiết kế vào năm 1976, là một hệ thống tệp cho nhiều hệ điều hành như DOS, Windows và OpenDOS. Được thiết kế cho các ổ cứng nhỏ và cấu trúc thư mục đơn giản, hệ thống tệp FAT được đặt theo cách nó tổ chức các thư mục và bảng phân bổ tệp tin, nơi lưu trữ tất cả các tệp tin và nằm ở đầu ổ đĩa.

FAT tạo ra hai bản sao của bảng phân bổ tệp tin để bảo vệ ổ đĩa khỏi hỏng hóc. Bảng phân bổ tệp tin và thư mục gốc được lưu trữ ở một vị trí cố định. Ổ định dạng bằng hệ thống tệp FAT tạo thành một cụm (cluster), và kích thước của ổ đĩa định dạng xác định kích thước cụm.

Hệ thống sử dụng số cụm cho hệ thống tệp FAT với 16 bit, và số cụm này là lũy thừa của hai. Các thiết bị triển khai hệ thống FAT bao gồm bộ nhớ flash, máy ảnh kỹ thuật số và các thiết bị di động khác. Hầu hết các hệ điều hành được cài đặt trên máy tính cá nhân đều triển khai hệ thống tệp FAT.

