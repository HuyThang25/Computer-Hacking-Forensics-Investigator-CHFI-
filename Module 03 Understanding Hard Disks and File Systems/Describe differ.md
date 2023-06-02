HDDs và SSDs lưu trữ dữ liệu trong máy tính. HDDs ghi dữ liệu bằng từ tính trên một đĩa xoay quay và chứ phần chuyển động; do đó, nó dễ bị hư hỏng về mặt vật lý. SSDs sử dụng chip bộ nhớ NAND (NOT AND) để lưu trữ dữ liệu và không chứ phần chuyển động.

## Hiểu về HDDs

HDD là một thiết bị lưu trữ dữ liệu không bay hơi (không bị mất khi tắt máy) được sử dụng trên hệ thống máy tính. Một ổ cứng lưu trữ dữ liệu sử dụng phương thức giống với file cabinet. Người dùng, khi cần có thể truy cập dữ liệu và chương trình. Khi máy tính lưu trữ chương trình hay dữ liệu, hệ thống sẽ sao chép dữ liệu từ HDD tới khu vự dễ bay hơi (RAM). Khi người dùng hay hệ thống thay đổi tệp, máy tính lưu tệp bằng cách thay thế tệp cũ thành một tệp mới. HDD ghi dữ liệu bằng từ tính vào ổ cứng.

HDD bao gồm nhữn đia quay, và tốc độ đọc/ ghi của nó phụ thuộc và tiếp độ quay của đĩa (số vòng trên phút - RPM). Đĩa quay càng nhanh thì tốc độ đọc/ghi của HDD càng nhanh.

HDDs dễ bị hỏng về mặt vật lý vì chứ những bộ phận chuyển động. Trong thời gian dài thì sẽ bị mòn và gây hỏng hóc cho ổ cứng.

HDDs khác nhau về các đo lường sau đây:

- 

## Hiểu về Tracks

Mọi đĩa trong HDDs có 2 mặt, và mỗi mặt lại được chia thành nhiều vòng gọi là tracks (đường tròn). Tracks lưu trữ tất cả thông tin trên ổ cứng, và các tracks trên phân vùng đĩa chứa các khối dữ liệu. Một ổ cứng tiêu chuẩn chứa lên đến 10.000 tracks trên mỗi đĩa. Đầu đọc và ghi dữ liệu the thứ tựtừ tâm đĩa ra ngoài vành. Kiểu sắp xếp dữ liệu này giúp dễ dàng truy cập vào bất cứ vùng nào của ổ cứng, đó là lý do tại sao nó được gọi là "random-access storage devices (thiết bị truy cập ngẫu nhiên)".

Mỗi trach bao gồm một lượng các đơn vị nhỏ hơn goi là sectors, và tất cat đĩa trong HDD có mật độ track giống nhau. Mật độ track đề cập đến số vòng trên một diện tích trên bề mặt đĩa; nó được tối ưu hoá nên mỗi cùng trên bề mặt đĩa sẽ có thể chứa tối đa số bit. Mật độ track do đó mà cũng quyết định khả năng lưu trữ ô cứng.

Đánh số track:

- Đánh số track trên ổ cứng bắt đầu từ 0 ở mép ngoài và di chuyển về phía trung tâm. Số lượng track trên ổ cứng phụ thuộc vào kích thước của đĩa.
- Các đầu đọc/ghi trên cả hai mặt của một đĩa quay trong ổ đĩa cứng (HDD) được gắn chặt và khóa chung với nhau trên một bộ cần có nhiều cánh tay.
- Các cần cánh tay di chuyển cùng nhau vào trong và ra ngoài để định vị tất cả các đầu đọc/ghi ở cùng một số track.
- Khi đề cập đến vị trí của một track trên HDD, thường sử dụng số xi-lanh (cylinder number) thay vì số track (track number).
- Cylinder là một tập các track bắt đầu tại vị trí giống nhau trên đĩa.

## Hiểu về sector

Các track chứ đơn vị nhỏ hơn gọi là sectors, và đó cũng là đơn vị nhỏ nhất trên đĩa. Sector là một thuật ngữ toán học chỉ một phần hình tròn hình thức hình chiếc bánh hoặc góc, và nó được bao quanh bởi chu vi của hình tròn và hai bán kính. 


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
