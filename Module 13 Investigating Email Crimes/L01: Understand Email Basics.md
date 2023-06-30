Hiện nay, ngày càng có nhiều doanh nghiệp sử dụng email như phương tiện giao tiếp chính. Sự phụ thuộc ngày càng tăng vào email cũng đã gây ra tội phạm qua email. Do đó, nhà điều tra pháp y cần phải hiểu đầy đủ về hệ thống email và kiến trúc bên trong, cùng với các thành phần hoạt động cùng nhau để chuyển gửi một email từ người gửi đến người nhận. Phần này sẽ trình bày về các nguyên tắc cơ bản của một hệ thống email.


## Giới thiệu về Hệ thống Email

Email là viết tắt của "thư điện tử" (electronic mail), được sử dụng để gửi, nhận và lưu trữ tin nhắn qua hệ thống truyền thông điện tử. Với sự phụ thuộc ngày càng cao vào công nghệ, email đã trở thành một trong những phương tiện giao tiếp phổ biến nhất.

Một hệ thống email hoạt động dựa trên kiến trúc cơ bản khách hàng-máy chủ. Nó cho phép khách hàng gửi/nhận thư qua các máy chủ email tương tác với nhau. Hầu hết các hệ thống email có trình soạn thảo văn bản với các tùy chọn định dạng cơ bản, cho phép khách hàng soạn tin nhắn văn bản và gửi đến một hoặc nhiều người nhận. Sau khi tin nhắn được gửi đi, nó đi qua nhiều máy chủ và được lưu trữ trong hòm thư của người nhận cho đến khi người đó truy cập lấy tin nhắn.

## Các thành phần liên quan trong giao tiếp qua email

Có một số thành phần của giao tiếp qua email đóng vai trò cụ thể khi một tin nhắn email được truyền từ người gửi đến người nhận.

### Mail User Agent

Còn được gọi là email client, Mail User Agent (MUA) là một ứng dụng desktop dùng để đọc, gửi và tổ chức các email. Nó cung cấp giao diện cho người dùng nhận, soạn, hoặc gửi email từ các địa chỉ email đã được cấu hình.

Người dùng cần thiết lập và cấu hình địa chỉ email trước khi sử dụng email client. Cấu hình bao gồm việc cung cấp email ID, mật khẩu, địa chỉ Post Office Protocol version 3 (POP3)/Internet Message Access Protocol (IMAP) và Simple Mail Transfer Protocol (SMTP), số cổng và các tùy chọn liên quan khác. Có nhiều email client độc lập và dựa trên web như Claws Mail, Thunderbird, Mailbird, Zimbra Desktop, Gmail và Outlook.com. Email client chỉ hoạt động khi người dùng chạy nó.

### Mail Transfer Agent

Mail Transfer Agent (MTA) là một thành phần quan trọng trong quá trình truyền tin nhắn email. Đây chủ yếu là một loại máy chủ email nhận tin nhắn từ mail submission agent và giải mã thông tin tiêu đề để xem tin nhắn đang đi đến đâu. Sau khi xác định được, nó chuyển tin nhắn cho máy chủ MTA tiếp theo.

Tất cả các máy chủ MTA trò chuyện với nhau qua giao thức SMTP. Một số ví dụ về MTA bao gồm Sendmail, Exim và Postfix.

### Mail Delivery Agent

Mail Delivery Agent (MDA) là máy chủ nhận tin nhắn email từ MTA cuối cùng và lưu trữ nó trong hòm thư của người nhận. Dovecot là một ví dụ về MDA.

### SMTP Server

SMTP là một máy chủ email đi ra cho phép người dùng gửi email đến một địa chỉ email hợp lệ. Người dùng không thể sử dụng máy chủ SMTP để nhận email; tuy nhiên, phối hợp với giao thức Post Office Protocol (POP) hoặc IMAP, họ có thể sử dụng SMTP để nhận email với cấu hình đúng.

Bất kỳ máy chủ SMTP nào đều được máy khách email của người dùng gán địa chỉ theo định dạng sau: smtp.serveraddress.com (ví dụ, địa chỉ máy chủ SMTP của Gmail sẽ là smtp.gmail.com).

Khi người dùng gửi một email đến một người nhận cụ thể, nó trước tiên đến máy chủ SMTP xử lý tin nhắn để xác định địa chỉ của người nhận và sau đó chuyển tiếp nó đến máy chủ cụ thể đó. Tất cả các máy chủ SMTP thông thường lắng nghe cổng 25. Tuy nhiên, các máy chủ SMTP đi ra sử dụng cổng 587 cho kết nối an ninh lớp vận chuyển và cổng 465 cho kết nối secure sockets layer (SSL).

### POP3 Sever

POP3 là một giao thức đơn giản để truy xuất email từ máy chủ email. Khi máy chủ POP3 nhận được email, chúng được lưu trữ trên máy chủ cho đến khi người dùng yêu cầu.

Máy chủ POP3 không cho phép khái niệm về thư mục; nó coi hòm thư trên máy chủ là kho lưu trữ duy nhất của nó. Khi người dùng kết nối đến máy chủ thư để khôi phục thư của mình bằng cách sử dụng email client, thư sẽ được tự động tải xuống từ máy chủ thư vào ổ cứng của người dùng và không còn được lưu trữ trên máy chủ trừ khi người dùng chỉ định để giữ một bản sao của nó.

Máy chủ POP3 có thể hiểu các lệnh đơn giản như sau:
- USER - nhập ID người dùng
- PASS - nhập mật khẩu
- QUIT - thoát khỏi máy chủ POP3
- LIST - liệt kê các tin nhắn và kích thước của chúng
- RETR - truy xuất một tin nhắn, dựa trên số thứ tự tin nhắn
- DELETE - xóa một tin nhắn, dựa trên số thứ tự tin nhắn

Do máy chủ POP3 thực hiện việc tải xuống thư từ máy chủ vào hệ thống, người dùng có thể đọc thư ngay cả khi không có kết nối Internet. Tuy nhiên, vì thư được lưu trữ trên ổ cứng, người dùng không thể truy cập chúng từ các máy từ xa.

### IMAP Server

Máy chủ IMAP tương tự như máy chủ POP3. Giống như POP3, IMAP xử lý email đến. Theo mặc định, máy chủ IMAP lắng nghe cổng 143 và IMAPS (IMAP qua SSL) lắng nghe trên cổng 993.

IMAP lưu trữ email trên máy chủ thư và cho phép người dùng xem và làm việc trên email của họ, như thể các email được lưu trữ trong hệ thống cục bộ của họ. Điều này cho phép người dùng tổ chức tất cả các email dựa trên yêu cầu của họ. Khác với POP3, IMAP không di chuyển thư từ máy chủ đến hòm thư của người dùng.

Nó hoạt động như một máy chủ từ xa lưu trữ tất cả các email của người dùng trên máy chủ thư. IMAP cho phép các email client truy xuất các phần mở rộng email Internet đa mục đích (MIME) dưới dạng toàn bộ một tin nhắn hoặc nhiều phần, cho phép các client chỉ truy xuất phần văn bản của email mà không cần tải xuống tệp đính kèm. Giao thức này lưu trữ một bản sao của tất cả các email trên máy chủ ngay cả khi người dùng tải xuống chúng vào hệ thống của mình. Do đó, người dùng có thể truy cập chúng từ bất kỳ hệ thống hoặc thiết bị tính toán nào.

## How Email Communication Works

Khi người dùng gửi một email tới người nhận, nó đi qua một số giai đoạn trước khi đến được đích. Dưới đây là một kịch bản để mô tả các giai đoạn này:

Giả sử có một người dùng email tên là Bob muốn gửi một email tới người dùng email khác có tên là Alice. Bob soạn thảo một tin nhắn bằng cách sử dụng ứng dụng email hoặc MUA (Mail User Agent) hoặc một dịch vụ email trực tuyến như Yahoo!, sau đó Bob chỉ định địa chỉ email của Alice và nhấn nút gửi.

Tin nhắn email được nhận bởi một máy chủ MTA (Mail Transfer Agent) thông qua giao thức SMTP (Simple Mail Transfer Protocol) mà giải mã thông tin tiêu đề và tìm kiếm tên miền trong địa chỉ email của Alice. Phương pháp này cho phép máy chủ MTA xác định máy chủ email đích và chuyển tiếp tin nhắn tới MTA tương ứng.

Mỗi khi một máy chủ MTA nhận được một tin nhắn trong quá trình gửi mail, nó sẽ sửa đổi thông tin tiêu đề. Khi đến máy chủ MTA cuối cùng, tin nhắn sẽ được chuyển tiếp tới MDA (Mail Delivery Agent), nơi nó được lưu trữ trong hộp thư của Alice.

Sau đó, MUA của Alice sẽ lấy tin nhắn bằng cách sử dụng giao thức POP3 (Post Office Protocol version 3) hoặc IMAP (Internet Message Access Protocol), và Alice cuối cùng có thể đọc tin nhắn.

Hiểu về các phần của một tin nhắn email:

Tin nhắn email là một văn bản ngắn gọn và không chính thức được gửi hoặc nhận qua mạng. Tin nhắn email là các văn bản đơn giản có thể bao gồm cả tệp đính kèm như hình ảnh và bảng tính. Có thể có nhiều người nhận nhận được tin nhắn email cùng một lúc.
Hiện nay, RFC 5322 định nghĩa định dạng tin nhắn email trên Internet và RFC 2045 đến RFC 2049 định nghĩa đính kèm nội dung đa phương tiện - cùng với nhau gọi là multi-
purpose Internet mail extensions (MIME).

Tin nhắn email bao gồm ba phần chính:

1. Tiêu đề tin nhắn:

Phần tiêu đề bao gồm các trường thông tin sau:
- To: Chỉ định người nhận tin nhắn. Lưu ý rằng trường "To" không luôn chứa địa chỉ của người nhận.
- Cc: Viết tắt của "carbon copy". Trường này chỉ định các người nhận bổ sung ngoài những người được liệt kê trong trường "To". Sự khác biệt giữa "To" và "Cc" là ý nghĩa; một số chương trình email xử lý chúng khác nhau khi tạo các phản hồi.
- Bcc: Viết tắt của "blind carbon copy". Trường này gửi bản sao email cho những người không muốn nhận phản hồi hoặc xuất hiện trong tiêu đề. Bcc được sử dụng phổ biến bởi những người gửi thư rác vì nó làm bối rối nhiều người dùng không có kinh nghiệm khi nhận một email không có địa chỉ của họ hoặc không dành cho họ.
- From: Chỉ định người gửi tin nhắn.
- Reply-To: Chỉ định địa chỉ để gửi phản hồi. Mặc dù trường này có nhiều ứng dụng hợp lệ, nhưng nó cũng được sử dụng rộng rãi bởi người gửi thư rác để tránh chỉ trích. Thỉnh thoảng, một kẻ gửi thư rác chuyên nghiệp sẽ yêu cầu nhận phản hồi qua email và sử dụng trường "Reply-To" để thu thập chúng, nhưng thường thì địa chỉ được chỉ định trong thư rác là không hợp lệ hoặc thuộc về một nạn nhân vô tội.
- Sender: Không phổ biến trong email (thường sử dụng "X-Sender" thay thế) nhưng đôi khi xuất hiện, đặc biệt trong các bản sao của bài đăng Usenet. Nó nên xác định người gửi; trong trường hợp của các bài đăng Usenet, nó là một thông tin xác đáng tin cậy hơn so với dòng "From".
- Subject: Một trường hoàn toàn tự do được người gửi chỉ định để mô tả chủ đề của tin nhắn.
- Date: Chỉ định ngày tạo và gửi email. Nếu máy tính của người gửi bỏ qua trường này, một máy chủ thư hoặc máy tính khác có thể thêm vào, thậm chí trong quá trình truyền tải.
- MIME-Version: Là một tiêu đề MIME khác phản ánh phiên bản giao thức MIME.
- Priority: Là một tiêu đề tự do xác định mức độ ưu tiên của thư. Hầu hết phần mềm email bỏ qua nó. Người gửi thư rác thường sử dụng nó trong một cố gắng để đảm bảo thư của họ được đọc.

2. Nội dung tin nhắn:

Phần nội dung của email chứa thông điệp và đôi khi bao gồm một khối chữ ký ở cuối. Một dòng trống tách biệt giữa tiêu đề và nội dung. Trong một email, phần nội dung hoặc văn bản luôn nằm sau các dòng tiêu đề.

Thân email là thông điệp chính của email chứa văn bản, hình ảnh, liên kết và dữ liệu khác (như các tệp đính kèm). Thân email hiển thị các tệp đính kèm riêng lẻ xuất hiện cùng với văn bản. Tiêu chuẩn email trên Internet không đặt ra bất kỳ giới hạn nào cho kích thước của thân email. Tuy nhiên, các máy chủ thư riêng lẻ có giới hạn kích thước tin nhắn.

3. Signature:

Email signature là một số thông tin bổ sung nhỏ được đính kèm ở cuối tin nhắn email, bao gồm tên và thông tin liên hệ của người gửi email. Nó có thể chứa văn bản đơn thuần hoặc hình ảnh.

