HDDs và SSDs lưu trữ dữ liệu trong máy tính. HDDs ghi dữ liệu bằng từ tính trên một đĩa xoay quay và chứa phần chuyển động; do đó, nó dễ bị hư hỏng về mặt vật lý. SSDs sử dụng chip bộ nhớ NAND (NOT AND) để lưu trữ dữ liệu và không chứa phần chuyển động.

## Hiểu về HDDs

HDD là một thiết bị lưu trữ dữ liệu không bay hơi (không bị mất khi tắt máy) được sử dụng trên hệ thống máy tính. Một ổ cứng lưu trữ dữ liệu sử dụng phương thức giống với file cabinet. Người dùng, khi cần có thể truy cập dữ liệu và chương trình. Khi máy tính lưu trữ chương trình hay dữ liệu, hệ thống sẽ sao chép dữ liệu từ HDD tới khu vự dễ bay hơi (RAM). Khi người dùng hay hệ thống thay đổi tệp, máy tính lưu tệp bằng cách thay thế tệp cũ thành một tệp mới. HDD ghi dữ liệu bằng từ tính vào ổ cứng.

HDD bao gồm nhữn đĩa quay, và tốc độ đọc/ ghi của nó phụ thuộc và tiếp độ quay của đĩa (số vòng trên phút - RPM). Đĩa quay càng nhanh thì tốc độ đọc/ghi của HDD càng nhanh.

HDDs dễ bị hỏng về mặt vật lý vì chứa những bộ phận chuyển động. Trong thời gian dài thì sẽ bị mòn và gây hỏng hóc cho ổ cứng.

HDDs khác nhau về các đo lường sau đây:

- Capacity
- Interface used
- Speed in RPM
- Seek time
- Access time
- Transfer time

## Hiểu về Tracks

Mọi đĩa trong HDDs có 2 mặt, và mỗi mặt lại được chia thành nhiều vòng gọi là tracks (đường tròn). Tracks lưu trữ tất cả thông tin trên ổ cứng, và các tracks trên phân vùng đĩa chứa các khối dữ liệu. Một ổ cứng tiêu chuẩn chứa lên đến 10.000 tracks trên mỗi đĩa. Đầu đọc và ghi dữ liệu the thứ tựtừ tâm đĩa ra ngoài vành. Kiểu sắp xếp dữ liệu này giúp dễ dàng truy cập vào bất cứ vùng nào của ổ cứng, đó là lý do tại sao nó được gọi là "random-access storage devices (thiết bị truy cập ngẫu nhiên)".

Mỗi track bao gồm một lượng các đơn vị nhỏ hơn goi là sectors, và tất cả đĩa trong HDD có mật độ track giống nhau. Mật độ track đề cập đến số vòng trên một diện tích trên bề mặt đĩa; nó được tối ưu hoá nên mỗi vùng trên bề mặt đĩa sẽ có thể chứa tối đa số bit. Mật độ track do đó mà cũng quyết định khả năng lưu trữ ô cứng.

Đánh số track:

- Đánh số track trên ổ cứng bắt đầu từ 0 ở mép ngoài và di chuyển về phía trung tâm. Số lượng track trên ổ cứng phụ thuộc vào kích thước của đĩa.
- Các đầu đọc/ghi trên cả hai mặt của một đĩa quay trong ổ đĩa cứng (HDD) được gắn chặt và khóa chung với nhau trên một bộ cần có nhiều cánh tay.
- Các cần cánh tay di chuyển cùng nhau vào trong và ra ngoài để định vị tất cả các đầu đọc/ghi ở cùng một số track.
- Khi đề cập đến vị trí của một track trên HDD, thường sử dụng số xi-lanh (cylinder number) thay vì số track (track number).
- Cylinder là một tập các track bắt đầu tại vị trí giống nhau trên các đĩa.

## Hiểu về sector

Các track chứa đơn vị nhỏ hơn gọi là sectors, và đó cũng là đơn vị nhỏ nhất trên đĩa. Sector là một thuật ngữ toán học chỉ một phần hình tròn hình chiếc bánh hoặc góc, và nó được bao quanh bởi chu vi của hình tròn và hai bán kính. 


Mỗi sector thông thường lưu trữ 512 byte dữ liệu đối với HDDs và 2048 byte với CD-ROM và DVD-ROM. Tuy nhiên, các ổ cứng mới nhất sử dụng sector có kích thước 4096 byte (4 KB), với các byte bổ sung được sử dụng cho kiểm soát ổ đĩa nội bộ, thông tin hỗ trợ lưu trữ dữ liệu, phát hiện và sửa lỗi. Tất cả các sector nằm giữ hai đường tròn đồng tâm tạo thành một track. Các track kết hợp để tạo thành bề mặt của một đĩa cứng.

Thông tin một sector bao gồm:
- ID information: Phần này chứa số và vị trí của sector, giúp xác định các sector trên đĩa. Ngoài ra, nó cũng chứa thông tin trạng thái về sector.
- Synchronization fields (Trường đồng bộ hoá): Bộ điều khiển ổ đĩa sử dụng các trường này để điều khiển quá trình đọc dữ liệu.
- Data: Phần này chứa thông tin được lưu trữ trên sector.
- Error correction coding (ECC): Mã này đảm bảo tính toàn vẹn của dữ liệu.
- Gaps: là các khoảng trống được sử dụng để cung cấp thời gian cho bộ điều khiển tiếp tục quá trình đọc.

Những yếu tố này cùng nhau tạo thành phần trên đầu sector (sector overhead). Đây là một yếu tố quan trọng xác định thời gian truy cập dữ liệu. Khi ổ đĩa cứng sử dụng các bit để quản lý đĩa hoặc dữ liệu, kích thước phần trên đầu (overhead) cần được giảm thiểu để tối đa hóa hiệu suất. Một tệp trên đĩa lưu trữ dữ liệu theo chuỗi liên tiếp để tận dụng không gian một cách tối ưu, trong khi hệ thống phân bổ sector cho tệp dựa trên kích thước của nó. Nếu kích thước của một tệp là 600 byte, thì hệ thống sẽ phân bổ hai sector, mỗi sector có kích thước 512 byte. Số track và số sector đề cập đến địa chỉ của bất kỳ dữ liệu nào trên ổ đĩa cứng.

Xác định đỉa chỉ sector:

- Cylinders, heads, và sector (CHS) xác định địa chỉ của từng sector riêng lẻ trên đĩa. (có thể hiểu là Cylinders để xác định tập các track có cùng một khoảng các với tâm của các đĩa, head giúp xác định đĩa nào, sevtor là xác định đoạn dữ liệu trên track)
- Khi một đĩa cứng được định dạng, nó được chia thành các track và sector.
- Ví dụ, đĩa cứng đã được định dạng có thể chứa 50 track, mỗi track được chia thành 10 sector.
- Số track và số sector được sử dụng bởi hệ điều hành và ổ đĩa để xác định thông tin được lưu trữ.

## Hiểu về 4K Sectors:

Ổ đĩa cứng mới sử dụng các sector advanced-format có kích thước 4096 byte (4 KB hoặc 4K). Định dạng này sử dụng bề mặt lưu trữ trên đĩa hiệu quả bằng cách kết hợp tám sector 512 byte thành một sector duy nhất (4096 byte). Cấu trúc của sector 4K giữ nguyên các yếu tố thiết kế của sector 512 byte, với các khu vực bắt đầu và mã sửa lỗi (ECC) được đại diện bởi các ký tự định danh và đồng bộ hóa, tương ứng. Công nghệ sector 4K loại bỏ các khu vực tiêu đề dư thừa giữa các sector.

## Mật độ dữ liệu trên ổ cứng:

Ổ cứng lưu trữ dữ liệu bằng phương pháp ghi dữ liệu theo phương pháp zoned bit recording, còn được gọi là multiple zone recording. Trong kỹ thuật này, các track hình thành một tập hợp các vùng (zone) tùy thuộc vào khoảng cách của chúng đến trung tâm đĩa, và các track ở bên ngoài có nhiều sector hơn so với các track ở bên trong. Điều này cho phép ổ đĩa lưu trữ nhiều bit hơn trong mỗi track ở vùng bên ngoài so với vùng ở phần trong nhất, giúp đạt được dung lượng dữ liệu tổng cộng cao.

Dưới đây là một số thuật ngữ liên quan đến mật độ dữ liệu trên đĩa cứng:

- Track density (Mật độ track): là thuật ngữ chỉ khối lượng không gian được yêu cầu bởi một số lượng track cụ thể trên một đĩa cứng. Đĩa cứng với mật độ track cao hơn có khả năng lưu trữ nhiều thông tin hơn và cung cấp hiệu suất tốt hơn.
- Areal density (Mật độ điện tích): là thuật ngữ chỉ số lượng bit trên mỗi inch vuông trên một đĩa cứng. Nó đại diện cho lượng dữ liệu mà một đĩa cứng có thể chứa.
- Bit density (Mật độ bit): là thuật ngữ chỉ số lượng bit mà một đơn vị độ dài của track có thể chứa.

## Địa chỉ hoá dữ liệu CHS (Cylinder-Head-Sector) và tính toán dung lượng của đĩa cứng:

Quá trình địa chỉ hóa dữ liệu trên đĩa cứng (Hard-disk data addressing) là kỹ thuật gán địa chỉ cho các khối dữ liệu vật lý trên đĩa cứng.

CHS (Cylinder-Head-Sector) là một quá trình xác định các sector riêng lẻ trên đĩa cứng dựa vào vị trí của chúng trên một track, và các số head và cylinder xác định các track này. Nó liên kết thông tin trên ổ cứng theo các thông số như head (mặt đĩa), cylinder (bán kính), và sector (vị trí góc).

Ví dụ về tính toán dung lượng đĩa: Một ổ đĩa cứng có 16.384 cylinder, 80 head và 63 sector trên mỗi track. Giả sử mỗi sector có 512 byte. Dung lượng của ổ đĩa là bao nhiêu?

Đáp án:
Tổng kích thước của đĩa = Số cylinder * Số head * Số sector trên mỗi track * 512 byte trên mỗi sector
Tổng kích thước của đĩa = (16.384 cylinder) * (80 head) * (63 sector / track) * (512 byte / sector)
= 42.278.584.320 byte
## Đo lường hiệu suất của ổ cứng 

Đo hiệu suất ổ đĩa cứng bao gồm tính toán hai đặc điểm của nó là: thời gian truy cập và tốc độ truyền dữ liệu.

### Thời gian truy cập

Đây là thời gian mà ổ đĩa cần để khởi động việc truyền dữ liệu và phụ thuộc vào tính cơ khí của các đĩa quay và đầu đọc di chuyển. Các thành phần sau được cộng vào để tính toán thời gian truy cập:

- Thời gian tìm kiếm (Seek time): Đây là thời gian mà bộ điều khiển ổ đĩa cứng cần để tìm một phần dữ liệu cụ thể. Khi đọc hoặc ghi dữ liệu, các đầu đọc đĩa di chuyển đến vị trí chính xác thông qua quá trình tìm kiếm. Thời gian cần để di chuyển các đầu đọc/ghi đĩa từ một điểm đến điểm khác trên đĩa gọi là thời gian tìm kiếm. Thời gian tìm kiếm thông thường nằm trong khoảng từ 10 đến 20 ms, với ổ đĩa cứng phổ biến trên máy tính để bàn có thời gian tìm kiếm khoảng 9 ms.
- Độ trễ quay (Rotational latency): Đây là thời gian trễ do việc quay của đĩa để đến vị trí đĩa được chọn dưới các đầu đọc/ghi. Độ trễ quay trung bình bằng một nửa thời gian mà đĩa cần để hoàn thành một vòng quay. Thuật ngữ này chỉ áp dụng cho các thiết bị lưu trữ quay như HDD và đĩa mềm, không áp dụng cho băng ghi.

### Tốc độ truyền dữ liệu

Tốc độ truyền dữ liệu của ổ đĩa được biểu thị bởi tốc độ nội bộ (internal rate), đó là tốc độ truyền dữ liệu giữa bề mặt đĩa và bộ điều khiển ổ đĩa, cũng như tốc độ ngoại vi (external rate), hay tốc độ truyền dữ liệu giữa bộ điều khiển ổ đĩa và hệ thống máy chủ. Tốc độ truyền của máy chủ hoặc tốc độ truyền dữ liệu là tốc độ mà máy tính chủ có thể truyền dữ liệu từ giao diện Integrated Drive Electronics (IDE)/Enhanced IDE (EIDE) hoặc giao diện Small Computer System Interface (SCSI) tới CPU.

- Tốc độ truyền dữ liệu tại vùng trong của đĩa dao động từ 44,2 MB/giây đến 74,5 MB/giây.
- Tốc độ truyền dữ liệu tại vùng ngoài dao động từ 74,0 MB/giây đến 111,4 MB/giây.

## Hiểu về Solid-State Drive (SSD)

SSD là một thiết bị lưu trữ dữ liệu điện tử thực hiện công nghệ bộ nhớ bán dẫn để lưu trữ dữ liệu theo cách tương tự như ổ đĩa cứng (HDD). Trong điện tử, thuật ngữ "bán dẫn" ám chỉ một mạch điện tử được xây dựng hoàn toàn bằng bán dẫn. SSD sử dụng hai loại bộ nhớ sau đây:

- NAND-based SSDs: Các SSD này sử dụng vi mạch bộ nhớ NAND bán dẫn để lưu trữ dữ liệu. Bộ nhớ NAND là bộ nhớ không bay hơi và giữ lại dữ liệu ngay cả khi không có nguồn điện. Do đó, dữ liệu trong các vi mạch này ở trạng thái không bay hơi và không cần bất kỳ bộ phận chuyển động nào. Bộ nhớ NAND được phát triển chủ yếu để giảm chi phí lưu trữ dữ liệu trên mỗi bit. Tuy nhiên, nó vẫn đắt hơn bộ nhớ quang và ổ đĩa cứng. Bộ nhớ dựa trên NAND được sử dụng rộng rãi ngày nay trong các thiết bị di động, máy ảnh kỹ thuật số, máy nghe nhạc MP3, v.v. Nó chỉ cho phép một số lượng hữu hạn lần ghi trên suốt tuổi thọ của thiết bị.

- Volatile RAM-based SSDs: SSD dựa trên bộ nhớ bay hơi như RAM động (DRAM) được sử dụng khi các ứng dụng đòi hỏi truy cập dữ liệu nhanh. Các SSD này bao gồm một pin nạp được bên trong hoặc một bộ chuyển đổi AC/DC bên ngoài, cũng như bộ nhớ lưu trữ dự phòng. Dữ liệu được lưu trữ trong DRAM trong quá trình truy cập dữ liệu và được lưu trữ trong bộ nhớ dự phòng trong trường hợp xảy ra cúp điện.

### Các lợi ích của SSD

Ba lợi ích chính của SSD so với ổ đĩa cứng từ tính là như sau:

- Truy cập dữ liệu nhanh hơn
- Tiêu thụ điện năng thấp hơn
- Độ tin cậy cao hơn
### Thành phần của SSD:

1. Bộ nhớ NAND flash: Nó sử dụng công nghệ lưu trữ không bay hơi để lưu trữ dữ liệu và bao gồm các transistor cổng lơ lửng không cần nguồn điện để giữ lại dữ liệu.
2. Bộ điều khiển: Đây là một bộ xử lý tích hợp giúp kết nối giữa các thành phần bộ nhớ flash và hệ thống thông qua việc thực thi phần mềm cấp firmware.
3. Bộ nhớ DRAM: Đây là một bộ nhớ bay hơi và yêu cầu nguồn điện để giữ lại dữ liệu. DRAM được sử dụng trong ổ đĩa SSD để tăng hiệu suất đọc/ghi.
4. Giao diện máy chủ: Dựa trên yêu cầu về hiệu suất, các giao diện máy chủ khác nhau được sử dụng trong các ổ đĩa SSD. Các giao diện máy chủ SSD thông dụng bao gồm SATA (Serial Advanced Technology Attachment), PCIe (Peripheral Component Interconnect Express) và SCSI.

### Giao diện Disk

Ổ đĩa lưu trữ kết nối với máy tính thông qua một giao diện. Có các loại giao diện khác nhau, bao gồm IDE, SATA, PCIe và SCSI.

#### ATA/PATA (IDE/EIDE)

IDE là một giao diện điện tử tiêu chuẩn được sử dụng giữa đường dẫn dữ liệu hoặc bus trên bo mạch chủ máy tính và các thiết bị lưu trữ của máy tính, chẳng hạn như ổ đĩa cứng, ổ đĩa SSD và ổ CD-ROM/DVD. Tiêu chuẩn bus 16-bit Industry Standard Architecture (ISA) của IBM PC là cơ sở cho giao diện IDE, cung cấp khả năng kết nối trong các máy tính sử dụng các tiêu chuẩn bus khác. IDE chính thức của Viện Tiêu chuẩn Quốc gia Mỹ (ANSI) là Advanced Technology Attachment (ATA).

#### Parallel ATA

Parallel ATA (PATA), dựa trên công nghệ truyền tín hiệu song song, cung cấp một bộ điều khiển trên chính ổ đĩa, loại bỏ nhu cầu sử dụng thẻ chuyển đổi riêng biệt. Tiêu chuẩn PATA chỉ cho phép độ dài cáp lên đến 46 cm (18 inch).

PATA có các đặc điểm sau:

- Tương đối rẻ
- Dễ cấu hình
- Cho phép bộ nhớ cache kiểm tra trước (look-ahead caching)

#### Enhanced Integrated Drive Electronics (EIDE)

Hầu hết các máy tính hiện nay được bán sử dụng một phiên bản nâng cao của IDE được gọi là Enhanced Integrated Drive Electronics (EIDE). Các ổ đĩa IDE kết nối với máy tính bằng cách sử dụng một thẻ chuyển đổi IDE. Bộ điều khiển IDE trên các máy tính hiện đại là một tính năng tích hợp trên bo mạch chủ. EIDE là một sự mở rộng của giao diện IDE hỗ trợ các tiêu chuẩn ATA-2 và ATA Packet Interface (ATAPI). Bo mạch chủ chứa hai loại cổng EIDE. Một cổng kết nối hai ổ đĩa, bao gồm cáp 80 dây cho ổ cứng nhanh và một cáp dẹt 40 chân cho CD-ROM/DVD-ROM. Enhanced hoặc Expanded IDE là một giao diện điện tử tiêu chuẩn kết nối bo mạch chủ máy tính với các ổ đĩa lưu trữ của nó. EIDE có thể xử lý ổ cứng lớn hơn 528 Mbyte, cho phép truy cập nhanh đến ổ cứng và cung cấp hỗ trợ cho việc truy cập bộ nhớ trực tiếp (DMA) và các ổ đĩa bổ sung như thiết bị băng và ổ CD-ROM. Khi nâng cấp hệ thống máy tính với một ổ cứng lớn hơn, bộ điều khiển EIDE được chèn vào khe thẻ hệ thống. EIDE truy cập vào các ổ cứng lớn hơn 528 Mbyte bằng cách sử dụng một địa chỉ khối logic (LBA) 28 bit để chỉ định các vị trí thực tế của đầu đọc, sector và vòng quay của dữ liệu đĩa. LBA 28 bit cung cấp đủ thông tin để xác định các sector duy nhất trong một thiết bị lưu trữ với dung lượng 8,4 GB.

#### Serial ATA

Serial ATA (SATA) cung cấp một kênh từ điểm tới điểm giữa bo mạch chủ và ổ đĩa. Cáp trong SATA có độ dài ngắn hơn so với cáp trong PATA. Nó sử dụng cáp bọc bốn dây có độ dài tối đa 1 mét. Cáp SATA linh hoạt hơn, mỏng hơn và nhẹ hơn so với cáp dẹt yêu cầu cho ổ cứng PATA truyền thống.

SATA có các đặc điểm sau:

- Tốc độ hoạt động cao
- Dễ kết nối với các thiết bị lưu trữ
- Dễ cấu hình

Truyền dữ liệu với tốc độ 1,5 Gbps (SATA phiên bản 1.0) và 6 Gbps (SATA phiên bản 3)
Kết nối ổ đĩa và bo mạch chủ thông qua một kênh điểm tới điểm của SATA dựa trên công nghệ truyền tín hiệu tuần tự. Công nghệ này cho phép truyền dữ liệu với tốc độ khoảng 1,5 Gbps trong chế độ kênh bán đồng bộ.

#### SCSI (Small Computer System Interface)

SCSI là một tập hợp các giao diện điện tử tiêu chuẩn ANSI cho phép máy tính cá nhân giao tiếp với phần cứng ngoại vi như ổ đĩa cứng, ổ đĩa băng, ổ đĩa CD-ROM, máy in và máy quét. Được sử dụng ban đầu bởi Apple Computer, Inc. và vẫn được sử dụng trong các máy tính Macintosh, các bộ SCSI hiện tại là các giao diện song song. Các cổng SCSI vẫn có sẵn như một tính năng tích hợp trong các máy tính PC hiện nay và được hỗ trợ bởi tất cả các hệ điều hành chính.

Ngoài việc cung cấp tốc độ truyền dữ liệu nhanh hơn, SCSI còn linh hoạt hơn các giao diện truyền dữ liệu song song trước đây. SCSI cho phép kết nối đến 7 hoặc 15 thiết bị (tùy thuộc vào chiều rộng của bus) với một cổng SCSI duy nhất theo cách dạng chuỗi nối. Điều này cho phép một bo mạch hoặc thẻ điện tử có thể chứa tất cả các thiết bị ngoại vi, thay vì phải có một thẻ riêng cho mỗi thiết bị, làm cho nó trở thành một giao diện lý tưởng để sử dụng với máy tính xách tay và máy tính gọn nhẹ. Một bộ chuyển đổi máy chủ duy nhất, dưới dạng một thẻ PC, có thể phục vụ làm giao diện SCSI cho một máy tính xách tay, giải phóng các cổng song song và cổng tuần tự để sử dụng với một modem và máy in ngoại vi bên ngoài và cho phép sử dụng các thiết bị khác.

#### Serial Attached SCSI (SAS)

Serial Attached SCSI (SAS) là một giao thức nối tiếp điểm-điểm dạng chuỗi được sử dụng để xử lý luồng dữ liệu giữa các thiết bị lưu trữ máy tính như ổ đĩa cứng và ổ đĩa băng. Nó là sự kế thừa của SCSI song song và sử dụng bộ lệnh SCSI tiêu chuẩn.

SAS được chọn thay thế SCSI vì tính linh hoạt và các tính năng hữu ích khác, như được giải thích dưới đây:
- Trong khi tiêu chuẩn SCSI song song mới nhất chỉ hỗ trợ tối đa 16 thiết bị, SAS sử dụng expanders và có thể hỗ trợ lên đến 65.535 thiết bị.
- SAS không bị ảnh hưởng bởi các vấn đề như kết thúc và độ lệch đồng hồ.
- Vì SAS là công nghệ điểm-điểm, nó không bị ảnh hưởng bởi các vấn đề cạnh tranh tài nguyên, mà thường gặp trong SCSI song song.
- Ổ đĩa SAS mang lại hiệu suất, khả năng mở rộng và độ tin cậy tốt hơn trong các ứng dụng lưu trữ so với ổ đĩa SCSI, và chúng có thể hoạt động trong môi trường mà ổ đĩa SCSI không thể làm được.

### PCIe SSD

PCIe SSD là một thẻ mở rộng chuỗi nối tiếp tốc độ cao tích hợp bộ nhớ flash trực tiếp vào bo mạch chủ. Các thiết bị này kết nối với máy chủ thông qua một liên kết nối tiếp riêng biệt của chúng bằng cách loại bỏ việc chia sẻ một bus, giảm độ trễ và tăng tốc độ truyền dữ liệu giữa máy chủ và lưu trữ. Tốc độ truyền dữ liệu được xác định bởi số làn PCIe trên mỗi ổ SSD. PCIe 5.0 được ra mắt vào ngày 29 tháng 5 năm 2019 và có băng thông là 32 GT/s (~128 GB/s), làm cho nó lý tưởng cho các ứng dụng như trí tuệ nhân tạo, học máy, game, tính toán hình ảnh, lưu trữ và mạng.

### Giao thức lưu trữ SSD: NVMe SSD

Non-Volatile Memory Express (NVMe) là một giao thức lưu trữ được phát triển cho bộ nhớ flash NAND và SSD hiệu năng cao sử dụng công nghệ khe cắm thẻ PCIe. Với hệ thống hàng đợi song song của nó, NVMe vượt qua những hạn chế của SATA và các tùy chọn lưu trữ SSD khác. Nó có thể xử lý các công việc nặng, giảm thiểu độ trễ và cung cấp hỗ trợ hàng đợi tốt hơn so với SSD SATA/Advanced Host Controller Interface (AHCI), đáng kể cải thiện hiệu suất và giảm thiểu hạn chế của CPU. Hiện tại, NVMe hỗ trợ ba kiểu dáng: thẻ PCIe gắn ngoài, ổ SSD M.2 và ổ SSD U.2 kích thước 2.5-inch.
