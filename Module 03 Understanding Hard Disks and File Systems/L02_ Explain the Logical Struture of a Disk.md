
Dữ liệu được lưu trữ trong máy tính được tổ chức dưới dạng các tập tin/thư mục theo cấu trúc cây được lưu trữ trên ổ cứng. Cấu trúc logic của một ổ cứng tương thích với hệ điều hành được cài đặt trên nó. Ổ cứng cần cấu trúc logic để hiểu ổ cứng và giải quyết các vấn đề liên quan đến đĩa. MBR (master boot record) là sector đầu tiên trên ổ cứng và nó chứa các boot loader và bảng phân vùng được truy cập bởi hệ điều hành.

## Cấu trúc logic của ổ cứng

Cấu trúc logic của một ổ đĩa cứng chủ yếu phụ thuộc vào các hệ thống tập tin được sử dụng và phần mềm như hệ điều hành. Những yếu tố này điều khiển và xác định quá trình truy cập dữ liệu trên ổ cứng. Hệ điều hành sử dụng các loại hệ thống tập tin khác nhau và những hệ thống tập tin này sử dụng các cơ chế điều khiển và truy cập khác nhau cho dữ liệu trên ổ cứng. Hệ điều hành tổ chức cùng một ổ đĩa cứng theo nhiều cách khác nhau. Cấu trúc logic của ổ đĩa cứng trực tiếp ảnh hưởng đến tính nhất quán, hiệu suất, khả năng tương thích và khả năng mở rộng của các phần tử lưu trữ của ổ đĩa cứng.

## Clusters

Cụm (Cluster) là đơn vị lưu trữ nhỏ nhất có thể truy cập được trên ổ đĩa cứng. Hệ thống tập tin chia khối lượng dữ liệu lưu trữ trên đĩa thành các phần nhỏ riêng biệt để đạt hiệu suất tối ưu và sử dụng đĩa hiệu quả. Cụm được tạo thành bằng cách kết hợp các sector để dễ dàng xử lý các tệp tin. Cụm cũng được gọi là đơn vị phân bổ, là một tập hợp các track và sector từ cụm số 2 đến 32 hoặc cao hơn, tuỳ thuộc vào kế hoạch định dạng. Hệ thống phân bổ tập tin phải linh hoạt để phân bổ các sector cần thiết cho các tệp tin. Phân bổ có thể có kích thước là một sector cho mỗi cụm. Mọi quá trình đọc hoặc ghi tiêu tốn ít nhất một cụm.

Để lưu trữ một tệp tin, hệ thống tập tin phải gán số cụm cần thiết cho nó. Kích thước của cụm hoàn toàn phụ thuộc vào khối lượng đĩa và thay đổi từ 4 đến 64 sector. Trong một số trường hợp, kích thước của cụm có thể là 128 sector. Các sector nằm trong một cụm là liên tục. Do đó, mỗi cụm là một phần không gian liên tục trên ổ đĩa cứng. Trong một cụm, khi hệ thống tập tin lưu trữ một tệp tin nhỏ hơn kích thước của cụm, không gian dư thừa sẽ bị lãng phí và được gọi là không gian trống (slack space).

### Cluster Size
Kích thước của cụm có ảnh hưởng quan trọng đến hiệu suất của hệ điều hành và sử dụng đĩa. Phân vùng đĩa xác định kích thước của một cụm, và các khối lượng lớn sử dụng kích thước cụm lớn hơn. Hệ thống có thể thay đổi kích thước cụm của một phân vùng hiện có để cải thiện hiệu suất. Nếu kích thước cụm là 8192 byte, hệ thống tập tin sẽ phân bổ một cụm đầy để lưu trữ một tệp tin có kích thước 5000 byte. Nếu kích thước của tệp tin là 10.000 byte, hệ thống tập tin sẽ phân bổ hai cụm tổng cộng 16.384 byte không gian lưu trữ. Do đó, kích thước cụm đóng vai trò quan trọng trong việc tối đa hóa việc sử dụng hiệu quả của đĩa. Việc sử dụng kích thước cụm lớn giảm thiểu vấn đề mảnh vỡ, nhưng cũng tăng khả năng sử dụng không gian không sử dụng.

Hệ thống tập tin chạy trên máy tính duy trì các mục nhập cụm. Các cụm tạo thành chuỗi trên đĩa sử dụng các số liên tiếp, không cần phải lưu trữ toàn bộ tệp tin trong một khối liên tục trên đĩa. Hệ thống tập tin có thể lưu trữ nó thành các phần được đặt ở bất kỳ vị trí nào trên đĩa cũng như di chuyển nó sang bất kỳ vị trí nào sau khi tạo tệp tin. Quá trình chuỗi cụm này không hiển thị cho hệ điều hành. Người dùng chỉ có thể thay đổi kích thước cụm khi định dạng lại ổ đĩa.

Các bước sau để thay đổi kích thước cụm:

- Chọn ổ đĩa cần định dạng, nhấp chuột phải và chọn Format từ menu thả xuống
- Trong hộp thoại Format, chọn kích thước đơn vị phân bổ mà ổ định dạng mới sẽ sử dụng. Kích thước cụm có thể từ 512 byte đến 4096 byte.

### Lost Clusters

Một cụm mất là một lỗi File Allocation Table (FAT) xảy ra khi hệ điều hành đánh dấu các cụm là đã sử dụng nhưng không phân bổ cho bất kỳ tệp tin nào. Lỗi này xuất phát từ quá trình mà hệ thống tập tin FAT sử dụng để gán không gian và nhóm các tệp tin cùng nhau. Đây chủ yếu là một lỗi cấu trúc logic và không phải là lỗi vật lý trên đĩa. Các cụm mất xảy ra khi người dùng không đóng tệp tin đúng cách hoặc tắt máy tính mà không đóng ứng dụng. Những lỗi này cũng xảy ra do hỏng đĩa như các trình điều khiển kém chất lượng và xung đột tài nguyên. Hệ điều hành đánh dấu những cụm này là đã sử dụng, mặc dù chúng không có tệp tin nào được gán hoặc liên kết với chúng. Các chương trình kiểm tra đĩa có thể kiểm tra một ổ đĩa hoàn chỉnh để tìm kiếm các cụm bị mất. Để phát hiện các cụm bị mất, người dùng có thể sử dụng một chương trình có thể lưu chúng dưới dạng tệp tin hoặc xóa chúng. Phương pháp sau sẽ gây hỏng tệp tin mới được tạo ra; tuy nhiên, dữ liệu bị lạc sẽ trở nên hiển thị và có thể khôi phục một số phần của dữ liệu đó.

Các chương trình kiểm tra đĩa có thể quét hệ thống máy tính để tìm kiếm các cụm bị mất bằng quy trình sau đây:

- Một bản sao trùng lặp được tạo trong bộ nhớ của FAT trong khi ghi chú tất cả các cụm được đánh dấu là "đang sử dụng".
- Bắt đầu từ thư mục gốc, các cụm được sử dụng bởi một tệp tin được theo dõi và đánh dấu là "đã tính toán" để kết nối chúng với tệp tin. Quy trình này được lặp lại cho tất cả các thư mục con.
- Các cụm bị mất hoặc "cụm mồ côi" được đánh dấu trong FAT là đang sử dụng nhưng không có liên kết với bất kỳ tệp tin nào.

Chkdsk.exe hoặc Check Disk là một tiện ích tích hợp sẵn trong Windows giúp phát hiện lỗi trong hệ thống tập tin và phương tiện đĩa. Tiện ích Check Disk nên được sử dụng trong trường hợp gặp sự cố như màn hình xanh và khó khăn trong việc mở hoặc lưu tệp tin hoặc thư mục. Tiện ích này cũng kiểm tra các sector hỏng và cụm bị mất.

Dưới đây là các bước để sử dụng phiên bản dòng lệnh của tiện ích Check Disk:

- Mở Command Prompt bằng cách gõ "cmd" trong tiện ích Run.
- Nhập "chkdsk" trong Command Prompt để chạy tiện ích Check Disk ở chế độ chỉ đọc.
- Sau khi quét hoàn tất, tiện ích Check Disk sẽ hiển thị trạng thái của ổ đĩa hiện tại.
Lưu ý rằng việc chạy tiện ích Check Disk có thể mất thời gian tương đối dài, tùy thuộc vào kích thước và trạng thái của ổ đĩa.

## Slack Space


Slack space (không gian lãng phí) là phần không gian bị lãng phí trong một cụm trên đĩa, nằm giữa cuối một tệp tin và cuối cụm; nó được tạo ra khi hệ thống tập tin cấp phát một cụm đầy đủ cho một tệp tin nhỏ hơn kích thước của cụm. Số lượng lớn tệp tin và kích thước cụm lớn dẫn đến lãng phí không gian đĩa do slack space. Hệ thống tập tin DOS và Windows sử dụng các cụm có kích thước cố định. Kích thước tiêu thụ bởi một tệp tin trong một cụm không phụ thuộc vào lưu trữ dữ liệu, mặc dù hệ thống tập tin dự trữ toàn bộ không gian trong một cụm cho một tệp tin.

Phiên bản cũ hơn của Windows và DOS sử dụng bảng phân bổ 16-bit, dẫn đến kích thước cụm lớn cho các phân vùng lớn. Ví dụ, nếu kích thước của mỗi phân vùng là 4 GB, kích thước của mỗi cụm là 32 KB và một tệp tin chỉ yêu cầu 10 KB, thì hệ thống sẽ cấp phát một cụm 32 KB đầy đủ, dẫn đến lãng phí không gian 22 KB.

Để loại bỏ sự không hiệu quả này, hệ thống sử dụng phân vùng. Một cách tiếp cận khác để giảm slack space là sử dụng Hệ thống Tệp Tin Công Nghệ Mới (NTFS), cho phép sử dụng cụm nhỏ hơn nhiều trên các phân vùng lớn so với FAT. Việc lưu trữ các tệp tin ít được sử dụng bằng cách nén cũng giúp giảm slack space. Khi kích thước đĩa ngày càng tăng, vấn đề slack space trở nên quan trọng hơn.

### Các loại Slack Space trong Tệp Tin:

- RAM slack: Slack RAM là không gian lưu trữ dữ liệu bắt đầu từ cuối tệp tin đến cuối sector cuối cùng của tệp tin.
- Drive slack: Slack của ổ đĩa là không gian lưu trữ dữ liệu bắt đầu từ cuối sector cuối cùng của tệp tin đến cuối cụm cuối cùng của tệp tin.


Trong lĩnh vực điều tra pháp y, slack space là một hình thức chứng cứ quan trọng. Thường xuyên, slack space có thể chứa thông tin liên quan đến nghi phạm cần thiết cho việc chứng minh tại tòa. Ví dụ, nếu nghi phạm xóa các tệp tin của một cụm đĩa cứng hoàn toàn và lưu các tệp tin mới, điều này chỉ chiếm một nửa của cụm, nửa còn lại có thể không trống. Nó có thể chứa dữ liệu của các tệp tin đã bị xóa. Nhà điều tra pháp y có thể thu thập dữ liệu này bằng cách sử dụng các công cụ pháp y máy tính.

## Master Boot Record (MBR)

Bộ ghi khởi động chính (Master Boot Record - MBR) là sector đầu tiên hoặc sector số không trên đĩa cứng, nó chỉ định vị trí của hệ điều hành để hệ thống tải vào bộ nhớ chính. MBR còn được gọi là sector phân vùng hoặc bảng phân vùng chính vì nó chứa một bảng xác định vị trí dữ liệu phân vùng trên đĩa cứng. Một chương trình trong bản ghi này tải phần còn lại của hệ điều hành vào RAM.

Một tệp MBR chứa thông tin về các tệp tin khác nhau hiện có trên đĩa, vị trí và kích thước của chúng. Trong thực tế, MBR hầu như luôn luôn ám chỉ sector khởi động hoặc sector phân vùng 512 byte của một đĩa cứng. Các lệnh fdisk/MBR giúp tạo MBR trên Windows và DOS. Khi máy tính khởi động, BIOS tham khảo sector đầu tiên này để lấy hướng dẫn quá trình khởi động và thông tin về cách tải hệ điều hành.

MBR được sử dụng để:

- Lưu trữ bảng phân vùng, chỉ định các phân vùng trên đĩa cứng
- Khởi tạo hệ điều hành
- Nhận diện đĩa cứng riêng lẻ bằng cách sử dụng một chữ ký đĩa 32 bit

MBR bao gồm các cấu trúc sau:

- Bảng phân vùng: Là một cấu trúc dữ liệu 64 byte lưu trữ thông tin về các loại phân vùng có trên đĩa cứng và vị trí của chúng. Bảng này có cấu trúc chuẩn không phụ thuộc vào hệ điều hành. Nó có khả năng mô tả chỉ bốn phân vùng, gọi là phân vùng chính hoặc phân vùng vật lý. Tất cả các phân vùng khác là các phân vùng logic liên kết với một trong các phân vùng chính.
- Mã khởi động chính (Master Boot Code): Đây là một đoạn mã máy tính nhỏ mà hệ thống tải vào BIOS và thực thi để khởi động quá trình khởi động của hệ thống. Sau khi thực thi, hệ thống chuyển quyền điều khiển cho chương trình khởi động có mặt trên phân vùng hoạt động để tải hệ điều hành.

Mã khởi động chính thực hiện các chức năng sau:

- Kiểm tra bảng phân vùng để tìm phân vùng hoạt động (active partition).
- Xác định sector đầu tiên của phân vùng hoạt động.
- Tải một bản sao của sector khởi động từ phân vùng hoạt động vào bộ nhớ.
- Chuyển quyền điều khiển cho mã thực thi trong sector khởi động.
MBR là một phần quan trọng của quá trình khởi động hệ thống và cung cấp thông tin quan trọng về phân vùng và các tệp tin trên đĩa cứng. Bất kỳ lỗi nào xảy ra trong MBR có thể ảnh hưởng đến khả năng khởi động của hệ thống và truy cập vào dữ liệu trên đĩa cứng.

### Structure of a Master Boot Record

Cấu trúc của MBR (Master Boot Record) bao gồm ba phần:

- Mã khởi động chính (Master Boot Code hoặc Boot Strap): Đây là mã thực thi và có trách nhiệm tải hệ điều hành vào bộ nhớ của máy tính. Nó được cấu thành từ một cấu trúc dữ liệu gồm 446 byte.
- Bảng phân vùng (Partition Table): Bảng phân vùng chứa thông tin về tất cả các phân vùng trên đĩa cứng và bao gồm một cấu trúc dữ liệu 64 byte.
- Chữ ký đĩa (Disk Signature): Nó được đặt ở cuối của MBR và chỉ chứa 2 byte dữ liệu. Chữ ký đĩa này được yêu cầu bởi BIOS trong quá trình khởi động.

Các hệ điều hành Windows và DOS sử dụng tệp MBR để lưu trữ thông tin về các tệp tin trên đĩa cứng. Nhiều sản phẩm thay thế tệp MBR do hãng Microsoft cung cấp. Một số công cụ tiện ích của bên thứ ba hữu ích khi cài đặt hai hoặc nhiều hệ điều hành trên một đĩa cứng.

Trong công tác điều tra pháp lý, các nhà điều tra cần sử dụng nhiều công cụ thu thập dữ liệu để thực hiện các nhiệm vụ pháp lý. Trong môi trường UNIX/Linux, lệnh "dd" được sử dụng để sao lưu và khôi phục MBR.

#### Để sao lưu MBR:

dd if=/dev/xxx of=mbr.backup bs=512 count=1

#### Để khôi phục MBR:

dd if=mbr.backup of=/dev/xxx bs=512 count=1

Trong đó, "/dev/xxx" đại diện cho thiết bị đĩa cần sao lưu hoặc khôi phục MBR.

## Disk Partitions

Phân vùng đĩa đề cập đến việc tạo ra các ổ đĩa logic để quản lý bộ nhớ một cách hiệu quả, và một phân vùng là một ổ đĩa logic để lưu trữ dữ liệu. Các phân vùng ẩn được tạo trên một ổ đĩa có thể ẩn dữ liệu. Khoảng trống giữa các phân vùng chính và phân vùng phụ được gọi là "inter-partition gap". Nếu phân vùng này chứa dữ liệu ẩn, các tiện ích chỉnh sửa đĩa như Disk Editor có thể được sử dụng để thay đổi thông tin trong bảng phân vùng. Việc làm này sẽ loại bỏ tất cả các tham chiếu đến phân vùng ẩn, đã được giấu khỏi hệ điều hành. Một phương pháp khác để ẩn dữ liệu là đặt dữ liệu, có thể là bằng chứng số, ở cuối ổ đĩa bằng cách khai báo số byte nhỏ hơn kích thước thực tế của ổ đĩa. Disk Editor cho phép nhà điều tra truy cập vào những khu vực ẩn hoặc không sử dụng trên đĩa.

Có hai loại phân vùng như sau:

- Phân vùng chính (Primary partition): Đây là ổ đĩa chứa thông tin về hệ điều hành, vùng hệ thống và thông tin khác cần thiết để khởi động. Trong MS-DOS và các phiên bản Windows trước đây của Microsoft, phân vùng chính đầu tiên (C:) phải là một phân vùng chính. Nó được gán chữ cái ổ đĩa "C:". Một ổ đĩa có thể có tối đa bốn phân vùng chính và mỗi phân vùng được coi là một thực thể riêng biệt.
- Phân vùng mở rộng (Extended partition): Đây là ổ đĩa logic chứa thông tin về dữ liệu và các tệp tin được lưu trữ trên đĩa. Có nhiều công cụ khác nhau để xem xét các phân vùng đĩa. Một số công cụ chỉnh sửa đĩa như Disk Edit, WinHex và Hex Workshop cho phép người dùng xem tiêu đề tệp và thông tin quan trọng về các tệp tin. Cả hai tính năng này đòi hỏi phân tích các mã thập lục phân mà hệ điều hành nhận dạng và sử dụng để duy trì hệ thống tệp tin.

### BIOS Parameter Block (BPB)

Khối thông số BIOS (BIOS Parameter Block - BPB) là một cấu trúc dữ liệu được đặt tại sector 1 trong bản ghi khởi động đĩa (Volume Boot Record - VBR) của ổ đĩa cứng và mô tả cấu trúc vật lý của một phân vùng đĩa. Trên các thiết bị được phân vùng như ổ đĩa cứng, nó mô tả phân vùng đĩa, trong khi trên các thiết bị chưa phân vùng, nó mô tả toàn bộ phương tiện lưu trữ. Bất kỳ phân vùng nào bao gồm đĩa mềm cũng có thể sử dụng BPB, nó cũng mô tả kiến trúc cơ bản của hệ thống tệp tin. Độ dài của BPB thay đổi theo các hệ thống tệp tin được liệt kê (ví dụ: FAT16, FAT32 và NTFS) vì các hệ thống tệp tin khác nhau lưu trữ các khối dữ liệu khác nhau và duy trì các loại trường khác nhau trong BPB.

### Globally Unique Identifier (GUID)

Globally Unique Identifier (GUID) là một số duy nhất có độ dài 128 bit được tạo ra bởi hệ điều hành Windows để xác định một thiết bị cụ thể, một tài liệu, một mục nhập trong cơ sở dữ liệu và/hoặc người dùng. Nó được biểu diễn dưới dạng 32 ký tự thập lục phân với các nhóm được phân tách bằng dấu gạch ngang.

Ví dụ, khi duyệt một trang web, một GUID được tạo ra và gán cho trình duyệt, giúp theo dõi và ghi lại phiên duyệt web của người dùng.

Hệ điều hành Windows gán một GUID cho bộ đăng ký để nhận diện thư viện liên kết động của Model Đối tượng thành phần (COM) cũng như cho các tài khoản người dùng dựa trên tên người dùng (miền).

#### Các ứng dụng phổ biến:

- Trong Registry của Windows, GUID được sử dụng để xác định DLL (thư viện liên kết động) COM (Component Object Model)
- Trong các bảng cơ sở dữ liệu, GUID được sử dụng làm giá trị khóa chính
- Trong một số trường hợp, một trang web có thể gán một GUID cho trình duyệt của người dùng để ghi lại và theo dõi phiên làm việc
- Windows gán một GUID cho tên người dùng để xác định tài khoản người dùng

## GUID Partition Table (GPT)

![](https://github.com/HuyThang25/Image/blob/main/R.jpg)

Bảng phân vùng GUID (GPT) là một chuẩn phân vùng cho ổ cứng và là một phần của Giao diện Firmware Mở rộng (UEFI), thay thế giao diện firmware BIOS cổ điển. UEFI sử dụng các hệ thống giao tiếp phân vùng vượt qua các hạn chế của chuẩn phân vùng MBR.

Chuẩn phân vùng MBR sử dụng 32 bit để lưu trữ Địa chỉ Khối Logic (LBA) và thông tin kích thước trên các sector 512 byte. Tương tự như MBR hiện đại, GPT sử dụng địa chỉ khối logic (LBA) thay vì địa chỉ cylinder–head–sector (CHS). Trong bảng phân vùng GUID (GPT), mỗi khối logic có kích thước 512 byte, và mỗi mục phân vùng có kích thước 128 byte; địa chỉ khối logic tiêu cực bắt đầu từ cuối của ổ đĩa, với -1 đại diện cho khối cuối cùng có thể truy cập được. LBA 0 lưu trữ MBR bảo vệ, LBA 1 chứa tiêu đề GPT, và tiêu đề GPT bao gồm một con trỏ đến bảng phân vùng hoặc Mảng Mục Phân vùng ở LBA 2. UEFI cấp 16.384 byte cho Mảng Mục Phân vùng. Vì ổ đĩa có sector 512 byte với một mảng mục phân vùng có kích thước 16.384 byte và kích thước tối thiểu là 128 byte cho mỗi mục phân vùng, LBA 34 là sector đầu tiên có thể sử dụng.

Dưới đây là những lợi ích của bố cục đĩa GPT:

- GPT cho phép người dùng phân vùng ổ đĩa lớn hơn 2 TB
- Nó cho phép người dùng có tối đa 128 phân vùng trong Windows sử dụng bố cục phân vùng GPT
- Phân vùng và dữ liệu khởi động GPT an toàn hơn so với MBR vì GPT lưu trữ dữ liệu ở nhiều vị trí trên đĩa
- Nó sử dụng kiểm tra tự động tạo mã dò lỗi (CRC) để đảm bảo tính toàn vẹn dữ liệu
- Sử dụng kiểm tra tự động tạo mã CRC32 để phát hiện lỗi trong tiêu đề và bảng phân vùng

### Protective MBR
 

MBR bảo vệ chiếm vị trí đầu tiên của GPT tại LBA 0. Nó giúp các hệ thống cổ điển giải quyết các vấn đề tương thích khi không hiểu được định dạng GPT. MBR bảo vệ lưu trữ mã khởi động cho các hệ điều hành hỗ trợ ổ đĩa khởi động GPT. Ngoài ra, nó đảm bảo rằng các hệ điều hành không thể nhận diện ổ đĩa GPT sẽ đánh dấu nó là không xác định và không thể xóa nó mà không có lệnh từ người dùng. Hơn nữa, các hệ điều hành nhận diện bảng phân vùng GPT cũng kiểm tra MBR bảo vệ trước khi bắt đầu các hoạt động. MBR bảo vệ tương tự với MBR cổ điển về chức năng, khác biệt chính là MBR bảo vệ chỉ có một phân vùng thuộc loại 0xEE (EFI_GPT_DISK). Nếu phân vùng không thuộc loại 0xEE hoặc bảng phân vùng MBR bao gồm nhiều mục, MBR sẽ không hoạt động.

Lệnh Get-MBR được sử dụng để hiển thị Bảng phân vùng MBR của ổ đĩa được định dạng GPT.

### GPT Header

Tiêu đề GPT đại diện cho phần bắt đầu chính thức của bảng phân vùng, không gian đĩa truy cập đầu tiên và cấu trúc của bảng phân vùng.

Một ổ đĩa cứng chạy hệ điều hành Windows 64-bit có thể có tối đa 128 phân vùng với kích thước mỗi phân vùng là 128 byte. Tiêu đề bảng phân vùng lưu trữ các thông tin về đĩa như ID phân vùng của ổ đĩa GPT, kích thước và vị trí của tiêu đề bảng phân vùng, một bản sao lưu của tiêu đề bảng phân vùng, vị trí và kích thước của bảng phân vùng.

Ngoài ra, nó lưu trữ mã kiểm tra CRC32 của bảng phân vùng, đó là một mã phát hiện lỗi được sử dụng để phát hiện các thay đổi ngẫu nhiên. Cơ chế kiểm tra này giúp chương trình khởi động, firmware và hệ điều hành phát hiện bất kỳ lỗi nào trong bảng phân vùng. Nếu xảy ra bất kỳ lỗi nào trong GPT chính, người dùng có thể khôi phục các phân vùng đĩa cứng từ GPT dự phòng, nhưng lỗi trong bảng phân vùng GPT dự phòng có thể làm cho đĩa cứng trở thành không thể truy cập.

#### GPT Header

- Là con trỏ đến bảng phân vùng và xác định bố cục logic hoàn chỉnh.
- Chứa thông tin như chữ ký "EFI PART" và GUID duy nhất của đĩa.
- Giá trị MyLBA, luôn là 1, xác định vị trí của tiêu đề GPT, trong khi giá trị AlternateLBA đại diện cho GPT dự phòng và chiếm lĩnh sector cuối cùng trên đĩa.
- GPT dự phòng thay thế GPT gốc khi nó bị hỏng.
- Giá trị FirstUsableLBA và LastUsableLBA chỉ đến phần của đĩa mà các phân vùng có thể sử dụng.
- Giá trị PartitionEntryLBA đại diện cho bắt đầu của mảng, trong khi NumberOfPartitionEntries và SizeOfPartitionEntry chỉ định kích thước tổng thể của phân vùng.

#### GPT Partition Array

Mảng entry phân vùng nằm kế tiếp tiêu đề GPT và sử dụng các khối 128 byte cho mỗi entry; 16 byte đầu tiên của mỗi khối đại diện cho GUID loại phân vùng. 16 byte tiếp theo chứa GUID đặcific cho khối phân vùng. Do tính độc nhất của GUID, không cần có một đăng ký trung tâm để chỉ định loại phân vùng GUID. Không cần thiết để mỗi sector bị giới hạn trong 512 byte, tức là 3 phân vùng chính và 1 phân vùng mở rộng. Một sector có thể có nhiều hơn bốn entry phân vùng. Thông số kỹ thuật GPT mô tả kích thước và tổ chức chung của cấu trúc dữ liệu (trừ LBA 0 và LBA 1), nhưng nó không đếm số lượng sector trên đĩa. Tiêu đề GPT trỏ đến mảng phân vùng thông qua giá trị PartitionEntryLBA. Kích thước và số lượng phân vùng được xác định trong tiêu đề GPT.

Mỗi phân vùng chứa các thông tin sau đây:

- Hai GUID, trong đó một đại diện cho loại phân vùng và một định danh duy nhất cho phân vùng.
- Giá trị StartingLBA và EndingLBA của phân vùng mô tả vị trí và kích thước của phân vùng.
- Thuộc tính cụ thể cho loại phân vùng.
- Tên phân vùng do người dùng định nghĩa gồm 36 ký tự.
