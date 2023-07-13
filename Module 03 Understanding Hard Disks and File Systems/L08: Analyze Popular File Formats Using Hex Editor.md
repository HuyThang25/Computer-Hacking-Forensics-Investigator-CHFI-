Hex editor được thiết kế để phân tích và chỉnh sửa các tệp tin, bộ nhớ chính, hình ảnh đĩa và cấu trúc của chúng, vv. Phần này sẽ thảo luận về việc xem xét các định dạng tệp tin khác nhau như jpg, png, bmp, pdf, zip và docx bằng hex editor.

## Phân tích Tệp hình ảnh: JPEG

Nguồn: https://developer.apple.com

Joint Photographic Experts Group (JPEG), ủy ban đã tạo ra tiêu chuẩn và định dạng tệp JPEG, là thuật ngữ được sử dụng để đại diện cho bất kỳ tệp hình ảnh đồ họa nào được tạo bằng tiêu chuẩn và định dạng JPEG.

Đây là một phương pháp nén mất mát dành cho hình ảnh kỹ thuật số và cho phép người dùng điều chỉnh mức độ nén, ảnh hưởng đến kích thước lưu trữ và chất lượng hình ảnh. 
Tệp JPEG cho phép tỷ lệ nén lên đến 90%, chỉ còn một phần mười so với kích thước dữ liệu gốc.

### Cấu trúc tệp

Một luồng bit JPEG chứa một chuỗi các phần dữ liệu. Mỗi phần bắt đầu bằng một giá trị đánh dấu, với mỗi đánh dấu có một giá trị số nguyên 16-bit và được lưu trữ theo định dạng byte big-endian. Bit quan trọng nhất của đánh dấu được đặt thành 0xff. Byte thấp hơn của đánh dấu xác định loại đánh dấu.

Các bit đầu tiên của tệp đại diện cho loại tệp, và tệp JPEG bắt đầu bằng giá trị nhị phân 0xffd8 (bắt đầu hình ảnh; SOI) và kết thúc bằng giá trị nhị phân 0xffd9 (kết thúc hình ảnh; EOI). Do đó, ffd8 (0x được ngầm hiểu) ở đầu biểu thị một tệp JPEG khi xem bằng hex editor. Luồng bit JPEG chứa một chuỗi các phần dữ liệu, hoặc đoạn, và mỗi phần bắt đầu bằng một giá trị đánh dấu. Định dạng cơ bản của một đoạn là giá trị số nguyên 16-bit xác định kích thước tệp. Byte quan trọng nhất của đánh dấu (bit bên trái nhất) là 0xff. Byte thấp hơn của đánh dấu xác định loại đánh dấu.

Định dạng cơ bản của một đoạn như sau: đánh dấu FF số thứ tự (1 byte) dữ liệu; kích thước (2 byte); và dữ liệu (n byte). Ví dụ, cho đánh dấu FF E1 00 0E, đánh dấu (0xFFE1) có 0x000E (tương đương 14) byte dữ liệu. Tuy nhiên, kích thước 14 byte bao gồm bộ mô tả kích thước (2 byte); do đó, chỉ có 12 byte dữ liệu theo sau 0x000E.

## Phân tích Tệp hình ảnh: BMP

Định dạng tệp hình ảnh bitmap (BMP), định dạng tệp hình ảnh bitmap độc lập thiết bị (DIB), hoặc đơn giản là bitmap là một định dạng tệp hình ảnh đồ hoạ tiêu chuẩn được sử dụng để lưu trữ hình ảnh trên hệ điều hành Windows. Microsoft đã phát triển định dạng này để Windows có thể hiển thị hình ảnh trên bất kỳ loại màn hình nào. Hình ảnh bitmap có thể bao gồm các hoạt ảnh. Kích thước và màu sắc của các hình ảnh này có thể thay đổi từ 1 bit mỗi pixel (đen trắng) đến màu 24 bit (16,7 triệu màu).

### Cấu trúc tệp

Mỗi tệp bitmap chứa các cấu trúc dữ liệu sau:
- Tiêu đề tệp: Phần đầu tiên của một tệp bitmap là tiêu đề, chứa dữ liệu về loại, kích thước và bố cục của tệp
- Tiêu đề thông tin: Đây là một thành phần tiêu đề chứa các thông số kích thước, loại nén và định dạng màu của bitmap
- Mảng RGBQUAD: Đây là một bảng màu gồm các phần tử bằng số màu có mặt trong bitmap; bảng màu này không hỗ trợ bitmap với màu 24 bit, vì mỗi pixel được biểu diễn bằng giá trị RGB 24 bit trong bitmap thực tế
- Dữ liệu hình ảnh: Đây là một mảng các byte chứa dữ liệu hình ảnh bitmap; dữ liệu hình ảnh bao gồm thông tin màu sắc và đổ bóng cho mỗi pixel

Một tệp bitmap luôn có 42 4D là các ký tự đầu tiên trong biểu diễn thập lục phân. Những ký tự này tương ứng với BM trong mã ASCII.

## Hex View of Popular Image File Formats:

### Định dạng Tệp hình ảnh GIF

GIF là một định dạng tệp chứa 8 bit cho mỗi pixel và hiển thị 256 màu sắc cho mỗi khung hình. Định dạng này được phát triển bởi CompuServe vào năm 1987. GIF sử dụng kỹ thuật nén dữ liệu không mất mát, giữ cho chất lượng hình ảnh không thay đổi. Hiện tại có hai phiên bản của GIF.

- **GIF 87a:** Được phát triển vào năm 1987, đây là phiên bản đầu tiên của GIF sử dụng kỹ thuật nén tệp Lempel-Ziv-Welch (LZW) và hỗ trợ các tính năng như tạo ảnh xen kẽ, bảng màu 256 màu và lưu trữ nhiều hình ảnh.
- **GIF 89a:** Được tạo ra vào năm 1989, phiên bản này hỗ trợ các tính năng như độ trong suốt của nền, thời gian trễ và các tham số thay thế hình ảnh. Các tính năng này hữu ích để lưu trữ nhiều hình ảnh dưới dạng hoạt ảnh.

Cấu trúc tệp GIF bao gồm tiêu đề, dữ liệu hình ảnh, dữ liệu siêu dữ liệu tùy chọn và chân trang. Giá trị hex của một tệp hình ảnh GIF bắt đầu với các giá trị 47 49 46, đại diện cho tên tệp GIF.

### Định dạng Tệp hình ảnh PNG

Portable Network Graphics (PNG) là định dạng hình ảnh không mất mát nhằm thay thế định dạng GIF và TIFF. PNG cải tiến định dạng tệp GIF và thay thế nó bằng một định dạng tệp hình ảnh. Định dạng này không có bản quyền và không yêu cầu giấy phép.

Định dạng tệp PNG hỗ trợ màu sắc thật 24-bit, độ trong suốt trong cả kênh bình thường và kênh alpha, cũng như hình ảnh dựa trên bảng màu/ chỉ số với 24-bit RGB hoặc 32-bit RGBA và hình ảnh xám.

Chữ ký tệp PNG bao gồm phần còn lại của tệp chứa một hình ảnh PNG duy nhất. Các hình ảnh này bao gồm một chuỗi các khối, bắt đầu bằng một khối IHDR và kết thúc bằng một khối IEND. Giá trị hex của tệp PNG, như được hiển thị trong ảnh chụp màn hình dưới đây, bắt đầu với 89 50 4e, tương ứng với giá trị hex của GIF.

## Phân tích Tệp PDF

Adobe Inc. phát triển định dạng Portable Document Format (PDF) vào năm 1992. Định dạng này giúp người dùng dễ dàng xem, lưu và in tài liệu mà không phụ thuộc vào nền tảng, hệ điều hành, phần cứng và phần mềm sử dụng. Nó bao gồm văn bản kèm theo các thành phần truyền thông như hình ảnh và liên kết. Phần mềm Acrobat Reader có thể mở và hiển thị các tệp PDF.

### Ưu điểm

- Tệp PDF không phụ thuộc vào thiết bị và hỗ trợ các hệ thống khác nhau như Mac, Linux, v.v.
- Các tệp này hỗ trợ các thuật toán nén khác nhau.
- Chúng cũng hỗ trợ nhiều yếu tố đa phương tiện.
- Nó cho phép bảo mật bằng mật khẩu.

### Cấu trúc Tệp PDF

- **Phần tiêu đề:** Dòng đầu tiên của tệp PDF chỉ định số phiên bản của PDF.
  Ví dụ: %PDF-1.3
- **Thân:** Nó bao gồm các đối tượng (hình ảnh, phông chữ, trường hình thức, luồng văn bản, chú thích, đánh dấu, v.v.) tạo nên nội dung của tài liệu.

### Bảng liên kết chéo (xref table)

- Chứa liên kết đến tất cả các đối tượng trong tệp
- Cho phép truy cập ngẫu nhiên đến các đối tượng
- Cho phép theo dõi các thay đổi đã được cập nhật trong tệp PDF.

### Phần Trailer:

- Chứa các liên kết đến bảng xref và các đối tượng chính trong từ điển trailer
- Kết thúc bằng %%EOF để nhận biết sự kết thúc của tệp

Giá trị hex cho một tệp PDF bắt đầu bằng 25 50 44 46, đây là chữ ký của mọi tệp PDF biểu thị cho các giá trị %PDF ở dạng hexa. Phiên bản tệp PDF sẽ theo sau chữ ký này, trong khi tệp kết thúc với giá trị %EOF, biểu thị cho sự kết thúc của tệp.
