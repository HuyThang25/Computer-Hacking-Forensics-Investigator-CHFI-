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

Mail Transfer Agent (MTA) là một thành phần quan trọng trong quá trình truyền tin nhắn email. Đây chủ yếu là một loại máy chủ email nhận tin nhắn từ mail submission agent và giải mã thông tin tiêu đề để xem tin nhắn đang đi đến đâu. Sau khi xác định được, nó chuyển tin nhắn cho MTA máy chủ tiếp theo.

Tất cả các MTA máy chủ trò chuyện với nhau qua giao thức SMTP. Một số ví dụ về MTA bao gồm Sendmail, Exim và Postfix.

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



