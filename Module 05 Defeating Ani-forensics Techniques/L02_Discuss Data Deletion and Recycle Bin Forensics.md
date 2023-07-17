Xóa tệp tin/dữ liệu là một kỹ thuật chống pháp y phổ biến được sử dụng bởi các kẻ tấn công. Khi một kẻ tấn công xóa tệp tin/dữ liệu trên hệ thống Windows, nếu nó đã được xóa bằng cách sử dụng thao tác xóa thông thường và không phải là thao tác Shift+Delete, thì nó sẽ nằm trong Thùng rác (Recycle Bin). Để ngăn chặn việc khôi phục lại các tệp tin đã bị xóa như vậy, người gây án có thể ẩn hoặc xóa các siêu dữ liệu liên quan đến các tệp tin trong thư mục Thùng rác.

Phần này trình bày những gì xảy ra với các tệp tin khi chúng bị xóa trên hệ thống Windows và thảo luận về cách các nhà điều tra có thể tìm và khôi phục các tệp tin đã bị ẩn/mất từ Thùng rác.

## Điều gì xảy ra khi một file bị xoá trong Windows?

Khi người dùng xóa một tệp tin trên hệ thống Windows, hệ điều hành không xóa thực sự tệp tin đó mà đánh dấu mục nhập của tệp tin là không được cấp phát trong Bảng Quản lý Tập tin Chính (MFT) và gán một ký tự đặc biệt. Ký tự này chỉ ra rằng không gian đã sẵn sàng để sử dụng.

Trong hệ thống tệp tin FAT, hệ điều hành thay thế ký tự đầu tiên của tên tệp tin bị xóa bằng một mã hex byte, E5h. E5h là một thẻ đặc biệt chỉ ra rằng đó là một tệp tin đã bị xóa. Hệ thống tệp tin FAT đánh dấu các cụm tương ứng của tệp tin đó là không được sử dụng, mặc dù chúng không trống.

Trong hệ thống tệp tin NTFS, khi người dùng xóa một tệp tin, hệ điều hành chỉ đánh dấu mục nhập của tệp tin đó là không được cấp phát nhưng không xóa nội dung thực tế của tệp tin. Các cụm được cấp phát cho tệp tin bị xóa được đánh dấu là miễn phí trong $BitMap (tệp tin $BitMap là một bản ghi của tất cả các cụm đã sử dụng và chưa sử dụng). Máy tính sau đó nhận ra các cụm trống đó và sử dụng không gian đó để lưu trữ một tệp tin mới. Tệp tin bị xóa có thể khôi phục lại nếu không gian không được cấp phát cho bất kỳ tệp tin nào khác. Trên hệ thống Windows, thực hiện thao tác Xóa thông thường gửi các tệp tin đến Thùng rác. Trong khi thực hiện thao tác Shift+Delete sẽ bỏ qua Thùng rác.

### Recycle Bin trong Windows

Thùng rác trong Windows

Thùng rác tạm thời lưu trữ các tệp tin đã bị xóa. Khi người dùng xóa một mục, nó sẽ được gửi đến Thùng rác. Tuy nhiên, Thùng rác không lưu trữ các mục bị xóa từ phương tiện di động như ổ đĩa USB hoặc ổ đĩa mạng. Các mục có trong Thùng rác vẫn chiếm không gian đĩa cứng và dễ dàng khôi phục. Người dùng có thể sử dụng tùy chọn khôi phục trong Thùng rác để khôi phục lại các tệp tin đã bị xóa và gửi chúng trở lại vị trí ban đầu.

Ngay cả khi các tệp tin đã bị xóa khỏi Thùng rác, chúng vẫn tiếp tục chiếm không gian đĩa cứng cho đến khi các vị trí đó được hệ điều hành ghi đè bằng dữ liệu mới.

Khi Thùng rác trở nên đầy, Windows sẽ tự động xóa các mục cũ hơn. Hệ điều hành Windows gán một không gian cụ thể trên mỗi phân vùng ổ đĩa cứng để lưu trữ các tệp tin trong Thùng rác. Hệ thống không lưu trữ các mục lớn hơn trong Thùng rác; thay vào đó, nó xóa chúng vĩnh viễn.

#### Dưới đây là các bước để thay đổi dung lượng lưu trữ của Thùng rác:

1. Trên Màn hình, nhấp chuột phải vào biểu tượng Thùng rác và chọn "Thuộc tính".
2. Chọn vị trí của Thùng rác cần thay đổi, dưới mục Vị trí Thùng rác (thường là ổ đĩa C).
3. Nhấp "Kích thước tùy chỉnh" và sau đó nhập dung lượng lưu trữ tối đa (theo MB) cho Thùng rác vào ô "Kích thước tối đa (MB)".
4. Nhấp OK.

#### Dưới đây là các bước để xóa hoặc khôi phục tệp tin trong Thùng rác:

Mở Thùng rác để thực hiện các thao tác xóa hoặc khôi phục.

1. Để khôi phục một tệp tin, nhấp chuột phải vào biểu tượng tệp tin và chọn Khôi phục.
2. Để khôi phục tất cả các tệp tin, chọn Tất cả, điều hướng đến Quản lý, và nhấp vào Khôi phục các mục đã chọn.
3. Để xóa một tệp tin, nhấp chuột phải vào biểu tượng tệp tin và chọn Xóa.
4. Để xóa tất cả các tệp tin, có hai phương pháp:
  	- Chọn Tất cả, nhấp chuột phải và chọn tùy chọn Xóa
  	- Đi đến tùy chọn Quản lý trong thanh công cụ và nhấp vào Làm trống Thùng rác
    	- Cả hai phương pháp đều hiển thị một cửa sổ pop-up xác nhận việc xóa vĩnh viễn các mục đó. Nhấp vào Đồng ý.

#### Vị trí lưu trữ Thùng rác trên hệ thống tệp tin FAT: 

Hệ thống tệp tin FAT cũ hơn, được sử dụng trong Windows 98 và các phiên bản trước đó, lưu trữ các tệp tin đã bị xóa trong thư mục Drive:\RECYCLED.

#### Vị trí lưu trữ Thùng rác trên hệ thống tệp tin NTFS:

- Trên Windows 2000, NT và XP, nó nằm trong `Drive:\RECYCLER\<SID>`
- Trên Windows Vista và các phiên bản sau đó, nó nằm trong: `Drive:\$Recycle.Bin\<SID>`

Không có giới hạn kích thước cho Thùng rác trong Windows Vista và các phiên bản sau đó, trong khi các phiên bản cũ có giới hạn tối đa là 3,99 GB. Thùng rác không thể lưu trữ các mục lớn hơn dung lượng lưu trữ của nó.

Khi người dùng xóa một tệp tin hoặc thư mục, Windows lưu trữ tất cả các chi tiết của tệp tin, chẳng hạn như tên và đường dẫn lưu trữ, trong tệp INFO2, một tệp tin ẩn được tìm thấy trong Thùng rác. Hệ điều hành sử dụng thông tin này để khôi phục lại tệp tin đã bị xóa đến vị trí ban đầu. Thư mục ẩn Recycled chứa các tệp tin đã bị xóa từ một máy tính chạy Windows.

**Trong các phiên bản Windows trước, các tệp tin đã bị xóa được đổi tên bởi hệ điều hành bằng định dạng sau:**

D<ký tự ổ đĩa gốc của tệp tin><#>.<phần mở rộng gốc>

Ví dụ, trong trường hợp của một tệp tin Dxy.ext trong thư mục Recycled, "x" đại diện cho tên ổ đĩa như "C", "D" và các tên khác, "y" đại diện cho số tuần tự bắt đầu từ một và "ext" là phần mở rộng của tệp tin gốc.

**Trong Windows Vista và các phiên bản sau đó, các tệp tin đã bị xóa được đổi tên bởi hệ điều hành bằng định dạng sau:**

$R<#>.<phần mở rộng gốc>, trong đó <#> biểu thị một tập hợp các chữ cái và số ngẫu nhiên.

Đồng thời, một tệp tin siêu dữ liệu tương ứng được tạo ra có tên:

$I<#>.<phần mở rộng gốc>, trong đó <#> biểu thị một tập hợp các chữ cái và số ngẫu nhiên tương tự như $R.

Các tệp tin $R và $I nằm tại C:\$Recycle.Bin\<USER SID>.

**Tệp tin $I chứa các siêu dữ liệu sau đây:**

- Tên tệp tin ban đầu
- Kích thước tệp tin ban đầu
- Ngày và giờ mà tệp tin đã bị xóa

Trong các phiên bản Windows mới hơn Vista và XP, hệ điều hành lưu trữ toàn bộ đường dẫn và tên tệp tin hoặc thư mục trong một tệp tin ẩn được gọi là INFO2. Tệp tin này vẫn nằm trong thư mục Recycled hoặc Recycler và lưu trữ thông tin về các tệp tin đã bị xóa.

INFO2 là tệp tin cơ sở dữ liệu chính và rất quan trọng cho việc khôi phục dữ liệu. Nó chứa các thông tin khác nhau về các tệp tin đã bị xóa như tên tệp tin ban đầu, kích thước tệp tin ban đầu, ngày và giờ xóa, số định danh duy nhất và số ổ đĩa mà tệp tin đã được lưu trữ.

