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
  
** Các tính năng:**

   - Chỉ định loại tệp tin trước khi khôi phục để tìm kiếm các tệp tin đã mất nhanh chóng
   - Lưu kết quả tìm kiếm trước đó để tiếp tục khôi phục liên tục
   - Quét các tệp tin bị mất nhanh hơn bằng cách tự động bỏ qua các sector hỏng

