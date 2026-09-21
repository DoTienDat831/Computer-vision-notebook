Ánh sáng phản xạ - Các màu sắc con người cảm nhận được được xác định bởi bản chất của một ánh sáng phản xạ từ một vật thể.

Hình ảnh được tạo ra bằng cách chiếu sáng một cảnh và hấp thụ năng lượng phản xạ bởi các vật thể trong cảnh đó.

Hình ảnh kỹ thuật số luôn chỉ là sự xấp xỉ của cảnh thực tế.

IMAGE REPRESENTATION
- Một ảnh kỹ thuật số được tạo từ M hàng và N cột điểm ảnh, mỗi điểm ảnh lưu trữ một giá trị.
- Giá trị điểm ảnh thường là các mức xám trong khoảng 0 - 255 (Đen - Trắng).
- Dễ dàng bỉểu diễn dưới dạng ma trận.

Spatial Resolution - Độ phân giải không gian của một hình ảnh được xác định bởi cách lây mẫu được thực hiện. (16, 32, 64, 128, 256)

Intensity Level Resolution - Độ phân giải mức cường độ ánh sáng
- đề cập đến số mức độ cường độ sáng được sử dụng để biểu diễn hình ảnh.
	- ILR càng nhiều, mức độ chi tiết có thể phân biệt được trong ảnh càng tinh tế.
	- ILR được cho dưới dạng số bit được sử dụng để lưu trữ mỗi mức độ cường độ ánh sáng.

Relationships Between Pixels
Xét 1 điểm ảnh p tại (x, y) -> p(x,y)
 - 4 láng giềng của p, N(4): (x+1, y), (x-1, y), (x, y+1), (x, y-1)
 - 4 láng giềng chéo của p:Nd(4) (x+1, y+1), (x+1,y-1), (x-1, y+1), (x-1, y-1)
 - 8 láng giềng: N(4) + Nd(4)


- **Ảnh số (Digital Image)** = ma trận 2 chiều gồm các pixel.
- **Lấy mẫu (Sampling)** = chọn số lượng pixel để biểu diễn ảnh.
- **Lượng tử hóa (Quantization)** = quyết định số mức cường độ sáng (mức xám) mà mỗi pixel có thể nhận.
- **Độ phân giải (Resolution)** = được xác định bởi cả việc lấy mẫu và lượng tử hóa.
- **Biểu diễn màu (Color Representation)** = các hệ màu như RGB, Grayscale, HSV.