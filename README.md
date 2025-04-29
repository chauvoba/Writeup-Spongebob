# Writeup-Spongebob
Writeup CTF Cậu bé bọt biển
Một thử thách tìm kiếm thông điệp bị ẩn tại Viblo CTF, link dẫn đến thử thách: https://ctf.viblo.asia/puzzles/spongebob-spongebob-f6zdxekrcdy

# Đề bài 
<img width="518" alt="image" src="https://github.com/user-attachments/assets/1a36c533-9bb4-48b8-b2fb-b45bb49961ca" />

# Phân tích
Đầu tiên chúng ta tải về file image.zip được đính kèm đề bài. Giải nén & mở ảnh lên sẽ là Spongebob - Nhân vật hoạt hình khá nổi tiếng trong phim hoạt hình Cậu bé bọt biển. 
<img width="194" alt="image" src="https://github.com/user-attachments/assets/bc660612-c3bb-4194-9af6-dfe2c43650ff" />

Chú ý đến tên được đặt cho ảnh của Spongebob, ta thấy tác giả đặt tên cho ảnh là "lsb_image.png"
<img width="397" alt="image" src="https://github.com/user-attachments/assets/cdc48122-8325-474c-9a9b-76e290239b4a" />

Kết hợp với gợi ý từ đề bài (Stego), chúng ta có thể nhận ra ngay một cơ chế ẩn giấu thông điệp bên trong một bức ảnh rất nổi tiếng, với tên gọi là Least Significant Bit (LSB). Cùng nói sơ qua một chút về LSB: 
+ Chúng ta biết được rằng một bức ảnh được cấu thành nên từ rất nhiều pixel, và các pixel này được tạo nên từ các chuỗi nhị phân gồm các bit giá trị (Với value là 0 hoặc 1)
+ Các bit giá trị này sẽ quyết định đến màu sắc của một bức ảnh. Tuy nhiên, sẽ có các bit nằm ở cuối các chuỗi nhị phân, mà nếu như giá trị có thay đổi thì cũng sẽ không ảnh hưởng quá nhiều đến chất lượng hoặc màu sắc của bức ảnh (Ví dụ minh họa 10100000 -> 10100001)
+ Cơ chế ẩn giấu thông điệp LSB được thực hiện bằng cách thay đổi các bit giá trị cuối và ít quan trọng nhất này thành các bit giá trị chứa thông điệp cần được mã hóa. Thông thường, thông điệp mã hóa sẽ được nhúng tuần tự vào các chuỗi nhị phân theo tuần tự (Trong một số trường hợp cũng có thể làm ngược lại)

# Bài giải 
Chúng ta bắt đầu giải. Mở google và tìm kiếm một trang web Decode LSB bất kỳ có ở trên mạng. Upload ảnh lên và thực hiện Decode. Khi thành công, chúng ta sẽ nhận được thông điệp sau, sau khi loại trừ các giá trị lặp còn lại: ZmxhZ3toaWRkZW5fdGV4dF9pbWFnZV9sc2J9
<img width="894" alt="image" src="https://github.com/user-attachments/assets/984cee5e-269c-419d-9322-74b327bab105" />

Nhìn vào chuỗi giá trị này, chúng ta đoán rằng trông nó rất giống với các thông điệp mã hóa sử dụng Base64. Vì vậy, thực hiện copy chuỗi giá trị này và tiếp tục tìm kiếm bất kỳ một trang web Decode online nào đó để thực hiện giải mã. 
<img width="465" alt="image" src="https://github.com/user-attachments/assets/387dc80d-d280-4615-a498-745fd8e3de1a" />

