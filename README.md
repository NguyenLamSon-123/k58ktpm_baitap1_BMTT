# k58ktpm_baitap1_BMTT
## Nội Dung Btap BMTT
### TÌM HIỂU CÁC PHƯƠNG PHÁP MÃ HOÁ CỔ ĐIỂN
Caesar
Affine
Hoán vị
Vigenère
Playfair
Với mỗi phương pháp, hãy tìm hiểu:

### Tên gọi
Thuật toán mã hoá, thuật toán giải mã
Không gian khóa
Cách phá mã (mà không cần khoá)
Cài đặt thuật toán mã hoá và giải mã bằng code C++/C#/vv  và bằng html+css+javascript

# Caesar Cipher
### Tên gọi
Mã Caesar, còn gọi là mã dịch chuyển, là một trong những phương pháp mã hóa cổ điển đơn giản nhất, được đặt tên theo Julius Caesar, người đã sử dụng nó để mã hóa thông điệp quân sự.
### Thuật toán mã hóa
 Giả sử bảng chữ cái gồm 26 chữ cái tiếng Anh (A-Z, không phân biệt hoa/thường, hoặc có thể mở rộng cho các bảng chữ cái khác).
 Đối với mỗi ký tự x trong plaintext (văn bản gốc), mã hóa thành y = (x + k) mod 26, trong đó k là khóa (số nguyên từ 0 đến 25).
 Ký tự không phải chữ cái giữ nguyên (như khoảng trắng, dấu câu).
### Thuật toán giải mã
 Đối với mỗi ký tự y trong ciphertext (văn bản mã hóa), giải mã thành x = (y - k) mod 26.
 Tương tự, ký tự không phải chữ cái giữ nguyên.
### Không gian khóa
 Không gian khóa là 26 (từ 0 đến 25), vì modulo 26. Nếu k=0 hoặc k=26, tương đương không mã hóa.
### Cách phá mã (mà không cần khóa)
 Phá mã bằng brute force: Thử tất cả 26 khóa có thể và kiểm tra văn bản giải mã nào có ý nghĩa (ví dụ: kiểm tra tần suất chữ cái hoặc từ có nghĩa trong tiếng Anh).
 Phân tích tần suất: Vì chỉ dịch chuyển, tần suất chữ cái trong ciphertext tương tự plaintext, dễ đoán k bằng cách so sánh với tần suất chuẩn (e.g., 'E' phổ biến nhất).

# Mã Affine (Affine Cipher)
### Tên gọi
Mã Affine, kết hợp nhân và cộng modulo.
### Thuật toán mã hóa

y = (a * x + b) mod 26.
Khóa cố định: a=5, b=8 (gcd(5,26)=1).

### Thuật toán giải mã

Tìm a_inv (a_inv * a ≡ 1 mod 26), x = a_inv * (y - b) mod 26.

### Không gian khóa
312 (12 giá trị a * 26 b).
### Cách phá mã (mà không cần khóa)
Brute force 312 khóa, hoặc giải hệ từ tần suất.

# Mã Hoán vị (Permutation Cipher / Transposition Cipher)
### Tên gọi
Mã Hoán vị, sắp xếp lại vị trí ký tự.
### Thuật toán mã hóa

Viết vào ma trận, đọc theo thứ tự cột sắp xếp bởi khóa.
Khóa cố định: [3,1,4,2] (4 cột).

### Thuật toán giải mã

Viết vào ma trận theo thứ tự sắp xếp, đọc theo hàng.

### Không gian khóa
n! với n=độ dài khóa (đây 4! = 24).
### Cách phá mã (mà không cần khóa)
Brute force hoán vị, anagramming.

# Mã Vigenère (Vigenère Cipher)
### Tên gọi
Mã Vigenère, đa bảng chữ cái với khóa lặp.
### Thuật toán mã hóa

y_i = (x_i + k_i) mod 26, k lặp lại.
Khóa cố định: "KEY".

### Thuật toán giải mã

x_i = (y_i - k_i) mod 26.

### Không gian khóa
26^m với m=độ dài khóa.
### Cách phá mã (mà không cần khóa)
Kasiski để tìm m, rồi phân tích tần suất.

# Mã Playfair (Playfair Cipher)
### Tên gọi
Mã Playfair, là mã thay thế digram (cặp chữ cái), sử dụng ma trận 5x5 từ khóa.
### Thuật toán mã hóa
Tạo ma trận 5x5 từ khóa (loại bỏ trùng, bỏ J hoặc hợp I/J, điền bảng chữ cái còn lại).
Plaintext chia thành cặp (digram), padding nếu cần (X cho ký tự đơn, hoặc xử lý trùng).
Đối với cặp (p1, p2):
Cùng hàng: Thay bằng ký tự phải cạnh.
Cùng cột: Thay bằng ký tự dưới.
Khác: Thay bằng góc đối diện hình chữ nhật.
### Thuật toán giải mã
Tương tự mã hóa, nhưng dịch ngược (trái cho hàng, trên cho cột).
### Không gian khóa
Với khóa là chuỗi chữ cái, không gian là số cách sắp xếp ma trận 5x5 độc đáo (rất lớn, khoảng 25! / số trùng lặp).
### Cách phá mã (mà không cần khóa)
Phân tích tần suất digram: So sánh tần suất cặp chữ cái phổ biến (e.g., TH, HE) để đoán ma trận.
Hill climbing hoặc genetic algorithm để tối ưu hóa ma trận dựa trên ngôn ngữ.
Khó hơn Caesar nhưng vẫn yếu với ciphertext dài.
