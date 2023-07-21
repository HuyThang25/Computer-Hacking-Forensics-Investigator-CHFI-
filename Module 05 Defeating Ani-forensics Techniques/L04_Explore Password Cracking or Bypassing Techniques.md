Trong quá trình điều tra pháp y trên một máy tính của người bị tình nghi, việc truy cập vào các tài nguyên và ứng dụng được bảo vệ bằng mật khẩu là một thách thức lớn đối với các nhà điều tra pháp y. Để vượt qua bảo vệ mật khẩu cho các tài nguyên và ứng dụng trên hệ thống, các nhà điều tra pháp y có thể sử dụng các công cụ phá mật khẩu đặc biệt hoặc tuân thủ các quy trình được thiết lập theo các bước cụ thể.

Phần này thảo luận cách các nhà điều tra pháp y có thể bẻ khóa hoặc vượt qua bảo vệ bằng mật khẩu được đặt đối với tài khoản người dùng và ứng dụng/tài nguyên trên hệ thống đáng ngờ.

## Kỹ thuật chống pháp y: Bảo vệ mật khẩu

Mật khẩu là rất quan trọng, vì chúng là cánh cửa vào hầu hết các hệ thống máy tính. Bảo vệ mật khẩu giúp bảo vệ thông tin, mạng, ứng dụng, tập tin, văn bản, v.v. khỏi người dùng trái phép. Nhiều tổ chức và cá nhân không muốn người khác truy cập vào dữ liệu, tài nguyên và sản phẩm khác của họ, do đó sử dụng mật khẩu và thuật toán mã hóa mạnh mẽ như biện pháp bảo mật.

Các kẻ tấn công và xâm nhập sử dụng các kỹ thuật bảo vệ này để che giấu dữ liệu chứng cứ, ngăn việc phân tích đảo mã các ứng dụng, gây trở ngại cho việc trích xuất thông tin từ các thiết bị mạng và ngăn chặn truy cập vào hệ thống và ổ cứng. Điều này làm cho công việc của các nhà điều tra pháp y trở nên khó khăn. Mã hóa là một kỹ thuật được ưa chuộng để ngăn chặn phân tích pháp y, vì nó làm cho dữ liệu không đọc được mà không có khóa giải mã thích hợp. Tuy nhiên, trong một số trường hợp, vẫn có các công cụ và phương pháp để khôi phục mật khẩu.

Thiết bị tính toán có thể lưu trữ và truyền mật khẩu dưới các định dạng khác nhau, chẳng hạn như mật khẩu văn bản rõ ràng, mật khẩu đã được che dấu và mật khẩu băm. Chỉ có mật khẩu băm cần phải bị phá vỡ trong quá trình phá mã, trong khi các loại mật khẩu khác có thể hỗ trợ trong giai đoạn phá mã.

- **Mật khẩu dạng rõ ràng (Cleartext passwords)**
  - Mật khẩu được gửi và lưu trữ dưới dạng văn bản rõ ràng mà không có bất kỳ sự biến đổi nào.
  - Ví dụ: Registry của Windows lưu trữ mật khẩu đăng nhập tự động ở dạng văn bản rõ ràng trong registry, tại đường dẫn HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon.
  - Nhà điều tra có thể sử dụng các công cụ như Cain và Ettercap để bắt mật khẩu dạng rõ ràng khi chúng được gửi đi hoặc lưu trữ.

- **Mật khẩu được che dấu (Obfuscated passwords)**
  - Mật khẩu được lưu trữ hoặc truyền sau khi được biến đổi.
  - Khi quá trình biến đổi có thể được đảo ngược, mật khẩu trở nên không đọc được khi người dùng áp dụng một thuật toán và sau khi áp dụng thuật toán đảo ngược, mật khẩu trở lại dưới dạng văn bản rõ ràng.

- **Băm mật khẩu (Password hashes)**
  
  - Băm mật khẩu là một dấu hiệu của mật khẩu gốc được tạo ra bằng cách sử dụng một thuật toán một chiều. Mật khẩu được băm bằng các thuật toán băm (MD5, SHA, v.v.), không thể đảo ngược để khôi phục mật khẩu gốc.

Có ba kỹ thuật phổ biến để crack mật khẩu và chúng được thảo luận như sau:

- **Dictionary Attacks (Tấn công từ điển)**
  
	Trong dictionary attack, một tập tin từ điển được nạp vào ứng dụng crack mật khẩu để chạy chống lại các tài khoản người dùng. Một từ điển là một tệp văn bản chứa nhiều từ điển hoặc các kết hợp ký tự được định trước.

	Chương trình sử dụng mỗi từ có trong từ điển để tìm mật khẩu. Dictionary attack hữu ích hơn brute-force attack. Tuy nhiên, tấn công này không hoạt động với hệ thống sử dụng passphrases hoặc mật khẩu không nằm trong từ điển. Tấn công này có thể áp dụng trong hai tình huống sau:
	- Trong mã giải mật mã, nó giúp tìm ra khóa giải mã để thu được plaintext từ ciphertext.
	- Trong bảo mật máy tính, nó giúp tránh xác thực và truy cập vào máy tính bằng cách đoán mật khẩu.
	
	Các phương pháp để cải thiện hiệu quả của dictionary attack:
	- Sử dụng nhiều bộ từ điển, chẳng hạn như từ điển chuyên ngành và từ điển nước ngoài, có thể giúp thu hồi mật khẩu chính xác.
	- Sử dụng xử lý chuỗi; ví dụ, nếu từ điển chứa từ "system," hãy thử xử lý chuỗi và sử dụng "metsys" và các chuỗi khác.

- **Brute-Forcing Attacks (Tấn công brute-force)**

	Các thuật toán mật mã phải đủ phức tạp để ngăn chặn tấn công brute-force. RSA xác định tấn công brute-force là "[một] kỹ thuật cơ bản để thử từng khóa có thể có cho đến khi xác định được khóa chính xác."

	Tấn công brute-force trong cơ bản là một tấn công mã học được sử dụng để giải mã bất kỳ dữ liệu đã mã hóa nào (có thể được gọi là cipher). Nói cách khác, nó bao gồm thử tất cả các khóa có thể để khôi phục lại plaintext, đó là cơ sở để tạo ra một ciphertext cụ thể.

	Tấn công brute-force cần nhiều sức mạnh xử lý hơn so với các tấn công khác. Việc phát hiện các khóa hoặc plaintext một cách nhanh chóng trong tấn công brute-force dẫn đến việc phá vỡ cipher. Một cipher được coi là an toàn nếu không tồn tại phương pháp nào để phá vỡ nó ngoại trừ tấn công brute-force. Hầu hết các cipher thiếu bằng chứng toán học về tính bảo mật.
	
	Một số điều cần xem xét cho tấn công brute-force:
	- Đó là quá trình tốn thời gian.
	- Nó cuối cùng có thể theo dõi tất cả các mật khẩu.
	- Cuộc tấn công chống lại hash NT có độ khó cao hơn so với hash LM.

- **Rule-based Attack (Tấn công dựa trên quy tắc)**

	Kẻ tấn công sử dụng tấn công dựa trên quy tắc khi họ biết một số thông tin đáng tin cậy về mật khẩu như quy tắc đặt mật khẩu, thuật toán liên quan hoặc các chuỗi và ký tự được sử dụng trong quá trình tạo ra mật khẩu.

	Ví dụ, nếu kẻ tấn công biết rằng mật khẩu chứa một số có hai hoặc ba chữ số, thì họ sẽ sử dụng một số kỹ thuật cụ thể để trích xuất mật khẩu nhanh hơn. Bằng cách thu thập thông tin hữu ích, chẳng hạn như việc sử dụng số, độ dài của mật khẩu và các ký tự đặc biệt, kẻ tấn công có thể cải thiện hiệu suất của công cụ crack và giảm thời gian cần để thu hồi mật khẩu.


		
	 Kỹ thuật này bao gồm tấn công brute-force, dictionary và syllable (một tấn công syllable kết hợp cả tấn công brute-force và dictionary và thường được sử dụng để crack mật khẩu không bao gồm một từ thực tế mà là một hỗn hợp của các ký tự và âm tiết). Kẻ tấn công có thể sử dụng nhiều từ điển, kỹ thuật brute-force hoặc đơn giản là thử đoán mật khẩu.

### Sử dụng Rainbow Tables để Crack Hashed Passwords

Một cuộc tấn công màu cầu vồng là một hiện thực hóa của kỹ thuật trao đổi thời gian-bộ nhớ mã hóa dựa trên bảng màu cầu vồng.

Một bảng màu cầu vồng là một bảng tra cứu được sử dụng để phục hồi mật khẩu văn bản thuần túy từ mật văn bản đã được mã hóa. Nó bao gồm tất cả các kết hợp văn bản thuần túy có thể cho các mật khẩu đã được mã hóa được tạo bằng một thuật toán băm cụ thể. Bảng này chứa danh sách từ như các tệp từ điển và danh sách tấn công brute-force cùng với các giá trị băm đã tính toán của chúng.

Kẻ tấn công sử dụng bảng này để tìm kiếm mật khẩu và cố gắng khôi phục nó từ các giá trị băm mật khẩu. Kẻ tấn công tính toán băm cho một danh sách các mật khẩu có thể có và so sánh nó với bảng băm đã được tính toán trước đó (bảng màu cầu vồng) để tìm một kết quả khớp.

Việc khôi phục mật khẩu dễ dàng bằng cách so sánh các giá trị băm mật khẩu đã bắt được với các bảng băm được tính toán trước đó.



