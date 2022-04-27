# <div align="center"><p> Sqlinjection Final - Redtigers/Level_2</p></div>
 ## Họ và tên: Mai Thị Hoàng Yến
 ## Ngày báo cáo: Ngày 27/4/2022
 ### MỤC LỤC
   [Simple login-bypass](#gioithieu)
   
### Nội dung báo cáo 
#### Simple login-bypass-level_2 <a name="gioithieu"></a>
 - B1: Đầu tiên chúng ta thử nhập `username=1` và `password=1`. Chúng ta sẽ bật on proxy lên và nhấn login.

   ![image](https://user-images.githubusercontent.com/101852647/165547892-3811cb13-f1c3-4e2f-9d95-710c2132016e.png)
   
 - B2: Click chuột phải và chọn `send to intruder`.

   ![image](https://user-images.githubusercontent.com/101852647/165543542-5f3954f4-990a-4280-b2ab-208d4c2ddbe5.png)

 - B3: Sau đó chúng ta vào tool intruder và nhấn `clear`

   ![image](https://user-images.githubusercontent.com/101852647/165543841-c90eb214-d4d9-4866-b410-2307a4c42ea7.png)

 - B4: Sau đó nhấn `add` số 1 của username và password.

   ![image](https://user-images.githubusercontent.com/101852647/165544183-f7a361cb-42d3-4b4f-a9ef-f4ef90f7eef1.png)

 - B5: Sau đó chọn `cluster bomb`.

   ![image](https://user-images.githubusercontent.com/101852647/165544400-2fcac70f-a097-4898-8caf-113d020aa33f.png)

 - B6: Tiếp theo click sang payload và `Add` những câu lệnh cần chèn cho username vào simple list.

   ![image](https://user-images.githubusercontent.com/101852647/165544762-7f236bff-a33a-453d-91c4-5f1f706f9000.png)

 - B7: Tiếp tục `Add` những câu lệnh cần chèn cho password vào simple list.

   ![image](https://user-images.githubusercontent.com/101852647/165544967-549eaaea-62c6-42b4-acbb-c3f7410fa8a6.png)
   
 - B8: Click `Start attack` và chúng ta sẽ kiểm tra xem câu lệnh nào là hợp lý để chúng ta có thể khai thác. Nhấn vào dòng có `lenght=650` và thấy `reponse` trả về cho chúng ta là kết quả lỗi. Như vậy chứng tỏ là những câu có độ dài là `650` không phải là câu lệnh chúng ta cần.

   ![image](https://user-images.githubusercontent.com/101852647/165545932-69b29875-2062-496e-a458-119bbeed7a3a.png)

 - B9: Tiếp tục khai thác thì thấy xuất hiện các dòng có `lenght=910` khác với lúc nãy nên chúng ta nhấn vào xem thử và thấy `reponse` trả về cho chúng ta là trang web đã được login. Thế là chúng ta có thể chọn những câu lệnh có lenght=910 để login.

   ![image](https://user-images.githubusercontent.com/101852647/165546496-066cbe78-922d-4753-8d03-a3fae11597d9.png)

 - B10: Bây giờ chúng ta thử đăng nhập xem thử là các câu lệnh đó có đúng là login được không. Chúng ta thử login `username = admin'--` và `password = ' or 1=1#` và kết quả là chúng ta đã đăng nhập thành công rồi (^_^).

   ![image](https://user-images.githubusercontent.com/101852647/165547224-6ec037cc-28d8-4b8d-bd58-e5af747a11bf.png)


