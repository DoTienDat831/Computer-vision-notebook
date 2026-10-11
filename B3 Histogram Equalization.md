PDF - Probability Density Function (Hàm mật độ xác suất)
- Ký hiệu: p(r)
- Định nghĩa: mô tả mức độ xuất hiện của giá trị mức xám r.
- p(rk) = nk / n
	- nk: số pixel có giá trị rk
	- n: tổng số pixel

CDF - Cummulative Distribution Function (Hàm phân bố tích lũy)
- Ký hiệu: T(r) hoặc P(R <= r)
- Định nghĩa: là **tổng xác suất tích lũy từ mức xám nhỏ nhất đến mức xám đang xét**.
```
|Mức xám|PDF|CDF|
|--:|--:|--:|
|0|0.20|0.20|
|1|0.30|0.50|
|2|0.40|0.90|
|3|0.10|1.00|

CDF(2) = PDF(0) + PDF(1) + PDF(2) = 0.2+0.3+0.4 =  0.9 

Nghĩa là **90% pixel có mức xám ≤ 2**.
```

Histogram của ảnh kỹ thuật số
- Biểu đồ tần suất của một ảnh số với các giá trị màu xám r0, r1, ..., rL-1 là hàm rời rạc:
	- p(rk) = nk / n
		- rk: mức xám thứ k với k = 0, 1, ..., L-1
		- nk: số lượng pixel trong ảnh có giá trị xám bằng rk
		- n: tổng số pixel trong toàn ảnh
		- L: tổng số mức xám có thể có (ví dụ 256 đối với ảnh 8-bit)
- Hàm p(rk) biểu thị phần tỷ lệ (fraction) của tổng số pixel có giá trị màu xám rk.

Một vài loại Histogram

![[Pasted image 20261006210922.png|281]]![[Pasted image 20261006211006.png|293]]![[Pasted image 20261006211016.png|287]]![[Pasted image 20261006211046.png|286]]


Histogram Equalization
- Thiết kế một phép biển đổi T(.) sao cho các giá trị màu xám trong ảnh đầu ra được phân bố đều trong khoảng [0, 1].

Triển khai Histogram Equalization
- Đối với hình ảnh có các giá trị màu xám rời rạc, tính toán:
- $$
p_{in}(r_k) = \frac{n_k}{n}
\qquad
0 \le r_k \le 1
\qquad
0 \le k \le L - 1
$$
	- L: tổng số mức độ màu xám
	- nk: số lượng pixel có giá trị màu xám rk
	- n: Tổng số pixel trong ảnh
- Dựa trên CDF, tính toán phiên bản rời rạc của phép biến đổi trước đó:
- $$
- s_k = T(r_k) = \sum_{j=0}^{k}(p_{in})(r_j)
\qquad
0 \le k \le L-1$$
Ví dụ: Áp dụng histogram equalization
$$
[ A= \begin{bmatrix} 1&1&5&5&0&0&1&0\\ 1&1&2&2&0&1&0&1\\ 1&7&6&6&5&5&0&0\\ 0&7&6&7&5&5&5&5\\ 4&7&6&7&3&5&7&0\\ 1&1&4&1&6&5&6&1\\ 2&2&4&1&1&5&1&1\\ 1&2&2&0&0&0&0&5 \end{bmatrix} ]$$

- Ảnh 8 x 8 = 64 pixel
- Mức xám [0, 7]
- L = 8  (8 mức xám)

Tính Histogram: Đếm số lần xuất hiện của từng mức xám
- rk nk
- 0 13
- 1 17
- 2 6
- 3 1
- 4 3
- 5 12
- 6 6
- 7 6
- Tổng: 64

Tính PDF
$$
p(r_k)=n_k/L$$
rk=1 => p(rk) = 13/64 = 0.203125


| $r_k$ | $n_k$ | $p(r_k)$ |
| ----- | ----- | -------- |
| 0     | 13    | 0.203125 |
| 1     | 17    | 0.265625 |
| 2     | 6     | 0.09375  |
| 3     | 1     | 0.015625 |
| 4     | 3     | 0.046875 |
| 5     | 12    | 0.187500 |
| 6     | 6     | 0.09375  |
| 7     | 6     | 0.09375  |

Tính CDF (Tổng tích lũy PDF)

| $(r_k)$ | $(n_k)$ |      PDF |      CDF |
| ------: | ------: | -------: | -------: |
|       0 |      13 | 0.203125 | 0.203125 |
|       1 |      17 | 0.265625 | 0.468750 |
|       2 |       6 | 0.093750 | 0.562500 |
|       3 |       1 | 0.015625 | 0.578125 |
|       4 |       3 | 0.046875 | 0.625000 |
|       5 |      12 | 0.187500 | 0.812500 |
|       6 |       6 | 0.093750 | 0.906250 |
|       7 |       6 | 0.093750 | 1.000000 |

Tính mức xám mới
$s_k=(L-1)CDF(r_k)$
L = 8

$$
s_k=7CDF(r_k)
$$
| \(r_k\) |      CDF | \(7\times CDF\) | Mức mới |
| ------: | -------: | --------------: | ------: |
|       0 | 0.203125 |        1.421875 |   **1** |
|       1 | 0.468750 |        3.281250 |   **3** |
|       2 | 0.562500 |        3.937500 |   **4** |
|       3 | 0.578125 |        4.046875 |   **4** |
|       4 | 0.625000 |        4.375000 |   **4** |
|       5 | 0.812500 |        5.687500 |   **6** |
|       6 | 0.906250 |        6.343750 |   **6** |
|       7 | 1.000000 |        7.000000 |   **7** |
