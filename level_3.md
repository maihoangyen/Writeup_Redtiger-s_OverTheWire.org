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

- B3: Chúng ta nhấn vào siêu liên kết thứ 2 `Admin`. Ngoài biết thêm thông tin chúng ta hãy để ý trên thanh url có một đoạn mã hóa đó là ` usr=MDQyMjExMDE0MTgyMTQw`. Nhưng chúng ta không biết đây là mã hóa gì ngay cả khi dùng hashid để tìm được tên mã hóa nhưng cũng không tìm thấy. Bây giờ phải chèn thử vào usr để xem nó có thông báo lỗi gì không.

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

- B7: Nhấn thử vào dòng có ` lenght=666` xem ta có khai thác được gì không thì thấy nó trả về trang web ban đầu. Chứng tỏ đây không phải là ký tự ta cần chèn.

  ![image](https://user-images.githubusercontent.com/101852647/165921735-f7a77441-884c-46f3-a3c5-04ec7b758629.png)

- B8: Sau một hồi ông bà gánh còng lưng thì đã xuất hiện dòng có ` lenght=817` nhấn vào xem thử xem sao nó trả về cho chúng ta một dòng lỗi.

  ![image](https://user-images.githubusercontent.com/101852647/165922396-d73d05c3-edd8-45a0-a5d0-3be7bc4e42f5.png)

- B9: Để ý mà xem trong dòng lỗi nó chỉ đến đường dẫn lỗi thử mở file đó lên xem có gì nào. Ta có thể thấy trong này có đoạn code của mã hóa và giải mã base64 được viết bằng php.

  ![image](https://user-images.githubusercontent.com/101852647/165923079-2cae52f4-117d-49ba-bba8-0481c379c4a2.png)

- B10: Chúng ta sẽ lợi dụng đoạn code này để chèn vào url và khai thác trang web nên chúng ta chỉ lấy đoạn encode. Đối với sự lười nhát của tôi thì tôi sẽ encode online bằng cách truy cập đường link `https://onlinephpfunctions.com/base64-encode/manual` này nhé và copy đoạn encode vào để có thể bắt đầu khai thác. Đầu tiên chúng ta nhập thử `Admin` xem nó mã hóa giống như trang web hay không.

  ![image](https://user-images.githubusercontent.com/101852647/165924168-a710a223-d36e-4c3b-86b3-dfba81e06fac.png)

- B11: Bây giờ chúng ta thử tìm xem là trang web có bao nhiêu cột bằng câu lệnh ` Admin' order by 1-- -` và cứ như thế đến `Admin`. Chứng tỏ có 7 cột' order by 1,2,3,4,5,6,7,8-- -` thì gặp lỗi. Chứng tỏ có 7 cột.
   
  ![image](https://user-images.githubusercontent.com/101852647/165924958-4eaab1af-271f-4695-8a8c-99b17bd68160.png)

  ![image](https://user-images.githubusercontent.com/101852647/165925830-c71573a6-8860-4baf-a3ce-821c883ec40e.png)

- B12: chúng ta sẽ sử dụng câu lệnh `1'  union select  1,null,null,null,null,null,null-- -` đến câu lệnh `1'  union select  null,null,null,null,null,null,1-- -` để thử xem là chúng ta có thể chèn username và password ở cị trí nào.Chúng ta thử hết 7 vị trí và thấy vị trí thứ 2 chèn đưuọc số 1 còn vị trí số một thì không.

  ![image](https://user-images.githubusercontent.com/101852647/165929075-a9d87945-2a7a-447e-807c-d11246810dd0.png)
  
  ![image](https://user-images.githubusercontent.com/101852647/165928865-74827223-bfe0-4b7a-a306-28f12d4bb50a.png)

- B13: Do ng ta đã cho chúng ta biết trước `username= Admin` rồi nên chúng ta chỉ cần chèn `password` bằng câu lệnh `1' union select null,password,null,null,null,null,null from level3_users where username='Admin`thôi cho nó nhanh.

  ![image](https://user-images.githubusercontent.com/101852647/165930522-1105acf2-099b-46de-933b-ac8e38084d67.png)

- B14: Chúng ta đăng nhập thử `username=Admin` và `password=thisisaverysecurepasswordEEE5rt` và chúng ta đã đăng nhập thành công(^-^).

  ![image](https://user-images.githubusercontent.com/101852647/165931006-051bfe17-a377-403f-b5ae-8a78937ff610.png)
 
