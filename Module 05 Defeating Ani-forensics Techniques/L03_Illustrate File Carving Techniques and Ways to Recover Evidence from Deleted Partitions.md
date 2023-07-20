File carving là một kỹ thuật được sử dụng để khôi phục các tệp tin đã bị xóa/mất và các mảnh của tệp tin từ ổ đĩa cứng khi siêu dữ liệu hệ thống tệp tin bị mất. Bằng cách cho phép nhà điều tra pháp y khôi phục các tệp tin đã bị xóa/mất từ ổ đĩa cứng, file carving giúp trích xuất những hiện vật quan trọng liên quan đến một vụ án tội phạm mạng để tiếp tục kiểm tra kỹ hơn. Người gây án cũng có thể cố gắng xóa toàn bộ phân vùng từ ổ đĩa cứng và sau đó hợp nhất không gian không được cấp phát của phân vùng bị xóa với phân vùng chính của hệ thống để ngăn chặn một nhà điều tra khám phá phân vùng đã bị mất.

Phần này thảo luận về các kỹ thuật file carving trên Windows, Linux và MacOS và liệt kê các công cụ khôi phục tệp tin khác nhau cho mỗi hệ điều hành. Nó cũng thảo luận về việc khôi phục các phân vùng đã bị xóa bằng cách sử dụng các công cụ khôi phục phân vùng tự động khác nhau.

## File Carving (Khắc phục tệp tin)

- Như đã thảo luận trước đó, khắc phục tệp tin là quá trình khôi phục các tệp tin từ các mảnh và đoạn từ không gian không được cấp phát trên ổ đĩa cứng trong trường hợp không có siêu dữ liệu hệ thống tệp tin. Trong pháp y máy tính, điều này giúp nhà điều tra trích xuất dữ liệu từ một phương tiện lưu trữ mà không cần sự hỗ trợ từ hệ thống tệp tin được sử dụng trong quá trình tạo ra tệp tin.

- Không gian không được cấp phát đề cập đến không gian trên ổ đĩa cứng không chứa bất kỳ thông tin tệp tin nào nhưng lưu trữ dữ liệu tệp tin mà không có chi tiết về vị trí của nó. Nhà điều tra có thể xác định các tệp tin bằng cách sử dụng các đặc điểm nhất định như tiêu đề tệp tin (một số byte đầu tiên) và chân trang tệp tin (một số byte cuối cùng).

- Ví dụ, một nghi phạm có thể cố gắng ẩn một hình ảnh khỏi sự phát hiện của nhà điều tra bằng cách thay đổi phần mở rộng tệp từ .jpg thành .dll. Tuy nhiên, việc thay đổi phần mở rộng tệp không làm thay đổi tiêu đề tệp, điều này có thể tiết lộ định dạng tệp thực tế.

- Phương pháp khắc phục tệp tin có thể khác nhau dựa trên các yếu tố khác nhau như các mảnh dữ liệu hiện có, kỹ thuật xóa đã sử dụng, loại phương tiện lưu trữ, v.v. Quá trình này phụ thuộc vào thông tin về định dạng của các tệp tin hiện có gây quan tâm. Nhà điều tra có thể phân tích các tiêu đề tệp tin để xác minh định dạng tệp tin bằng cách sử dụng các công cụ như 010 Editor, CI Hex Viewer, Hexinator, Hex Editor Neo, Qiew, WinHex, v.v.

- Khắc phục tệp tin không đòi hỏi cấu trúc hệ thống tệp tin để khôi phục dữ liệu từ ổ đĩa, trong khi việc khôi phục tệp tin yêu cầu có kiến thức về cấu trúc hệ thống tệp tin để khôi phục dữ liệu đã bị xóa.

## File Carving trên Windows

Khi một tệp tin/thư mục được xóa khỏi ổ đĩa, nội dung liên quan đến tệp tin/thư mục vẫn tồn tại trên ổ cứng, nhưng các con trỏ tới tệp tin được xóa.

Điều này cho phép các công cụ pháp y như Autopsy, Recall My Files, Ease US Data Recovery và R-Studio for Windows khôi phục các tệp tin/thư mục đã bị xóa từ ổ cứng. Trên các ổ đĩa SSD, việc khôi phục các tệp tin đã bị xóa trở nên khó khăn vì chức năng TRIM được kích hoạt mặc định.

### File Recovery Tools: Windows

#### Recover My Files

Source: http://www.recovermyfiles.com

Recover My Files là một phần mềm khôi phục dữ liệu giúp khôi phục các tệp tin/dữ liệu đã bị xóa từ Thùng rác Windows và các tệp tin bị mất do định dạng hoặc hỏng ổ cứng, nhiễm virus hoặc Trojan, và tắt hệ thống đột ngột hoặc lỗi phần mềm không mong muốn.

**Các tính năng:**
  
   - Khôi phục các tệp tin ngay cả khi đã được xóa khỏi Thùng rác
   - Khôi phục các tệp tin sau khi định dạng tình cờ, ngay cả sau khi Windows được cài đặt lại
   - Thực hiện khôi phục đĩa sau một sự cố ổ cứng
   - Khôi phục các tệp tin sau một lỗi phân vùng
   - Khôi phục dữ liệu từ ổ cứng RAW
   - Khôi phục tài liệu, ảnh, video, nhạc và email
   - Khôi phục từ ổ cứng, thẻ máy ảnh, USB, đĩa Zip, đĩa mềm hoặc phương tiện lưu trữ khác

#### EaseUS Data Recovery Wizard

Source: http://www.recovermyfiles.com

EaseUS Data Recovery Wizard là một phần mềm khôi phục dữ liệu được sử dụng để thực hiện khôi phục định dạng và khôi phục tệp tin đã bị xóa khỏi Thùng rác hoặc dữ liệu bị mất do mất phân vùng hoặc hỏng, lỗi phần mềm, nhiễm virus, tắt đột ngột hoặc bất kỳ lý do không xác định nào dưới Windows 10, 8, 7, 2000/XP/Vista/2003/2008 R2 SP1/Windows 7 SP1. Phần mềm này hỗ trợ RAID phần cứng và ổ cứng, ổ USB, thẻ SD, thẻ nhớ, v.v.
  
**Các tính năng:**

   - Chỉ định loại tệp tin trước khi khôi phục để tìm kiếm các tệp tin đã mất nhanh chóng
   - Lưu kết quả tìm kiếm trước đó để tiếp tục khôi phục liên tục
   - Quét các tệp tin bị mất nhanh hơn bằng cách tự động bỏ qua các sector hỏng

#### DiskDigger

Source: https://diskdigger.org

DiskDigger là một chương trình cho phép phục hồi và khôi phục lại các tệp tin bị mất từ ổ cứng, thẻ nhớ và ổ USB. Công cụ này có thể được sử dụng để khôi phục tài liệu hoặc ảnh đã bị xóa vô tình từ máy tính hoặc từ thẻ nhớ máy ảnh đã được định dạng lại hoặc có thể được sử dụng để kiểm tra các tệp tin trên một ổ USB cũ.

**Các tính năng:**
   - Hoạt động trên các hệ điều hành Windows 10, 8, 7, Vista và XP
   - Hiển thị các tệp tin có thể khôi phục dưới dạng danh sách hoặc xem trước theo hình thu nhỏ
   - Xem trước hình thu nhỏ của các tệp ảnh, bìa album từ các tệp MP3 và WMA và biểu tượng từ các tệp thực thi
   - Khi chọn một tệp tin có thể khôi phục, hiển thị xem trước đầy đủ của tệp tin (nếu có thể). Đối với các tệp ảnh, nó sẽ hiển thị hình ảnh (với chức năng pan và zoom). Đối với các tệp tài liệu, nó sẽ hiển thị xem trước văn bản của tài liệu. Đối với một số tệp âm thanh, nó sẽ cho phép bạn phát lại âm thanh
   - Xem trước các tệp JPG và TIFF sẽ hiển thị thông tin EXIF (mô hình máy ảnh, ngày chụp, cài đặt cảm biến, v.v.)
   - Xem trước các tệp MP3 sẽ hiển thị thông tin ID3 (nghệ sĩ, album, thể loại, v.v.)
   - Xem trước các tệp ZIP sẽ hiển thị danh sách các tệp được chứa trong bản lưu trữ

#### Handy Recovery

Source: https://www.handyrecovery.com

Handy Recovery là phần mềm khôi phục dữ liệu được thiết kế để khôi phục lại các tệp tin đã bị xóa vô tình từ ổ cứng và thẻ nhớ. Chương trình này có thể khôi phục các tệp bị hỏng do tấn công virus, cúp điện và lỗi phần mềm, hoặc các tệp từ các phân vùng đã bị xóa và định dạng. Nếu một chương trình không sử dụng Thùng rác khi xóa tệp, Handy Recovery có thể khôi phục lại các tệp như vậy. Nó cũng có thể khôi phục lại các tệp đã được chuyển từ Thùng rác sau khi đã được làm trống.

**Các tính năng:**
   - Khôi phục lại toàn bộ cấu trúc cây thư mục chứa các tệp và thư mục đã chọn
   - Ngoài dữ liệu tệp chính, chương trình cũng có thể khôi phục các luồng dữ liệu thay thế, được sử dụng trong hệ thống tệp NTFS để lưu trữ thông tin bổ sung về các tệp.

Các công cụ khôi phục dữ liệu trên Windows:

#### Quick Recovery
   
Source: http://www.recoveryourdata.com

Quick Recovery là một phần mềm khôi phục dữ liệu giúp khôi phục các tệp tin đã bị mất, xóa, hỏng hoặc suy giảm. Ứng dụng tìm kiếm, quét và khôi phục các tệp tin đã được mã hóa và bảo vệ bằng mật khẩu.

**Tính năng:**

- Sửa chữa và khôi phục các lỗi bad sectors trên ổ đĩa
- Khôi phục các tệp tin có nguy cơ bị nhiễm virus, ẩn và bảo vệ bằng mật khẩu
- Giao diện đồ họa (GUI) sẽ xác nhận việc sao lưu tại vị trí do người dùng xác định
- Khôi phục và phục hồi các tệp tin đã mã hóa và các tệp hệ thống như trình biên dịch (compiler).

#### Stellar Phoenix Windows Data Recovery
   
Source: https://www.stellarinfo.com

Stellar Phoenix Windows Data Recovery khôi phục dữ liệu đã bị mất, xóa hoặc không thể truy cập từ ổ cứng Windows và các phương tiện lưu trữ khác. Công cụ này giúp khôi phục dữ liệu bị mất do hỏng ổ cứng, định dạng và tấn công virus.

#### Total Recall
   
Source: http://www.totalrecall.com

Total Recall Data Recovery Software khôi phục dữ liệu đã bị mất từ ổ cứng, RAID, ảnh, các tệp tin bị xóa, iPod và các đĩa cắm removable được kết nối qua FireWire hoặc USB.

#### Advanced Disk Recovery

Source: https://www.systweak.com

Phần mềm Advanced Disk Recovery quét toàn bộ hệ thống để tìm các tệp và thư mục đã bị xóa và khôi phục chúng lại.

Phần mềm này quét ổ cứng, các phân vùng, các thiết bị ngoại vi và cả đĩa CD và DVD để tìm các tệp tin có thể khôi phục. Nó cung cấp hai loại quét: Quick Scan sử dụng MFT (Master File Table) và Deep Scan sử dụng chữ ký tệp.

Sau khi quét hoàn tất, người dùng có thể xem trước các tệp và thư mục hoặc khôi phục chúng vào vị trí ưa thích.

#### Windows Data Recovery Software
   
Source: http://www.diskdoctors.net

Disk Doctors Windows Data Recovery Software có thể khôi phục lại các tệp tin bị xóa vô tình, bao gồm các tệp tin đã bị xóa từ Thùng rác và từ Windows Explorer với Shift + Delete. Công cụ này cũng cho phép khôi phục dữ liệu từ phân vùng đã được định dạng lại (sang bất kỳ hệ thống tệp nào) và từ một phân vùng bị hỏng, bị xóa hoặc bị mất.

#### R-Studio

Source: https://www.r-studio.com

R-Studio là một phần mềm khôi phục dữ liệu. Nó có thể khôi phục các tệp tin từ các hệ thống tệp FAT12/16/32/exFAT, NTFS và NTFS5 (được tạo hoặc cập nhật bởi Windows 10, 8, 7, 2000/XP/2003/Vista). R-Studio hoạt động trên các ổ đĩa cục bộ và mạng, các phân vùng đã được định dạng, bị hỏng hoặc đã bị xóa.

**Tính năng:**
- Mô-đun xây dựng RAID tiên tiến: R-Studio có tích hợp mô-đun xây dựng RAID tiên tiến, giúp khôi phục dữ liệu từ hệ thống RAID hỏng.
- Trình chỉnh sửa văn bản/hệ thập lục phân đa tính năng: R-Studio cung cấp trình chỉnh sửa văn bản và hệ thập lục phân đa tính năng, cho phép người dùng nắm rõ hơn về các nội dung của dữ liệu.
- Mô-đun sao chép/ảnh ổ đĩa tiên tiến: R-Studio cung cấp mô-đun sao chép/ảnh ổ đĩa tiên tiến, giúp tạo ra môi trường khôi phục dữ liệu hoàn chỉnh, làm cho nó trở thành một giải pháp toàn diện cho việc tạo một trạm làm việc khôi phục dữ liệu.

#### Orion File Recovery Software

Source: https://www.nchsoftware.com

Phần mềm Orion File Recovery tìm kiếm các tệp tin đã bị xóa trên ổ cứng hoặc bất kỳ ổ đĩa ngoại vi hoặc cầm tay nào được kết nối với máy tính. Các tệp không bị ghi đè có thể được khôi phục hoặc xóa vĩnh viễn để ngăn chặn khôi phục trong tương lai.

**Tính năng:**
- Khôi phục các tệp tin, nhạc hoặc ảnh đã bị xóa
- Tìm kiếm trên ổ cứng, ổ đĩa ngoại vi hoặc ổ flash
- Xóa tệp tin vĩnh viễn để tăng cường bảo mật.

#### Data Rescue PC

Source: https://www.prosofteng.com

Data Rescue PC khôi phục các tệp tin từ ổ đĩa cứng đã bị hỏng hoặc bị nhiễm virus. Nó cũng khôi phục từ ổ đĩa ngoài hoặc ổ đĩa thứ cấp. Phần mềm quét ổ đĩa và sao chép các tệp tin sang ổ đĩa thứ hai.

**Tính năng:**
- Khôi phục mọi loại tệp tin từ ổ đĩa cứng
- Hoạt động khi ổ đĩa không thể gắn kết hoặc chỉ hoạt động một phần
- Khôi phục các tệp tin đã bị xóa, mất hoặc hỏng
- Khôi phục hình ảnh số từ các phương tiện máy ảnh kỹ thuật số, ngay cả sau khi đã bị xóa hoặc định dạng lại
- Khôi phục toàn bộ ổ đĩa hoặc chỉ các tệp tin bạn cần
- Khôi phục hình ảnh, phim và nhạc từ ổ đĩa PC và bất kỳ loại phương tiện máy ảnh kỹ thuật số nào.
#### Recover4all Professional

Source: http://www.recover4all.com

Recover4all là phần mềm khôi phục dữ liệu giúp khôi phục các tệp tin bị xóa vô tình dưới Windows. Nó khôi phục lại các tệp tin đã bị xóa từ Thùng rác, hoặc nếu ổ đĩa đã được định dạng hoặc hệ thống tệp bị hỏng.

#### Recuva
    
Source: http://www.piriform.com/recuva

Recuva khôi phục các tệp tin đã bị xóa từ máy tính Windows, Thùng rác, thẻ máy ảnh kỹ thuật số hoặc máy nghe nhạc MP3. Các tính năng của nó bao gồm:
    - **Khôi phục các tệp tin bị mất ưu việt:** Recuva có thể khôi phục lại ảnh, nhạc, tài liệu, video, email hoặc bất kỳ loại tệp tin nào khác. Ngoài ra, nó còn khôi phục từ bất kỳ phương tiện ghi đè nào, bao gồm thẻ nhớ, ổ đĩa cứng ngoại vi, USB, v.v.
    -** Khôi phục từ đĩa hỏng:** Recuva có thể khôi phục tệp tin từ các ổ đĩa bị hỏng hoặc mới định dạng và khả năng khôi phục là cao hơn.
    - **Quét sâu tìm tệp tin bị chôn:** Đối với các tệp tin khó tìm, Recuva có chế độ quét sâu tiên tiến tìm kiếm trên ổ đĩa để tìm các t traces của các tệp tin đã bị xóa.
    - **Xóa tệp tin một cách an toàn:** Đôi khi bạn cần một số tệp tin biến mất hoàn toàn. Tính năng xóa an toàn của Recuva sử dụng các kỹ thuật xóa tiêu chuẩn của ngành công nghiệp và quân đội để đảm bảo các tệp tin của bạn được xóa hoàn toàn.

#### Recover4all Professional

Source: http://www.recover4all.com

Recover4all Professional là một phần mềm khôi phục (undelete) các tệp tin bị xóa vô tình dưới hệ điều hành Windows. Nó khôi phục các tệp tin đã bị xóa từ Recycle Bin, hoặc nếu ổ đĩa đã được định dạng, hoặc nếu hệ thống tệp tin bị hỏng. Phần mềm Recover4all không yêu cầu cài đặt và có thể chạy trực tiếp từ một ổ đĩa USB, ổ flash, vv.

#### Recuva

Source: http://www.piriform.com/recuva

Recuva là một phần mềm khôi phục các tệp tin bị xóa từ máy tính chạy hệ điều hành Windows, Recycle Bin, thẻ máy ảnh kỹ thuật số hoặc máy nghe nhạc MP3. Các tính năng của Recuva bao gồm:

- **Khôi phục tệp tin một cách xuất sắc:** Recuva có thể khôi phục các hình ảnh, nhạc, tài liệu, video, email hoặc bất kỳ loại tệp tin nào bị mất. Ngoài ra, nó cũng có thể khôi phục từ bất kỳ phương tiện ghi đè nào, bao gồm thẻ nhớ, ổ đĩa cứng ngoài, USB, vv.

- **Khôi phục từ đĩa bị hỏng:** Recuva có thể khôi phục các tệp tin từ các ổ đĩa bị hỏng hoặc mới được định dạng, và khả năng khôi phục là cao hơn.

- **Quét sâu để tìm các tệp tin đã bị chôn vùi:** Đối với các tệp tin khó tìm, Recuva có chế độ quét sâu tiên tiến giúp tìm kiếm bất kỳ dấu vết nào của các tệp tin đã bị xóa.

- **Xóa tệp tin một cách an toàn:** Đôi khi bạn cần xóa một tệp tin một cách triệt hạ. Tính năng xóa an toàn của Recuva sử dụng các kỹ thuật xóa tiêu chuẩn trong ngành và quân sự để đảm bảo tệp tin của bạn bị xóa hoàn toàn.

#### Active@ File Recovery

Source: https://www.file-recovery.net

Active@ File Recovery bao gồm một hình ảnh CD/DVD ISO cho phép bạn ghi một đĩa CD hoặc DVD khởi động với một phiên bản nhẹ của Windows 7 chạy trong RAM (WinPE 3.0). Nó có thể khôi phục dữ liệu trong trường hợp hệ thống không thể khởi động và không thể kết nối được ổ đĩa cứng bị hỏng với máy tính khác.

#### Pandora Recovery

Source: https://www.pandorarecovery.com

Pandora Recovery cho phép bạn tìm kiếm và khôi phục các tệp tin đã bị xóa có thể khôi phục được từ các ổ đĩa được định dạng NTFS và FAT, bất kể loại tệp tin đó là hình ảnh, bài hát, phim hoặc tài liệu. Pandora Recovery sẽ quét ổ đĩa và tạo một chỉ mục của các tệp tin và thư mục (thư mục) đã bị xóa và tồn tại trên bất kỳ ổ đĩa logic nào của máy tính với định dạng tệp tin được hỗ trợ. Sau khi quét hoàn tất, người dùng hoàn toàn kiểm soát các tệp tin cần khôi phục và đích sử dụng cho quá trình khôi phục.

#### Ontrack EasyRecovery

Source: https://www.krollontrack.com

Ontrack DataAdvisor là phần mềm khôi phục tệp tin kết hợp các danh mục sao lưu cũ từ các hệ thống và phương tiện khác nhau thành một danh mục duy nhất. Nó hỗ trợ nhiều trạm làm việc và cho phép người dùng tự tạo danh mục của riêng họ. Sau khi nhận được các danh mục, chúng sẽ được đưa vào Ontrack DataAdvisor và người dùng có thể truy cập chúng thông qua một ứng dụng trực tuyến an toàn.

Nó có các công cụ khôi phục như khôi phục email; trình xem hex; công nghệ theo dõi, phân tích và báo cáo tự động (SMART); chẩn đoán khối lỗi/khối sử dụng không tốt; công cụ hình ảnh; sao chép ổ đĩa; và làm mới ổ đĩa. Nó cung cấp giám sát ổ đĩa cứng với quét SMART để bảo vệ ổ đĩa cứng và chức năng xóa để giải phóng không gian lưu trữ.

#### Seagate File Recovery Software

Source: https://www.seagate.com

Phần mềm Seagate File Recovery khôi phục các tệp tin và các kế hoạch cứu hộ cho các thiết bị lưu trữ. Công cụ này khôi phục các tệp tin từ máy tính để bàn, máy tính xách tay và ổ đĩa cứng ngoài cũng như các máy tính bảng và bộ nhớ trên chip trong điện thoại thông minh.

#### Wise Data Recovery

Source: http://www.wisecleaner.com

Wise Data Recovery là phần mềm khôi phục dữ liệu được sử dụng để lấy lại dữ liệu bị mất hoặc định dạng hoặc dữ liệu bị mất do sự cố hệ thống. Nó có thể khôi phục các tệp tin bị mất từ ổ đĩa cứng, ổ đĩa cứng ngoài, ổ đĩa USB, thẻ nhớ, máy ảnh kỹ thuật số, điện thoại di động, máy nghe nhạc MP3 và các phương tiện lưu trữ khác.

#### Glary Undelete

Source: https://www.glarysoft.com

Phần mềm Glary Undelete hoạt động trên hệ thống tệp FAT và NTFS. Công cụ này khôi phục các tệp bị xóa từ Recycle Bin, trong cửa sổ DOS, từ Windows Explorer với nút SHIFT được giữ lại. Nó khôi phục các tệp tin đã bị xóa do lỗi, sự cố và virus. Nó có thể khôi phục các tệp tin mà người dùng đã nén hoặc chia tách hoặc mã hóa trên hệ thống tệp NTFS.

#### Disk Drill

Source: https://www.cleverfiles.com

Disk Drill là phần mềm khôi phục dữ liệu cho máy tính Windows. Nó có thể khôi phục dữ liệu từ ổ đĩa cứng nội bộ và bên ngoài, ổ đĩa flash USB, iPod, thẻ nhớ. Nó có thể khôi phục các tệp tin từ mất phân vùng, ổ đĩa cứng bị định dạng lại, khởi động không thành công, xóa vô tình, làm sạch Recycle Bin và hỏng thẻ nhớ.

#### PhotoRec

Source: https://www.cgsecurity.org

Phần mềm khôi phục dữ liệu PhotoRec khôi phục các tệp tin bị mất; video, tài liệu và lưu trữ từ ổ đĩa cứng; đĩa CD-ROM; và hình ảnh bị mất từ bộ nhớ máy ảnh kỹ thuật số. Nó có thể khôi phục hệ thống tệp tin của phương tiện nếu nó bị hỏng nặng hoặc bị định dạng lại. Công cụ này khôi phục các phân vùng bị mất trên các hệ thống tệp tin khác nhau và làm cho các đĩa không thể khởi động có thể hoạt động.

#### DDR Professional Recovery Software

Source: http://www.recoverybull.com

Phần mềm khôi phục DDR Professional Windows khôi phục các tệp tin bị xóa trong tất cả các tình huống mất dữ liệu chính, bất kể là mất từ các phân vùng ổ đĩa cứng cố định hay từ bất kỳ ổ đĩa lưu trữ USB nào. Công cụ khôi phục dữ liệu tiên tiến này khôi phục các tệp bị xóa từ thẻ nhớ, máy ảnh kỹ thuật số, ổ đĩa USB, ổ cứng di động ngoài và người chơi nhạc, và thậm chí khôi phục các tệp bị xóa trên phân vùng ổ đĩa cứng chỉ trong vài lần nhấp chuột.

####File Scavenger

Source: http://www.quetek.com

File Scavenger là tiện ích khôi phục tệp "undelete" và dữ liệu cho Windows 10, 8, 7, Vista, Server 2003, 2000, NT và ME/98/95. File Scavenger khôi phục các tệp bị xóa một cách không cố ý (bao gồm các tệp đã bị xóa khỏi Recycle Bin, trong cửa sổ DOS, từ ổ đĩa mạng và từ Windows Explorer với nút SHIFT được giữ lại) miễn là việc khôi phục được thực hiện trước khi các tệp bị ghi đè một cách vĩnh viễn bởi dữ liệu mới. File Scavenger hỗ trợ các ổ đĩa cơ bản và động, nén NTFS, luồng dữ liệu thay thế, tệp tạm thời, tên tập tin Unicode, v.v. Trừ trường hợp nghiêm trọng, cả tệp và đường dẫn thư mục dẫn đến tệp đều có thể được khôi phục.

#### GetDataBack

Source: http://www.runtime.org

GetDataBack khôi phục dữ liệu nếu bảng phân vùng ổ đĩa cứng, bản ghi khởi động, FAT/MFT hoặc thư mục gốc bị mất hoặc bị hỏng; dữ liệu bị mất do tấn công virus; ổ đĩa đã được định dạng; fdisk đã được chạy; một sự cố hỏng hệ thống do ngưng hoạt động điện; tệp bị mất do một lỗi phần mềm; hoặc tệp bị xóa vô tình. Nó có thể khôi phục dữ liệu của bạn ngay cả khi ổ đĩa không được nhận diện bởi Windows.

#### UndeletePlus

Source: https://undeleteplus.com

UndeletePlus quét máy tính hoặc phương tiện lưu trữ để tìm các tệp bị xóa và khôi phục chúng theo yêu cầu. Nó hoạt động với máy tính, ổ đĩa flash, máy ảnh và các hình thức khác của phương tiện lưu trữ dữ liệu. Nó quét thiết bị, chọn các tệp cần khôi phục và khôi phục thông tin hoặc hình ảnh chỉ bằng một cú nhấp chuột.

#### VirtualLab

Source: https://www.binarybiz.com

VirtualLab là một phần mềm khôi phục dữ liệu hoạt động với tất cả các hệ điều hành Windows từ Windows 98 đến Windows 10, 8, 7, FAT 12/16/32 và hệ thống tệp NTFS.
Nó có thể phục hồi các tệp đã bị xóa từ các phân vùng bị mất/hỏng, đĩa định dạng, email bị xóa, ổ đĩa cứng và hệ thống RAID, và ảnh và thẻ nhớ flash.

#### Active@ UNDELETE

Source: https://www.active-undelete.com

Active@ UNDELETE là một phần mềm khôi phục dữ liệu giúp khôi phục các tệp bị xóa và phục hồi các phân vùng bị xóa. Nó khôi phục các khối ổ đĩa bị xóa trong chỗ, sửa lỗi các khối boot của ổ đĩa và có khả năng quay lại các thay đổi trong phân vùng.
Nó hỗ trợ các hệ điều hành Windows 10/8/7/Vista/XP, 2003/2008 Server.

#### WinUndelete

Source: https://www.winundelete.com

Phần mềm WinUndelete có thể được sử dụng để khôi phục các tệp bị xóa từ ổ đĩa cứng, ổ đĩa flash, ổ đĩa ngoài USB, thẻ máy ảnh kỹ thuật số và nhiều thiết bị khác. WinUndelete khôi phục các tệp bị xóa sau khi đã rỗng thùng rác hoặc bằng cách sử dụng các hành động xóa khác bỏ qua thùng rác.

#### R-Undelete

Source: https://www.r-undelete.com

Công cụ R-Undelete khôi phục tệp từ hệ thống tệp FAT và NTFS. R-Undelete khôi phục tệp trên bất kỳ ổ đĩa cục bộ nào được phần mềm nhận ra. Một thuật toán khôi phục tệp bổ sung tăng cường chất lượng khôi phục tệp. R-Undelete có thể chạy từ menu ngữ cảnh ổ đĩa và thư mục. Các tệp hình ảnh, video và âm thanh có thể được xem trước trong R-Undelete.

## File Carving on Linux

Trong Linux, người dùng có thể xóa tệp tin bằng lệnh "rm", trong đó inode trỏ đến tệp tin bị xóa, nhưng tệp tin vẫn tồn tại trên đĩa.

Do đó, nhà điều tra pháp y có thể sử dụng các công cụ bên thứ ba như Stellar Phoenix Linux Data Recovery, R-Studio cho Linux, TestDisk, PhotoRec, Kernel for Linux Data Recovery, v.v., để khôi phục dữ liệu bị xóa từ đĩa.

Nếu người dùng xóa một tệp đang được sử dụng bởi bất kỳ tiến trình nào, nội dung của tệp sẽ chiếm một không gian đĩa không thể được tái sử dụng bởi bất kỳ tệp hay chương trình nào khác.

Hệ thống tệp mở rộng thứ hai (ext2) được thiết kế sao cho nó hiển thị một số nơi dữ liệu có thể bị ẩn.

Lưu ý rằng nếu một tệp thực thi tự xóa mình, nội dung của nó có thể được khôi phục từ một bản hình ảnh bộ nhớ /proc. Lệnh "cp /proc/$PID/exe /tmp/file" tạo một bản sao của tệp trong /tmp.

Khác với Windows, Linux có thể truy cập và khôi phục dữ liệu từ nhiều máy tính khác nhau. Linux kernel hỗ trợ nhiều hệ thống tệp bao gồm VxFS, UFS, HFS, NTFS và FAT. Một số hệ thống tệp không đọc được trong môi trường Windows, và người dùng có thể dễ dàng khôi phục các tệp như vậy bằng cách sử dụng phiên bản Linux có khả năng khởi động như Knoppix.














