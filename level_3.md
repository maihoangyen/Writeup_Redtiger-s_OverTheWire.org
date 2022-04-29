# <div align="center"><p> Sqlinjection Final - Redtigers/Level_3</p></div>
 ## Họ và tên: Mai Thị Hoàng Yến
 ## Ngày báo cáo: Ngày 29/4/2022
 ### MỤC LỤC
   [Simple login-bypass](#gioithieu)
   
### Nội dung báo cáo 
#### Simple login-bypass-level_2 <a name="gioithieu"></a>
- B1: Đây là màn hình chính của level_3. Ở đây chúng ta thấy ng ta đã cho chúng ta biết thêm thông tin đó là `user= Admin`, `table=level3_users` và chúng ta thấy thêm là ng ta đã cho chúng ta 2 siêu liên kết.

  ![image](https://user-images.githubusercontent.com/101852647/165912678-3d714bb3-b6f1-416e-99a4-d7c43fd17a93.png)

- B2: Chúng ta nhấn thử vào siêu liên kết `TheCow`. Chúng ta thấy sự xuất hiện về thông tin ở trong đó.

  ![image](https://user-images.githubusercontent.com/101852647/165913282-0dab83df-a19a-4493-815d-fc414403c183.png)

- B3: Chúng ta nhấn vào siêu liên kết thứ 2 `Admin`. Ngoài biết thêm thông tin chúng ta hãy để ý trên thanh url có một đoạn mã hóa đó là ` usr=`. Nhưng chúng ta không biết đây là mã hóa gì ngay cả khi dùng hashid để tìm được tên mã hóa nhưng cũng không tìm thấy. Bây giờ phải chèn thử vào usr để xem nó có thông báo lỗi gì không.

  ![image](https://user-images.githubusercontent.com/101852647/165913436-ec15079f-c7bf-4964-a7ad-29e231ba8791.png)
  
  ![image](https://user-images.githubusercontent.com/101852647/165913793-01474bee-2b5e-4fa1-8066-423c65f17e3d.png)

- B4: Chúng ta sẽ dùng burpsuite để chèn những kí tự có trong bảng mã ascii xem sao.

  ![image](https://user-images.githubusercontent.com/101852647/165916882-88cc1f0e-ab79-4ed5-8483-c6426d3b0ec0.png)

- B5: Nhấn vào clear và bắt đầu add vào nhưng chỗ cần chèn

  ![image](https://user-images.githubusercontent.com/101852647/165917179-620df636-c8ac-4c6e-9901-29d5c4df67fe.png)

  ![image](https://user-images.githubusercontent.com/101852647/165917233-bfa20297-00cb-42d9-acf8-88c1031c418d.png)

- B6: Bắt đầu payload và chúng ta sẽ add những ký tự có trong bảng mã ascii vào trong simple list

  ![image](https://user-images.githubusercontent.com/101852647/165917555-140fc1ce-b0df-4bf7-ba27-a81f63ab8beb.png)
  
  ![image](https://user-images.githubusercontent.com/101852647/165917585-6f0bb9dc-aac6-4357-a792-dbb68da11475.png)

- B7: 
