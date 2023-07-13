Hệ thống lưu trữ như Redundant Array of Independent Disks (RAID) và Just a Bunch Of Drives/Disks (JBOD) kết nối nhiều ổ đĩa cứng để tăng khả năng lưu trữ của một hệ thống.

Phần này giải thích về các cấp độ lưu trữ RAID khác nhau, cũng như các thiết bị lưu trữ Just a Bunch Of Drives/Disks (JBOD), hệ thống lưu trữ khu vực (SAN) và hệ thống lưu trữ đính kèm mạng (NAS).

## Hệ thống lưu trữ RAID

Redundant Array of Independent Disks (RAID) là một công nghệ sử dụng đồng thời nhiều ổ đĩa nhỏ, hoạt động như một ổ đĩa lớn duy nhất.

RAID cung cấp phương pháp truy cập vào một hoặc nhiều ổ đĩa cứng riêng biệt, giảm nguy cơ mất dữ liệu nếu một ổ đĩa cứng gặp sự cố hoặc bị hỏng. Hơn nữa, RAID giúp cải thiện thời gian truy cập.

Công nghệ RAID hỗ trợ trong các khía cạnh sau đây:
- Duy trì lượng lưu trữ dữ liệu lớn
- Đạt hiệu suất nhập/xuất cao
- Đảm bảo tính tin cậy thông qua dự phòng dữ liệu

Ý tưởng cơ bản của hệ thống lưu trữ RAID là nhóm nhiều ổ đĩa cứng nhỏ và giá rẻ thành một mảng các ổ đĩa cứng cung cấp hiệu suất cao hơn so với một ổ đĩa cứng lớn duy nhất. Một hệ thống lưu trữ RAID là một tập hợp các ổ đĩa cứng hoạt động và hiển thị như một ổ đĩa lớn duy nhất với dung lượng cao đối với người dùng. Lợi ích chính của hệ thống RAID là ngay cả khi một ổ đĩa trong mảng RAID gặp sự cố hoặc bị hỏng, hệ thống tổng thể vẫn tiếp tục hoạt động mà không mất dữ liệu. Điều này xảy ra vì dữ liệu của mỗi ổ đĩa cứng riêng biệt được lưu trữ trên một ổ đĩa khác trong mảng.

Hệ thống RAID cho phép truy cập đồng thời vào các tệp tin khác nhau trên các ổ đĩa cứng khác nhau, giảm thời gian tìm dữ liệu trên ổ đĩa cứng. Hệ thống RAID có tốc độ truyền dữ liệu cao hơn đáng kể so với một ổ đĩa cứng duy nhất.

## Các cấp độ hệ thống lưu trữ RAID

### RAID 0: Disk Striping

Đây là cấp độ RAID đơn giản nhất và không liên quan đến bất kỳ dự phòng nào. Ban đầu, nó chia tệp thành một mảng có kích thước stripe do người dùng xác định. Sau đó, nó gửi những stripe này đến mỗi ổ đĩa trong mảng. Vì RAID 0 không có dự phòng, cấp độ RAID này cung cấp các đặc điểm hiệu suất tổng thể tốt nhất trong các cấp độ RAID đơn.

Dưới đây là các đặc điểm của RAID 0:
- Nó chia dữ liệu thành các khối và ghi đồng đều trên nhiều ổ đĩa cứng
- Nếu một ổ đĩa gặp sự cố, không thể khôi phục dữ liệu
- Nó không cung cấp dự phòng dữ liệu
- Yêu cầu tối thiểu hai ổ đĩa để thiết lập
- Lợi ích chính của cấp độ này là hiệu suất nhập/xuất cao, vì nó phân tán các nhập/xuất qua nhiều kênh và ổ đĩa cứng
- Tốc độ truyền dữ liệu nhanh và hiệu quả nhất

### RAID 1: Disk Mirroring

RAID 1 thường thực hiện chức năng gương bằng cách nhân bản hoặc sao chép dữ liệu ổ đĩa trên hai ổ đĩa khác nhau bằng cách sử dụng một bộ điều khiển RAID phần cứng hoặc phần mềm. Nếu một trong hai ổ đĩa gặp sự cố, ổ còn lại hoạt động như một ổ đơn lẻ cho đến khi người dùng thay thế ổ đĩa hỏng bằng một ổ mới.

Dưới đây là các đặc điểm của RAID 1:
- Nó ghi nhiều bản sao của dữ liệu lên nhiều ổ đĩa đồng thời
- Nó cung cấp dự phòng dữ liệu bằng cách sao chép hoàn toàn dữ liệu ổ đĩa lên nhiều ổ đĩa khác nhau
- Nếu một ổ đĩa gặp sự cố, có thể khôi phục dữ liệu
- Yêu cầu tối thiểu hai ổ đĩa để thiết lập
- So với một ổ đĩa cứng đơn lẻ, cấp độ này đọc dữ liệu nhanh hơn và ghi dữ liệu chậm hơn vì dữ liệu được phân phối trên nhiều ổ đĩa cứng
- Cấp độ này cung cấp sự bảo vệ dữ liệu tốt nhất
- Nhược điểm chính của cấp độ này là việc truy cập dữ liệu chậm
- Nó cung cấp tính nhất quán cao và tiếp tục sẵn có dữ liệu trong trường hợp một ổ đĩa cứng gặp sự cố
- Nó cung cấp 100% dự phòng dữ liệu và không yêu cầu thời gian xây dựng lại dữ liệu

### RAID 2

RAID 2 là một trong những cấp độ RAID duy nhất không triển khai bất kỳ kỹ thuật tiêu chuẩn nào như tính chẵn lẻ, sao chép hoặc đánh vần. Nó sử dụng một kỹ thuật tương tự đánh vần với tính chẵn lẻ. Nó chia dữ liệu thành các bit và phân phối chúng đến nhiều ổ đĩa dữ liệu và ổ đĩa dự phòng.

### RAID 3

RAID 3 sử dụng đánh vần theo cấp byte với một ổ đĩa tính chẵn dự phòng, lưu trữ các checksum. Nó cũng hỗ trợ một bộ xử lý đặc biệt để tính toán mã tính chẵn. Cấp độ RAID này không thể xử lý nhiều yêu cầu dữ liệu cùng lúc. Trong trường hợp xảy ra sự cố, nó cho phép khôi phục dữ liệu bằng cách tính toán lại các byte tính chẵn và các byte còn lại liên quan đến chúng.

### RAID 5

RAID 5 sử dụng đánh vần dữ liệu theo cấp byte trên nhiều ổ đĩa và phân phối thông tin tính chẵn lẻ trên tất cả các ổ đĩa thành viên. Quá trình ghi dữ liệu chậm. Ngoài ra, nó yêu cầu tối thiểu ba ổ đĩa để thiết lập. RAID 5 đánh vần và phân phối mã phát hiện và sửa lỗi hoặc dữ liệu và mã tính chẵn trên ba hoặc nhiều ổ đĩa.

### RAID 10

RAID 10, còn được gọi là RAID 1+0, là sự kết hợp của RAID 0 (đánh vần dữ liệu khối) và RAID 1 (sao chép đĩa) để bảo vệ dữ liệu. Nó yêu cầu ít nhất bốn ổ đĩa để triển khai. Nó có khả năng chống lỗi giống như RAID cấp độ 1 và có cùng chi phí như sao chép đĩa một mình. Nó cho phép sao chép ổ đĩa theo cặp để dự phòng và cải thiện hiệu suất, sau đó đánh vần dữ liệu trên nhiều ổ đĩa để đạt được hiệu suất tối đa. Người dùng có thể truy xuất dữ liệu từ RAID nếu một ổ đĩa trong mỗi cặp sao chép hoạt động; tuy nhiên, nếu hai ổ đĩa trong cùng một cặp sao chép bị lỗi, dữ liệu sẽ không khả dụng.

### RAID 6

RAID 6 là phiên bản nâng cấp của RAID 5, trong đó tính chẵn lẻ kép được phân phối trên mỗi ổ đĩa RAID 5 để đảm bảo khả năng chống lỗi cao. Do đó, nó có thể chịu được hai ổ đĩa hỏng. Tuy nhiên, nó có hai tập dữ liệu tính chẵn lẻ của mỗi hoạt động ghi, dẫn đến giảm hiệu suất ghi và gánh nặng hiệu suất máy chủ. Cấu hình RAID 6 yêu cầu tối thiểu 4 ổ đĩa và tối đa 16 ổ đĩa để triển khai. Nó phù hợp nhất với môi trường mạng nơi nhiều giao dịch nhập/xuất nhỏ được thực hiện đồng thời.

### RAID 1E (Striped Mirroring)

RAID 1E là sự kết hợp giữa RAID 1 (sao chép dữ liệu) và RAID 0 (đánh vần dữ liệu). Trong RAID 1E, dữ liệu được ghi vào một stripe trên một ổ đĩa và được sao chép thành một stripe trên ổ đĩa tiếp theo trong mảng. Nó yêu cầu ít nhất 3 ổ đĩa để triển khai. Lợi thế chính của RAID 1E so với RAID 1 là mảng RAID 1E có thể triển khai bằng một số lẻ ổ đĩa và hỗ trợ lỗi đĩa đơn, thay vì lỗi nhiều đĩa.

### RAID 5E

RAID 5E tương tự như RAID 5 nhưng bao gồm một ổ đĩa dự phòng mở rộng, có thể được sử dụng cho các hoạt động nhập/xuất và cung cấp hiệu suất tốt hơn so với RAID 5. Ổ đĩa dự phòng mở rộng được tạo trong RAID 5E có thể được sử dụng với cùng một mảng. Nó yêu cầu ít nhất 4 ổ đĩa và tối đa 16 ổ đĩa trong một mảng duy nhất để triển khai.

### RAID 5EE

RAID 5EE tương tự như cấp độ RAID 5E và bao gồm một ổ đĩa dự phòng nóng bổ sung trong mảng RAID 5 có thể được sử dụng cho các hoạt động nhập/xuất. Nó yêu cầu ít nhất 4 ổ đĩa và tối đa 16 ổ đĩa trong một mảng. Khu vực dự phòng được phân phối ở cuối các thành phần ổ đĩa trong RAID 5E, trong khi nó được phân phối kế tiếp các dải chẵn lẻ trong RAID 5EE. Ổ đĩa dự phòng nóng bổ sung mặc định là trống và có thể được sử dụng để sao chép dữ liệu từ ổ đĩa hỏng.

### RAID 50 (striping with parity)

RAID 50 là sự kết hợp giữa RAID 5 (đánh vần với tính chẵn lẻ) và RAID 0 (đánh vần ổ đĩa). Cấu hình này yêu cầu ít nhất 6 ổ đĩa. Nó cung cấp mức độ chịu lỗi cao vì một ổ đĩa trong mỗi nhóm con-array có thể gặp sự cố mà không mất dữ liệu.

### RAID 60

RAID 60 là sự kết hợp giữa RAID 6 (tính chẵn phân tán) và RAID 0 (đánh vần ổ đĩa). Nó hỗ trợ hai khối tính chẵn lẻ độc lập trên mỗi dải. Cấu hình này yêu cầu ít nhất 6 ổ đĩa. Nó cung cấp mức độ chịu lỗi cao vì mỗi tập RAID 60 có thể chịu được lỗi kép của hai ổ đĩa mà không mất dữ liệu. Nó là một trong những cấu hình RAID phức tạp nhất và sau một lỗi ổ đĩa, nó mất thời gian lâu hơn để khôi phục thông tin tính chẵn lẻ so với giải pháp sao chép đĩa.

## Just a Bunch of Drives/Disks (JBOD)

JBOD (Viết tắt của "Just a Bunch Of Drives/Disks") là một dạng cấu hình lưu trữ dữ liệu cho nhiều ổ cứng không hỗ trợ các mảng RAID. 

JBOD được xác định là việc nối tiếp các ổ cứng riêng lẻ có dung lượng và thông số kỹ thuật khác nhau thành một ổ đĩa logic lớn. Quá trình kết hợp các ổ cứng này gọi là "Spanning".

Mỗi ổ cứng riêng trong JBOD có thể được truy cập như một ổ đĩa riêng biệt bởi máy tính chủ. 

JBOD không hỗ trợ tính toàn vẹn dữ liệu, kiểm tra tính chẵn lẻ hoặc striping như các cấu hình RAID.

Trong trường hợp một ổ cứng gặp sự cố, hệ thống không bị hỏng hoàn toàn và dữ liệu có sẵn trên các ổ cứng khác vẫn được bảo toàn.

## Host Protected Areas (HPA) and Device Configuration Overlays (DCO)

Ổ cứng và các phương tiện lưu trữ khác có thể có các khu vực ẩn như khu vực bảo vệ máy chủ (HPA) và khu vực chồng lắp cấu hình thiết bị (DCO).

### HPA

HPA được giới thiệu lần đầu trong tiêu chuẩn ATA-4, đó là một khu vực dành riêng trên ổ cứng hoặc ổ SSD không hiển thị cho hệ điều hành. Khu vực này lưu trữ dữ liệu mà người dùng, BIOS hoặc hệ điều hành không thể sửa đổi, thay đổi hoặc truy cập. Nó có thể lưu trữ thông tin về các tiện ích HDD, các công cụ chẩn đoán, mã boot sector, v.v. Ba lệnh ATA có thể giúp người dùng tạo và sử dụng HPA bao gồm:

- IDENTIFY DEVICE
- SET MAX ADDRESS
- READ NATIVE MAX ADDRESS

### DCO

DCO được giới thiệu lần đầu trong tiêu chuẩn ATA-6, đó là một khu vực ẩn bổ sung có sẵn trên ổ cứng hiện đại, cho phép nhà cung cấp hệ thống mua ổ cứng có kích thước khác nhau từ các nhà sản xuất khác nhau và cấu hình chúng để có cùng số lượng sector. DCO là một khu vực ẩn tránh sự nhìn thấy từ hệ thống, BIOS và người dùng. Nó có thể giúp người dùng bật/tắt các tính năng trên ổ cứng. Để xác định kích thước và các tính năng thực tế của ổ cứng, có thể sử dụng lệnh `DEVICE_CONFIGURATION_IDENTIFY`.

Những khu vực này có thể gây khó khăn cho người dùng vì kẻ xâm nhập có thể ẩn dữ liệu trong chúng mà không được sự nhận thức của các nhà điều tra. Kẻ xâm nhập sử dụng các công cụ cụ thể để sửa đổi và ghi dữ liệu vào HPA và DCO trên ổ cứng. Các nhà điều tra có thể sử dụng các công cụ như EnCase, TAFT (một công cụ pháp y ATA (IDE)), TSK, v.v. để phát hiện và tạo hình ảnh HPA và/hoặc DCOs.

## Network-Attached Storage (NAS)

Lưu trữ kết nối mạng (NAS) là một thiết bị lưu trữ tập trung trong đó một hoặc nhiều máy chủ bao gồm nhiều ổ cứng riêng biệt được cấu hình theo RAID để tăng tính dự phòng. Nó lưu trữ và chia sẻ dữ liệu giữa các máy khách khác nhau trên một mạng chung. Nó được hiện diện trên mạng khu vực (LAN) như một nút mạng độc lập, có thể truy cập vào các thiết bị lưu trữ chia sẻ thông qua kết nối Ethernet tiêu chuẩn và được xác định bởi địa chỉ IP duy nhất của nó.

Khi làm việc trong nhóm, NAS cho phép chia sẻ dữ liệu một cách hiệu quả giữa các máy khách khác nhau ở vị trí xa hoặc ở các múi giờ khác nhau. NAS kết nối với một bộ định tuyến hoặc switch không dây, giúp cho máy khách dễ dàng truy cập vào các tệp hoặc thư mục từ bất kỳ thiết bị nào kết nối vào mạng.

Dựa trên số lượng ổ đĩa, hỗ trợ ổ đĩa, dung lượng ổ đĩa và khả năng mở rộng, các thiết bị NAS được phân loại thành ba loại sau đây.

1. **NAS cao cấp hoặc doanh nghiệp:** NAS doanh nghiệp được sử dụng bởi các doanh nghiệp lưu trữ lượng lớn dữ liệu tệp, bao gồm hình ảnh máy ảo. Nó cũng cung cấp khả năng gom nhóm NAS.

2. **NAS trung thị trường:** Loại NAS này phục vụ các doanh nghiệp cần một vài trăm terabyte dữ liệu. Các thiết bị này không thể được gom nhóm.

3. **NAS giá thấp hoặc desktop:** Các thiết bị trong loại NAS này được sử dụng trong các doanh nghiệp nhỏ yêu cầu lưu trữ chia sẻ cục bộ.

## Storage Area Network (SAN)

Mạng lưu trữ khu vực (SAN) là một mạng riêng tốc độ cao được dành riêng để cung cấp quyền truy cập vào lưu trữ cấp khối được tập trung. SAN là một mạng riêng và không bị ảnh hưởng bởi giao thông mạng như các điểm nghẽn trong mạng LAN. Kiến trúc của nó cho phép các thiết bị lưu trữ trong mạng truy cập được bởi nhiều máy chủ như một ổ cứng được kết nối. Các máy chủ truy cập vào dữ liệu được chia sẻ trên nhiều mảng ổ đĩa như là một ổ cứng cục bộ.

SAN bao gồm các thành phần như các máy chủ được kết nối với nhau, nhiều switch và các thiết bị lưu trữ có thể được kết nối bằng công nghệ fiber channel (FC), hỗ trợ tốc độ truyền dữ liệu cao và truy cập dữ liệu không gián đoạn. Vì FC SAN đắt tiền và khó để xử lý, giao diện Internet Small Computer Systems Interface (iSCSI) dựa trên Ethernet, là một giải pháp rẻ hơn cho FC, được sử dụng trong các doanh nghiệp nhỏ và vừa.

iSCSI dựa trên Ethernet giảm những thách thức của công nghệ FC bằng cách đóng gói lệnh SCSI vào các gói IP không đòi hỏi kết nối FC.

### Lợi ích của FC SAN:
- Nó có khả năng mở rộng cao vì có thể thêm dung lượng lưu trữ khi cần thiết.
- Nó hỗ trợ tốc độ truyền dữ liệu cao nhưng đắt để sử dụng. Do đó, các công ty lớn thường ưa thích FC SAN.
- Lợi ích chính của nó bao gồm sao lưu không cần máy chủ, trong đó hệ thống cho phép thiết bị lưu trữ sao chép dữ liệu trực tiếp vào thiết bị sao lưu mà không cần can thiệp từ máy chủ.
- SAN cung cấp bảo vệ khỏi sự cố động, cho phép hoạt động mạng không gián đoạn, để dữ liệu vẫn có thể được truy cập bởi các thiết bị khác khi bất kỳ thành phần nào gặp sự cố hoặc máy chủ tạm thời ngừng hoạt động để bảo trì.
