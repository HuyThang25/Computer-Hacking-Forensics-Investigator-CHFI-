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

### FAT32

FAT32 là phiên bản của FAT thay thế cho FAT16 và có sẵn trong Windows 95 OSR 2 và Windows 98. So với FAT16, FAT32 sử dụng các nhóm nhỏ hơn với nhiều bit địa chỉ hơn để hỗ trợ ổ đĩa lớn hơn và cung cấp khả năng lưu trữ tốt hơn. Nó luôn tạo một bản sao lưu của bảng phân bổ tập tin thay vì chỉ duy trì bản sao mặc định.

Các tính năng của FAT32:
- Hiệu quả sử dụng không gian của FAT32 cao hơn khoảng 10% - 15% so với FAT16 nhờ việc sử dụng các nhóm nhỏ hơn.
- FAT32 rất mạnh mẽ vì nó có thể thay đổi vị trí của thư mục gốc và sử dụng bản sao lưu của bảng phân bổ tập tin.
- FAT32 bao gồm một bản ghi khởi động mở rộng để tích hợp bản sao lưu của các cấu trúc thông tin cơ bản.
- Tỷ lệ hỏng hóc của ổ đĩa FAT32 thấp hơn so với ổ đĩa FAT16.
- FAT32 linh hoạt hơn FAT16.
- Thư mục gốc trên ổ đĩa FAT32 là một chuỗi nhóm thông thường, do đó nó có thể được đặt ở bất kỳ đâu trên ổ đĩa.
- FAT32 không áp đặt bất kỳ hạn chế nào về số lượng mục thư mục gốc.
- FAT32 cho phép người dùng tắt việc lặp lại bảng phân bổ tập tin.
- NTFS lưu trữ thông tin về các nhóm của tập tin và dữ liệu khác trong nhóm đó
- NTFS hỗ trợ tập tin có kích thước lên đến khoảng 16 tỷ byte
- Một danh sách kiểm soát truy cập (ACL) cho phép quản trị viên máy chủ truy cập vào các tập tin cụ thể
- NTFS có tính năng nén tập tin tích hợp
- NTFS cung cấp bảo mật dữ liệu trên cả đĩa gắn ngoài và đĩa cố định

### NTF Architecture (Kiến trúc NTFS)

Khi định dạng phân vùng của hệ thống tập tin, hệ thống tạo ra Master Boot Record. Nó chứa một số mã thực thi được gọi là mã khởi động chính và thông tin về bảng phân vùng cho ổ cứng. Khi một phân vùng mới được gắn kết, Master Boot Record chạy mã thực thi khởi động chính. Trong NTFS, tất cả các tập tin được lưu trữ trong các nhóm và có các thuộc tính riêng. Các thành phần như tên, kích thước hoặc dữ liệu được lưu trữ trong một tập tin được coi là các thuộc tính. Do đó, cấu trúc nội bộ của NTFS tương tự như một cơ sở dữ liệu trong đó tất cả các tập tin được xem như các đối tượng bởi hệ điều hành.

Các thành phần của kiến trúc NTFS bao gồm:
- Ổ cứng: Nó bao gồm ít nhất một phân vùng.
- Master Boot Record: Nó chứa mã khởi động chính được hệ thống máy tính BIOS tải vào bộ nhớ; mã này được sử dụng để quét Master Boot Record để xác định bảng phân vùng và tìm ra phân vùng nào là hoạt động/có thể khởi động.
- Boot sector: Còn được gọi là volume boot record (VBR), đây là sector đầu tiên được tìm thấy trong một hệ thống tập tin NTFS, nó lưu trữ mã khởi động và thông tin khác, chẳng hạn như loại, vị trí và kích thước dữ liệu trong hệ thống tập tin NTFS.
- Ntldr.dll: Là một trình khởi động, nó truy cập vào hệ thống tập tin NTFS và tải nội dung của tệp boot.ini.
- Ntfs.sys: Đây là một trình điều khiển tập tin hệ thống máy tính cho NTFS.
- Kernel mode: Đây là chế độ xử lý cho phép mã thực thi có truy cập trực tiếp vào tất cả các thành phần của hệ thống.
- User mode: Đây là chế độ xử lý trong đó một chương trình hoặc mã thực thi chạy.

### NTFS System Files

NTFS có nhiều tệp hệ thống được lưu trữ trong thư mục gốc của một phân vùng NTFS. Những tệp này chứa siêu dữ liệu của hệ thống tập tin.

#### NTFS Partition Boot Sector

Trong một phân vùng NTFS, hệ thống cấp phát 16 sector đầu tiên cho tệp dữ liệu metadata khởi động và 15 sector tiếp theo cho chương trình khởi động ban đầu của boot sector (IPL).

Sector đầu tiên, còn gọi là boot sector, chứa các thông tin về khởi động bao gồm loại hệ thống tập tin cũng như kích thước và vị trí dữ liệu NTFS. Sector cuối cùng chứa một bản sao phụ của boot sector để tăng tính đáng tin cậy của hệ thống tập tin.

Dưới đây là một ví dụ về boot sector của phân vùng NTFS định dạng trên Windows 2000. Cấu trúc gồm ba phần như sau:

- Các byte 0x00-0x0A tạo thành lệnh nhảy và ID OEM.
- Các byte 0x0B-0x53 là khối tham số BIOS (BPB) và BPB mở rộng.
- Phần code còn lại là mã khởi động và đánh dấu cuối sector.

#### Cluster Sizes of NTFS Volume

Cluster là đơn vị cấp phát nhỏ nhất trên đĩa cứng được sử dụng để lưu trữ một tập tin. NTFS sử dụng các nhóm có kích thước khác nhau để lưu trữ các tập tin tùy thuộc vào kích thước của phân vùng NTFS. Hệ thống tập tin NTFS có số lượng nhóm tối đa mà nó có thể hỗ trợ. Vì chỉ một tập tin có thể sử dụng một nhóm và không thể sử dụng không gian trống bên trong một nhóm cho các tập tin khác, đĩa cứng có thể lưu trữ thông tin một cách hiệu quả nếu nhóm nhỏ. Hệ thống tập tin NTFS là một cấu trúc tổ chức tập tin hiệu quả vì nó sử dụng các nhóm nhỏ.

#### NTFS Master File Table (MFT)

Hệ thống tập tin NTFS bao gồm một tệp tên là bảng tập tin chính (MFT). Trên các phân vùng NTFS, ít nhất một mục được lưu trữ trong MFT.

Các mục MFT hoặc không gian bộ nhớ mô tả bởi các mục MFT bên ngoài chúng lưu trữ thông tin về thuộc tính của tập tin như kích thước, thời gian và ngày, quyền truy cập và nội dung dữ liệu. Kích thước MFT tăng theo số lượng tập tin được thêm vào phân vùng NTFS và các mục được thêm vào MFT. Khi người dùng xóa một tập tin từ một phân vùng NTFS, hệ thống tập tin đánh dấu các giá trị trong MFT là miễn phí và làm cho vị trí đó có thể tái sử dụng.

Công cụ xếp chồng lại (defragmentation) cho các phân vùng NTFS trên hệ thống dựa trên Windows 2000 không thể di chuyển các mục MFT. Do sự xếp chồng không cần thiết của MFT gây suy giảm hiệu suất của hệ thống tập tin, NTFS dành không gian cho MFT để duy trì nó càng gọn nhẹ càng tốt khi nó mở rộng. Đối với MFT trong mỗi phân vùng, NTFS dành một số không gian gọi là vùng MFT (MFT zone). Phân bổ không gian tuân theo một số quy tắc đơn giản như việc phân bổ không gian bên ngoài phân vùng cho vị trí đầu tiên trong vùng MFT và phân bổ bộ nhớ cho các tập tin và thư mục.

NTFS xem xét kích thước tập tin trung bình và các biến số khác khi phân bổ bộ nhớ cho vùng MFT dự trữ hoặc bộ nhớ chưa được dự trữ trên đĩa khi đĩa đạt tới dung lượng tối đa. Các phân vùng có số lượng tập tin tương đối lớn sẽ phân bổ không gian chưa được dự trữ trước, trong khi các phân vùng có số lượng tập tin tương đối nhỏ sẽ phân bổ vùng MFT trước.

MFT là một cơ sở dữ liệu quan hệ chứa thông tin về các tập tin và thuộc tính của tập tin. Nó cũng xác định một phân vùng NTFS và có thể lấy thông tin về mọi tập tin và thư mục có mặt trên đó. Nó có một "điểm bắt đầu" và một loại "bảng mục lục" cho phân vùng NTFS. MFT duy trì một bản ghi cho tất cả các tập tin hoặc thư mục mới được tạo trên phân vùng NTFS, trong đó kích thước của mỗi bản ghi gần như tương đương với kích thước nhóm của phân vùng NTFS.

MFT lưu trữ thông tin về tập tin dưới dạng "thuộc tính". Các hàng chứa các bản ghi tập tin và các cột chứa các thuộc tính tập tin. Ngoài ra, có 16 bản ghi được dành riêng cho các tệp hệ thống.

Các thuộc tính tập tin được lưu trữ trong bản ghi tập tin được gọi là thuộc tính cư trú (resident attributes), và những thuộc tính nằm ngoài MFT được gọi là thuộc tính phi cư trú (non-resident attributes). Nếu các thuộc tính dữ liệu nhỏ, chúng có thể được lưu trữ trong bản ghi MFT mà không cần sử dụng thêm không gian lưu trữ bổ sung trên phân vùng NTFS. Tuy nhiên, đối với các tập tin lớn hơn, các thuộc tính bổ sung mà không thể vừa trong bản ghi MFT phải được di chuyển ra khỏi bản ghi MFT dưới dạng thuộc tính phi cư trú và lưu trữ như các thuộc tính bên ngoài.

#### NTFS Attributes

Trong hệ thống tập tin NTFS, mỗi tập tin được coi là một tập hợp các thuộc tính. Mỗi tập tin chứa các thuộc tính duy nhất như tên, thông tin bảo mật và dữ liệu siêu dữ liệu của hệ thống tập tin. Một thuộc tính là một thực thể có tên, thuộc tính và chức năng. Hệ thống tập tin xác định mỗi thuộc tính bằng cách sử dụng mã loại thuộc tính và tên thuộc tính, giúp xác định tập tin. Hệ thống lưu trữ mỗi tập tin và thư mục theo hai cách sau đây:

Thuộc tính cư trú (Resident attributes): Thuộc tính cư trú là thông tin được lưu trữ trong một lượng không gian nhớ nhỏ trực tiếp trong bản ghi MFT. Tập tin MFT lưu trữ các thuộc tính thông thường là các thuộc tính cư trú. NTFS yêu cầu các thuộc tính được lưu trữ trong MFT để đảm bảo hoạt động đúng đắn.

Thuộc tính phi cư trú (Non-resident attributes): Nếu không có đủ không gian cho các thuộc tính hoặc nếu các thuộc tính yêu cầu nhiều không gian hơn có sẵn trong bản ghi MFT, thì hệ thống lưu trữ các thuộc tính đó ở một vị trí khác và đặt một tham chiếu đến vị trí tập tin trong MFT. Các thuộc tính được lưu trữ bên ngoài MFT được gọi là thuộc tính phi cư trú.

Các thuộc tính quan trọng trong NTFS bao gồm:

- STANDARD_INFORMATION: Thuộc tính này cung cấp thông tin chung về tập tin như CreationTime, LastChangeTime, LastModificationTime và LastAccessTime.

- ATTRIBUTE_LIST: Danh sách thuộc tính duy trì danh sách các loại thuộc tính tập tin. Thuộc tính này chỉ tồn tại nếu ít nhất một loại thuộc tính là thuộc tính phi cư trú.

- $FILE_NAME: Tên tập tin được lưu trữ trong thuộc tính này. Nó cũng bao gồm các trường cho CreationTime, LastChangeTime, LastModificationTime và LastAccessTime.

- OBJECT_ID: Thuộc tính này giữ một ID được sử dụng bởi dịch vụ Distributed Link Tracking.

- SECURITY_DESCRIPTOR: Thuộc tính này chứa thông tin về bảo mật của tập tin. Trong các phiên bản NTFS mới nhất, tất cả thông tin bảo mật được lưu trữ trong một tệp duy nhất có tên là $SECURE. Với thuộc tính này, đối với các tập tin có cùng mức độ bảo mật, thông tin bảo mật không cần được lưu trữ trong từng tập tin.

- INDEX_ROOT: Một thư mục bao gồm một chỉ mục, cung cấp thông tin về các tập tin liên quan đến thư mục đó. Nếu chỉ mục có ít mục, chúng được lưu trữ trong thuộc tính $INDEX_ROOT. Nếu có nhiều mục, chúng được lưu trữ trong thuộc tính $INDEX_ALLOCATION. Các mục trong chỉ mục hình thành một cây b.

#### Dòng dữ liệu (Data Stream) trên NTFS

Dòng dữ liệu (data stream) đề cập đến một chuỗi byte. Trong quá trình điều tra đĩa, ta có thể thêm dữ liệu vào hoặc sửa đổi các tập tin hiện có. Dòng dữ liệu có thể không mang ý nghĩa hoặc có giá trị phục vụ cho mục tiêu chứng cứ hoặc pháp y. Đó là một thuộc tính bổ sung của các tập tin trên NTFS.

Việc sử dụng dấu hai chấm (:) giữa phần mở rộng tập tin và dòng dữ liệu là bắt buộc vì nó giống như dòng dữ liệu trong MFT (Master File Table), như được minh họa dưới đây:

`C:\ECHO text_message> myfile.txt:stream1`

Lệnh sau đây hiển thị nội dung của dòng dữ liệu:

`C:\ MORE < myfile.txt:stream1`

Dòng dữ liệu không xuất hiện khi người dùng mở một dòng dữ liệu trong trình chỉnh sửa văn bản. Phương pháp duy nhất để xác định xem một dòng dữ liệu có tồn tại trong tập tin là kiểm tra MFT cho mục tương ứng của tập tin đó.

Khi bạn sao chép một tập tin NTFS vào một phân vùng FAT như đĩa mềm, các dòng dữ liệu và các thuộc tính khác không được hỗ trợ bởi FAT sẽ bị mất đi.

#### Tập tin nén trên NTFS

Windows NT/2000 hỗ trợ nén tập tin, thư mục và phân vùng NTFS. Bất kỳ ứng dụng nào chạy trên hệ điều hành Windows có thể đọc và ghi tập tin đã nén trên một phân vùng NTFS mà không cần giải nén chúng. Quá trình giải nén diễn ra tự động khi hệ thống hoặc ứng dụng cố gắng đọc một tập tin, và quá trình nén diễn ra khi tập tin được đóng lại hoặc lưu lại. NTFS chứa các thuật toán nén hỗ trợ kích thước nhóm (cluster) khoảng 4 KB. Khi kích thước nhóm lớn hơn 4 KB trên một phân vùng NTFS, không có chức năng nén NTFS nào khả dụng.

Để thiết lập Trạng thái Nén cho một Phân vùng: 
- Nhấp chuột phải vào ổ đĩa cần nén và chọn Properties (Thuộc tính)
- Trong tab General (Chung), chọn "Compress this drive to save disk space" (Nén ổ đĩa này để tiết kiệm không gian đĩa) và nhấp vào Apply (Áp dụng)
- Trong hộp thoại Confirm Attribute Changes (Xác nhận thay đổi thuộc tính), chọn một tùy chọn và nhấp OK (Đồng ý)

#### Encrypting File System (EFS)

Để bảo vệ tập tin khỏi việc xử lý không đúng và đảm bảo tính bảo mật, hệ thống cần mã hóa chúng. Vì mục đích này, NTFS có tính năng tích hợp gọi là Hệ thống Mã hóa Tập tin (Encrypting File System - EFS). Mã hóa trong hệ thống tệp sử dụng công nghệ mã hóa khóa đối xứng kết hợp với công nghệ khóa công khai để thực hiện quá trình mã hóa. Người dùng được cung cấp một chứng chỉ số với một cặp khóa gồm khóa công khai và khóa riêng. Khóa riêng không áp dụng cho người dùng đăng nhập vào hệ thống cục bộ; thay vào đó, hệ thống sử dụng EFS để thiết lập một khóa cho người dùng cục bộ.

Công nghệ mã hóa này duy trì một mức độ minh bạch đối với người dùng đã mã hóa một tập tin. Người dùng không cần giải mã tập tin khi truy cập để thay đổi nội dung. Sau khi người dùng hoàn thành công việc trên một tập tin, hệ thống lưu các thay đổi và tự động khôi phục chính sách mã hóa.

Khi người dùng trái phép cố gắng truy cập vào một tập tin đã được mã hóa, họ sẽ nhận thông báo "Truy cập bị từ chối". Để kích hoạt chức năng mã hóa và giải mã trên hệ điều hành dựa trên Windows NT, người dùng phải thiết lập thuộc tính mã hóa cho các tập tin và thư mục mà họ muốn mã hóa hoặc giải mã. Hệ thống tự động mã hóa tất cả các tập tin và thư mục con trong một thư mục. Để tận dụng tối đa khả năng mã hóa, các chuyên gia khuyến nghị hệ thống nên có mã hóa ở mức thư mục. Điều này đồng nghĩa với việc một thư mục không nên chứa cùng lúc các tập tin đã mã hóa và các tập tin chưa mã hóa.

Người dùng có thể mã hóa tập tin hoặc thư mục bằng cách sử dụng giao diện đồ họa (GUI) của Windows, sử dụng công cụ dòng lệnh như Cipher, hoặc thông qua Windows Explorer bằng cách chọn các tùy chọn thích hợp trong menu.

Mã hóa quan trọng đối với các tập tin nhạy cảm trong một hệ thống, và NTFS sử dụng mã hóa để bảo vệ tập tin khỏi việc truy cập trái phép và đảm bảo mức độ bảo mật cao. Hệ thống cấp một chứng chỉ mã hóa tập tin mỗi khi người dùng mã hóa một tập tin. Nếu người dùng mất chứng chỉ đó và khóa riêng liên quan (qua đĩa hoặc bất kỳ nguyên nhân nào khác), họ có thể thực hiện phục hồi dữ liệu thông qua thành phần khóa phục hồi. Trong mạng dựa trên Windows 2000 Server, duy trì dịch vụ Active Directory, quản trị viên miền là thành phần khóa phục hồi theo mặc định. Việc chuẩn bị cho việc phục hồi tập tin được thực hiện trước, ngay cả trước khi người dùng hoặc hệ thống mã hóa chúng. Thành phần khóa phục hồi giữ một chứng chỉ đặc biệt và khóa riêng liên quan, hỗ trợ trong quá trình phục hồi dữ liệu.

#### Các thành phần của EFS

##### Dịch vụ EFS

Dịch vụ EFS, là một phần của hệ thống bảo mật, hoạt động như một giao diện với trình điều khiển EFS bằng cách sử dụng cổng truyền thông gọi cục bộ (LPC) giữa Local Security Authority (LSA) và trình giám sát tham chiếu bảo mật trong chế độ kernel.
Nó cũng hoạt động như một giao diện với CryptoAPI trong chế độ người dùng để tạo ra khóa mã hóa tập tin để tạo ra các trường giải mã dữ liệu (DDF) và các trường phục hồi dữ liệu (DRF). Dịch vụ này cũng hỗ trợ các giao diện lập trình ứng dụng Win32 (APIs).
Dịch vụ EFS sử dụng CryptoAPI để trích xuất khóa mã hóa tập tin (FEK) cho một tập tin dữ liệu và sử dụng nó để mã hóa FEK và tạo ra DDF.

##### Trình điều khiển EFS

Trình điều khiển EFS là một trình điều khiển bộ lọc hệ thống tệp tin được xếp chồng lên NTFS. Nó kết nối với dịch vụ EFS để lấy khóa mã hóa tập tin, DDF, DRF và các dịch vụ quản lý khóa khác.
Nó gửi thông tin này đến thư viện chạy thời gian hệ thống tệp tin EFS (FSRTL) để thực hiện các chức năng hệ thống tệp tin như mở, đọc, ghi và thêm.

##### CryptoAPI

CryptoAPI bao gồm một tập hợp các hàm cho phép các nhà phát triển ứng dụng mã hóa ứng dụng Win32 của họ; các hàm này cho phép ứng dụng mã hóa hoặc ký số dữ liệu và cung cấp bảo mật cho dữ liệu khóa riêng.

Nó hỗ trợ các hoạt động khóa công khai và khóa đối xứng như tạo, quản lý và lưu trữ an toàn, trao đổi, mã hóa, giải mã, băm, chữ ký số và xác minh chữ ký.

##### EFS FSRTL

EFS FSRTL là một phần của trình điều khiển EFS thực hiện các cuộc gọi NTFS để xử lý các hoạt động hệ thống tệp tin khác nhau như đọc, ghi và mở các tập tin và thư mục đã được mã hóa, cũng như các hoạt động để mã hóa, giải mã và khôi phục dữ liệu tập tin khi hệ thống ghi nó vào hoặc đọc nó từ đĩa.

Trình điều khiển EFS và FSRTL hoạt động như một thành phần duy nhất nhưng không truyền thông trực tiếp. Chúng giao tiếp với nhau bằng cách sử dụng cơ chế cuộc gọi điều khiển tệp NTFS.

##### Win32 API

EFS cung cấp một tập hợp các API để cung cấp truy cập vào các tính năng của nó; bộ API cung cấp giao diện lập trình cho các hoạt động như mã hóa các tập tin văn bản thô, giải mã hoặc khôi phục các tập tin mã hóa và nhập và xuất các tập tin đã mã hóa mà không cần giải mã.

#### Tập tin thưa thớt (Sparse Files)

Tập tin thưa thớt (sparse file) là một loại tập tin trên máy tính được thiết kế để sử dụng không gian hệ thống tệp tin hiệu quả hơn khi các khối được cấp phát cho tập tin này chủ yếu là trống rỗng. Để cải thiện hiệu suất, hệ thống tệp tin ghi thông tin ngắn gọn (metadata) về tập tin vào các khối trống để sử dụng không gian đĩa một cách tối ưu.

Các tập tin thưa thớt cung cấp một kỹ thuật tiết kiệm không gian đĩa bằng cách cho phép hệ thống I/O chỉ cấp phát dữ liệu có ý nghĩa (khác không). Trong một tập tin thưa thớt NTFS, các cụm được gán cho dữ liệu mà ứng dụng xác định; trong trường hợp dữ liệu không được xác định, hệ thống tệp tin đánh dấu không gian đó là chưa được cấp phát.

## Linux File Systems

Hệ điều hành Linux sử dụng các hệ thống tệp tin khác nhau để lưu trữ dữ liệu. Vì các nhà điều tra có thể gặp các nguồn tấn công hoặc hệ thống nạn nhân chạy Linux, họ nên có kiến thức toàn diện về các phương pháp lưu trữ mà nó sử dụng. Phần tiếp theo cung cấp cái nhìn sâu sắc về các hệ thống tệp tin Linux phổ biến và cơ chế lưu trữ của chúng.

### Linux File System Architecture 

Kiến trúc hệ thống tệp tin Linux bao gồm hai phần sau:

1. User space (Không gian người dùng):

	Đây là khu vực bảo vệ trong bộ nhớ nơi các tiến trình người dùng chạy, và khu vực này chứa bộ nhớ khả dụng.

2. Kernel space (Không gian kernel):

	Đây là không gian bộ nhớ mà hệ thống cung cấp tất cả các dịch vụ kernel thông qua các tiến trình kernel. Người dùng chỉ có thể truy cập không gian này thông qua một cuộc gọi hệ thống. Một tiến trình người dùng chỉ trở thành một tiến trình kernel khi nó thực hiện một cuộc gọi hệ thống.


Thư viện GNU C (glibc) nằm giữa không gian người dùng và không gian kernel và cung cấp giao diện cuộc gọi hệ thống kết nối kernel với các ứng dụng không gian người dùng.

Hệ thống tệp ảo (VFS) là một lớp trừu tượng trên cùng của một hệ thống tệp tin hoàn chỉnh. Nó cho phép các ứng dụng khách truy cập vào các hệ thống tệp tin khác nhau. Kiến trúc nội bộ của nó bao gồm một lớp phân tán, cung cấp trừu tượng hóa hệ thống tệp và nhiều bộ nhớ cache để tăng hiệu suất của các hoạt động trên hệ thống tệp tin.

Các đối tượng chính được quản lý động trong VFS là đối tượng dentry và inode; các đối tượng này được quản lý dưới dạng cache để tăng tốc độ truy cập vào hệ thống tệp tin. Khi một người dùng mở một tập tin, bộ nhớ cache dentry sẽ được điền với các mục đại diện cho các cấp thư mục, mà trong đó đại diện cho đường dẫn. Hệ thống cũng tạo ra một inode cho đối tượng đại diện cho tập tin. Hệ thống phát triển một bộ nhớ cache dentry bằng một bảng băm và cấp phát các mục cache dentry từ trình cấp phát slab dentry_cache. Hệ thống sử dụng thuật toán least-recently-used (LRU) để cắt tỉa các mục khi bộ nhớ khan hiếm.

Bộ nhớ cache inode hoạt động như hai danh sách và một bảng băm để tìm kiếm nhanh chóng. Danh sách đầu tiên định nghĩa các inode đã sử dụng, và các inode không sử dụng được đặt trong danh sách thứ hai. Bảng băm cũng lưu trữ các inode đã sử dụng.

Các trình điều khiển thiết bị là các đoạn mã liên kết với mọi thiết bị vật lý hoặc ảo và giúp hệ điều hành quản lý phần cứng của thiết bị. Các chức năng của các trình điều khiển thiết bị bao gồm thiết lập phần cứng, đưa thiết bị liên quan vào và ra khỏi dịch vụ, thu thập dữ liệu từ phần cứng và cung cấp nó cho kernel, truyền dữ liệu từ kernel đến thiết bị, và xác định và xử lý lỗi thiết bị.

### Filesystem Hierarchy Standard (FHS)

Linux có một cấu trúc cây phân cấp duy nhất đại diện cho hệ thống tệp tin như một thực thể duy nhất. Nó hỗ trợ nhiều loại hệ thống tệp tin khác nhau và triển khai một tập hợp cơ bản các khái niệm chung, ban đầu được phát triển cho UNIX.

Một số loại hệ thống tệp tin Linux là Minix, Filesystem Hierarchy Standard (FHS), ext, ext2, ext3, xia, MS-DOS, UMSDOS, VFAT, /proc, NFS, ISO 9660, HPFS, SysV, SMB và NCPFS. Minix là hệ thống tệp tin đầu tiên của Linux.

Dưới đây là một số hệ thống tệp tin phổ biến nhất:

- Filesystem Hierarchy Standard (FHS) định nghĩa cấu trúc thư mục và nội dung của nó trong Linux và các hệ điều hành tương tự Unix.
- Trong FHS, tất cả các tệp và thư mục đều có mặt dưới thư mục gốc (được biểu thị bằng /).

### Extended File System (ext)

Hệ thống tệp mở rộng (ext), hoặc hệ thống tệp mở rộng đầu tiên, được phát hành vào tháng 4 năm 1992, là hệ thống tệp đầu tiên vượt qua các giới hạn của hệ thống tệp Minix. Ban đầu, nó được phát triển như một phần mở rộng của hệ thống tệp Minix để khắc phục một số hạn chế như kích thước phân vùng tối đa là 64 MB và tên tệp ngắn. Hệ thống tệp ext cung cấp kích thước phân vùng tối đa là 2 GB và độ dài tên tệp tối đa là 255 ký tự. Hạn chế chính của hệ thống tệp này là nó không hỗ trợ các dấu thời gian riêng biệt cho truy cập, sửa đổi inode và dữ liệu. Nó duy trì một danh sách không được sắp xếp của các khối và inode trống, và hệ thống tệp bị phân mảnh.

Hệ thống tệp ext có cấu trúc siêu dữ liệu được lấy cảm hứng từ Hệ thống Tệp UNIX (UFS). Nhược điểm khác của hệ thống tệp này bao gồm chỉ có một dấu thời gian và các danh sách liên kết cho không gian trống, dẫn đến sự phân mảnh và hiệu suất kém. Nó đã được thay thế bởi hệ thống tệp mở rộng thứ hai (ext2).

### Second Extended File System (ext2)

Hệ thống tệp mở rộng thứ hai (ext2) được phát triển bởi Remy Card như một hệ thống tệp mở rộng và mạnh mẽ cho Linux. Là hệ thống tệp thành công nhất cho đến nay trong cộng đồng Linux, Ext2 là cơ sở cho tất cả các bản phân phối Linux hiện đang sử dụng.

Hệ thống tệp ext2 được phát triển dựa trên nguyên tắc lưu trữ dữ liệu dưới dạng các khối dữ liệu cùng độ dài. Mặc dù độ dài có thể thay đổi giữa các hệ thống tệp ext2 khác nhau, kích thước khối của một hệ thống tệp ext2 được đặt trong quá trình tạo.

Hệ thống làm tròn kích thước của mỗi tệp thành một số nguyên khối. Nếu kích thước khối là 1024 byte, thì một tệp có kích thước 1025 byte sẽ chiếm hai khối 1024 byte. Không phải tất cả các khối trong hệ thống tệp chứa dữ liệu; một số khối phải chứa thông tin mô tả cấu trúc của hệ thống tệp. Hệ thống tệp ext2 xác định cấu trúc của hệ thống tệp bằng cách mô tả mỗi tệp trong hệ thống bằng một cấu trúc dữ liệu inode.

Một inode mô tả các khối được sử dụng bởi dữ liệu trong một tệp, cũng như quyền truy cập của tệp, thời gian sửa đổi của tệp và loại tệp. Một inode đơn duy nhất mô tả mỗi tệp trong hệ thống tệp ext2, và mỗi inode có một số duy nhất xác định nó.

Bảng inode lưu trữ tất cả các inode cho hệ thống tệp. Hơn nữa, các thư mục ext2 chỉ đơn giản là các tệp đặc biệt (được mô tả bởi các inode) chứa các con trỏ đến các inode của các mục thư mục của chúng.

#### Superblock

Một superblock lưu trữ thông tin về kích thước và hình dạng của hệ thống tệp ext2. Thông tin này cho phép trình quản lý hệ thống tệp sử dụng và quản lý hệ thống tệp. Thông thường, hệ thống chỉ đọc superblock trong nhóm khối 0 khi người dùng gắn kết hệ thống tệp. Tuy nhiên, mỗi nhóm khối có một bản sao trùng lặp nếu hệ thống tệp bị hỏng.

Một superblock chứa các thông tin sau:
- **Số thần kỳ (Magic number)**: Nó cho phép phần mềm gắn kết xác minh Superblock cho hệ thống tệp ext2. Đối với phiên bản ext2 hiện tại, số thần kỳ là 0xEF53.
- **Cấp độ sửa đổi (Revision level)**: Các cấp độ sửa đổi chính và phụ cho phép mã gắn kết xác định liệu hệ thống tệp có hỗ trợ các tính năng chỉ có sẵn trong các phiên bản cụ thể của hệ thống tệp. Có cũng các trường tương thích tính năng giúp mã gắn kết xác định các tính năng mới nào có thể sử dụng an toàn trên hệ thống tệp.
- **Số lần gắn kết và số lần gắn kết tối đa**: Cùng nhau, chúng cho phép hệ thống xác định xem liệu nó cần kiểm tra đầy đủ hệ thống tệp hay không. Số lần gắn kết tăng lên mỗi khi hệ thống gắn kết hệ thống tệp. Khi số lần gắn kết đạt đến số lần gắn kết tối đa, thông báo cảnh báo "đạt đến số lần gắn kết tối đa, nên chạy e2fsck" được hiển thị.
- **Số nhóm khối (Block group number)**: Đây là số nhóm khối chứa bản sao của superblock
- **Kích thước khối (Block size)**: Nó chứa thông tin về kích thước của một khối cho hệ thống tệp theo byte
- **Số khối trên mỗi nhóm (Blocks per group)**: Đây là một số cố định bằng số khối trong một nhóm
- **Khối trống (Free blocks)**: Đây là số khối trống trong hệ thống tệp
- **Inode trống (Free inodes)**: Đây là số inode trống trong hệ thống tệp
- **Inode đầu tiên (First inode)**: Đây là số inode đầu tiên của hệ thống tệp
 
#### Group Descriptor (Mô tả Nhóm)

Mỗi mô tả nhóm chứa các dữ liệu sau:
- **Bảng bitmap khối (Block bitmap)**: Đây là số khối của bảng phân bố khối cho nhóm khối. Nó được sử dụng trong quá trình phân bố và hủy bỏ khối.
- **Bảng bitmap inode (Inode bitmap)**: Đây là số khối của bảng phân bố inode cho nhóm khối. Nó được sử dụng trong quá trình phân bố và hủy bỏ inode.
- **Bảng inode (Inode table)**: Đây là số khối của khối bắt đầu cho bảng inode cho nhóm khối
- **Số khối trống, số inode trống và số thư mục đã sử dụng (Free block count, free inode count, and used directory count)**: Tất cả các mô tả nhóm cùng nhau tạo thành bảng mô tả nhóm. Mỗi nhóm khối có toàn bộ bảng mô tả nhóm.

#### Ext2 Inode

Trong hệ thống tệp ext2, inode là khối xây dựng cơ bản. Mỗi file và thư mục trong hệ thống tệp đều có một và chỉ một inode để mô tả.

Hệ thống tệp lưu trữ các inode ext2 cho mỗi nhóm khối trong bảng inode, cùng với một bảng bitmap cho phép hệ thống theo dõi các inode đã được phân bố và chưa được phân bố.

Một inode ext2 chứa các trường sau:

- **Chế độ (Mode)**: Trường này chứa hai thông tin: mô tả của inode này và quyền truy cập của người dùng. Trong ext2, một inode có thể mô tả một file, thư mục, liên kết tượng trưng, thiết bị khối, thiết bị ký tự hoặc đường ống FIFO.
- **Thông tin chủ sở hữu**: Trường này chứa thông tin về người sở hữu của file hoặc thư mục, bao gồm các định danh người dùng và nhóm. Nó cho phép hệ thống tệp xác định quyền truy cập một cách chính xác.
- **Kích thước**: Trường này chứa kích thước của file trong byte.
- **Dấu thời gian**: Trường này chứa thời gian tạo inode và thời gian sửa đổi lần cuối cùng.
- **Các khối dữ liệu**: Các khối dữ liệu là các con trỏ đến các khối chứa dữ liệu được mô tả bởi inode này. 12 con trỏ đầu tiên trỏ đến các khối vật lý chứa dữ liệu mô tả bởi inode này, và 3 con trỏ cuối cùng chứa các mức đánh dấu liên tiếp. Ví dụ, con trỏ khối gián tiếp kép trỏ đến một khối chứa con trỏ đến các khối con trỏ đến các khối dữ liệu.

#### Thư mục ext2

Trong hệ thống tệp ext2, thư mục là các tệp đặc biệt được sử dụng để tạo và giữ đường dẫn truy cập đến các tệp trong hệ thống tệp. Một tệp thư mục là một danh sách các mục thư mục, mỗi mục chứa các thông tin sau.

- **Inode**: Đây là inode cho mục thư mục và là một chỉ mục vào mảng các inode trong bảng inode của nhóm khối.
Độ dài tên (Name length): Đây là độ dài của mục thư mục theo byte.
- **Tên (Name)**: Đây là tên của mục thư mục.

### Hệ thống tệp mở rộng thứ ba (ext3)

Được phát triển bởi Stephen Tweedie vào năm 2001, hệ thống tệp mở rộng thứ ba (ext3) là một hệ thống tệp ghi nhật ký được sử dụng trong hệ điều hành GNU/Linux. Đây là phiên bản nâng cao của hệ thống tệp ext2. Lợi ích chính của hệ thống tệp này là khả năng ghi nhật ký, giúp cải thiện tính tin cậy của hệ thống máy tính. Nó có thể được gắn kết và sử dụng như một hệ thống tệp ext2 và có thể sử dụng tất cả các chương trình được phát triển trong hệ thống tệp ext2.

Kích thước tối đa của một tệp ext3 đơn lẻ nằm trong khoảng từ 16 GB đến 2 TB, và kích thước tối đa của toàn bộ hệ thống tệp ext3 nằm trong khoảng từ 2 TB đến 32 TB. Hệ thống tệp ext3 cũng cung cấp tính toàn vẹn dữ liệu tốt hơn. Nó đảm bảo rằng dữ liệu tương thích với trạng thái của hệ thống tệp. Hơn nữa, ext3 nhanh hơn ext2 vì tính năng ghi nhật ký tối ưu hóa chuyển động đầu đĩa cứng. Nó cũng cung cấp ba chế độ ghi nhật ký để tùy chọn giữa việc tối đa hóa tính toàn vẹn dữ liệu và tối ưu hóa tốc độ. Hệ thống tệp ext3 cũng rất đáng tin cậy và có khả năng chuyển đổi phân vùng ext2 sang ext3 và ngược lại mà không cần phải phân vùng lại và sao lưu dữ liệu.

Lệnh để chuyển đổi ext2 sang ext3:

# /sbin/tune2fs -j <tên-phân-vùng>

Ví dụ, để chuyển đổi một hệ thống tệp ext2 nằm trên phân vùng /dev/hda5 thành một hệ thống tệp ext3, bạn có thể sử dụng lệnh sau:

# /sbin/tune2fs -j /dev/hda5

Các tính năng của Ext3

- **Toàn vẹn dữ liệu:** Nó cung cấp tính toàn vẹn dữ liệu mạnh mẽ cho các sự kiện xảy ra do tắt máy hệ thống. Người dùng có thể chọn loại và mức bảo vệ cho dữ liệu nhận được.
- **Tốc độ:** Vì hệ thống tệp ext3 là một hệ thống tệp ghi nhật ký, nó có hiệu suất cao hơn trong hầu hết các trường hợp so với ext2. Người dùng có thể chọn tốc độ tối ưu từ ba chế độ ghi nhật ký khác nhau.
- **Chuyển đổi dễ dàng:** Người dùng có thể dễ dàng chuyển đổi hệ thống tệp từ ext2 sang ext3 và tăng hiệu suất của hệ thống bằng cách sử dụng hệ thống tệp ghi nhật ký mà không cần định dạng lại.

### Hệ thống tệp mở rộng thứ tư (ext4)

Hệ thống tệp mở rộng thứ tư (ext4) là một hệ thống tệp ghi nhật ký được phát triển như là người kế nhiệm của hệ thống tệp ext3 phổ biến. Nó cung cấp khả năng mở rộng và đáng tin cậy tốt hơn so với ext3 để hỗ trợ các hệ thống tệp lớn trên các máy tính 64 bit để đáp ứng nhu cầu về dung lượng đĩa ngày càng tăng.

Hệ thống tệp ext4 cho phép ghi nhật ký theo mặc định và cho phép người dùng gắn kết một hệ thống tệp ext3 như một hệ thống tệp ext4. Hệ thống tệp này hỗ trợ Linux Kernel từ phiên bản 2.6.19 trở đi.

#### Các tính năng chính
- **Kích thước hệ thống tệp:** Ext4 hỗ trợ kích thước tệp tối đa lên đến 16 TB và kích thước thể tích tối đa khoảng 1 EiB (exbibyte)
- **Extents:** Nó thay thế hệ thống ánh xạ khối được tìm thấy trong ext2 và ext3 để tăng hiệu suất và giảm hiện tượng mảnh vụn
- **Delayed allocation:** Nó cải thiện hiệu suất và giảm hiện tượng mảnh vụn bằng cách trì hoãn việc phân bổ đến khi hệ thống xả dữ liệu vào đĩa
- **Phân bổ nhiều khối:** Nó phân bổ nhiều tệp liên tục trên một đĩa, từ đó giảm công việc gọi bộ phân bổ khối và tối ưu hóa phân bổ bộ nhớ
- **Tăng tốc độ kiểm tra hệ thống tệp (fsck):** Nó đánh dấu các nhóm khối và phần không được phân bổ và bỏ qua các phần đã đánh dấu khi thực hiện kiểm tra. Nhờ đó, nó hỗ trợ tốc độ kiểm tra hệ thống tệp nhanh hơn.
- **Kiểm tra tổng kiểm tra nhật ký:** Nó sử dụng kiểm tra tổng kiểm tra trong nhật ký để cải thiện tính đáng tin cậy
-** Phân bổ trước bền vững:** Hệ thống tệp có thể phân bổ không gian trên đĩa cho một tệp bằng cách ghi số không vào nó trong quá trình tạo
- **Cải thiện thông tin thời gian:** Nó cung cấp thông tin thời gian đo bằng nanosecond và hỗ trợ cho thông tin thời gian tạo
- **Tương thích ngược:** Hệ thống tệp tương thích ngược và cho phép người dùng gắn kết ext3 và ext2 như là ext4.

### Hiểu về Superblocks, Inodes và Data Blocks

##### Superblock

Một superblock chứa siêu dữ liệu của một hệ thống tệp; nó bao gồm chi tiết như kích thước của hệ thống tệp, kích thước khối, vị trí và kích thước của bảng inode, các khối đã được sử dụng và trống và số lượng tương ứng của chúng, thông tin về kích thước của các nhóm khối, thông tin về bản đồ khối đĩa và mức độ sử dụng.

Việc truy cập vào superblock của một hệ thống tệp là cần thiết để có thể yêu cầu truy cập vào bất kỳ tệp nào trong hệ thống tệp.

Một hệ thống tệp không thể được gắn kết nếu không thể truy cập vào superblock của nó; do đó, các tệp của nó không thể được truy cập. Nếu người dùng cố gắng gắn kết một hệ thống tệp có superblock bị hỏng hoặc bị hư hỏng, việc gắn kết sẽ thất bại và thường dẫn đến thông báo lỗi như "không thể đọc superblock."

Vì sự hỏng hóc của một superblock có thể phá hủy dữ liệu quan trọng, các bản sao dự phòng của dữ liệu được tạo tự động tại các khoảng thời gian nhất định trên hệ thống tệp (ví dụ: ở đầu mỗi nhóm khối).

Đối với mỗi hệ thống tệp đã gắn kết, Linux cũng duy trì một bản sao của superblock trong bộ nhớ.

Để xem thông tin superblock của một hệ thống tệp, sử dụng lệnh:
dumpe2fs /dev/sda1 | grep –i superblock

###### Inode

Inode lưu trữ siêu dữ liệu của các tệp và có thể cung cấp cho các nhà điều tra những chi tiết quan trọng liên quan đến các tệp.

Siêu dữ liệu của mỗi tệp được lưu trữ trong một inode dưới dạng một bảng. Inode thường tồn tại gần đầu một phân vùng. Mỗi inode được xác định bằng một số inode hoặc số chỉ mục inode. Mỗi tệp trên hệ thống Linux sẽ có một số inode duy nhất được gán cho nó khi nó được tạo.

Số inode của một tệp lưu trữ các thuộc tính như kích thước của tệp, loại tệp, quyền truy cập và kiểm soát truy cập, ngày/giờ, vị trí trên đĩa, vị trí tệp, v.v. Các tệp trong mỗi thư mục mang một số inode riêng, cùng với tên tệp.

Để xem số inode được gán cho các tệp hoặc thư mục, chạy lệnh sau:

	**ls -il**

Chú ý: Trong ảnh chụp màn hình trên, các số xuất hiện bên trái là số inode.

##### Data Blocks

Dưới đây là các chức năng của các khối dữ liệu trong hệ thống tệp Linux:

- Các khối dữ liệu lưu trữ dữ liệu thực tế của một tệp. Chúng cũng chứa các thư mục.
- Một khối dữ liệu chỉ có thể được phân bổ cho một tệp trong một hệ thống tệp.
- Trong trường hợp một khối dữ liệu không được phân bổ cho bất kỳ tệp nào, hệ thống coi nó như một khối dữ liệu có sẵn và phân bổ nó cho một tệp khi cần thiết.
- Khi một tệp bị xóa, khối dữ liệu liên quan đến nó trở thành tự do và trống rỗng và có thể được phân bổ cho một tệp khác để lưu trữ nội dung của nó.
- Bằng cách truy xuất các khối dữ liệu của một tệp, các nhà điều tra có thể tìm thấy thông tin về dữ liệu thực tế được lưu trữ trong tệp.






