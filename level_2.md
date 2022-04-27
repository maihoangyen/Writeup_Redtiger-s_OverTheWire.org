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

   ![image](https://user-images.githubusercontent.com/101852647/165548129-ed5fb9cf-7272-4fe1-b628-73d7bbf478f5.png)

 - B3: Sau đó chúng ta vào tool intruder và nhấn `clear`

   ![image](https://user-images.githubusercontent.com/101852647/165548211-4565cc40-9c9c-4902-ae1a-9be3a6925d48.png)

 - B4: Sau đó nhấn `add` số 1 của username và password.

   ![image](https://user-images.githubusercontent.com/101852647/165548351-da6d91b4-c004-4f30-aea0-f7919c52fd9e.png)

 - B5: Sau đó chọn `cluster bomb`.

   ![image](https://user-images.githubusercontent.com/101852647/165548447-09f2b91d-e748-4406-b9eb-4e124547ca02.png)

 - B6: Tiếp theo click sang payload và `Add` những câu lệnh cần chèn cho username vào simple list.

   ![image](https://user-images.githubusercontent.com/101852647/165548545-58319d59-c7b1-456b-8456-cdc7ff805521.png)

 - B7: Tiếp tục `Add` những câu lệnh cần chèn cho password vào simple list.

   ![image](https://user-images.githubusercontent.com/101852647/165548611-59858bbd-e067-498a-9ee0-8c026b626040.png)
   
 - B8: Click `Start attack` và chúng ta sẽ kiểm tra xem câu lệnh nào là hợp lý để chúng ta có thể khai thác. Nhấn vào dòng có `lenght=650` và thấy `reponse` trả về cho chúng ta là kết quả lỗi. Như vậy chứng tỏ là những câu có độ dài là `650` không phải là câu lệnh chúng ta cần.

   ![image](https://user-images.githubusercontent.com/101852647/165548762-d17fe033-a1d8-4826-acb2-ee314b76f9b3.png)

 - B9: Tiếp tục khai thác thì thấy xuất hiện các dòng có `lenght=910` khác với lúc nãy nên chúng ta nhấn vào xem thử và thấy `reponse` trả về cho chúng ta là trang web đã được login. Thế là chúng ta có thể chọn những câu lệnh có lenght=910 để login.

   ![image](https://user-images.githubusercontent.com/101852647/165548817-35832d41-8ab6-48e5-8522-a7e76adc6e18.png)

 - B10: Bây giờ chúng ta thử đăng nhập xem thử là các câu lệnh đó có đúng là login được không. Chúng ta thử login `username = admin'--` và `password = ' or 1=1#` và kết quả là chúng ta đã đăng nhập thành công rồi (^_^).

   ![image](https://user-images.githubusercontent.com/101852647/165548878-ab5bede6-49bc-4a30-9c35-6e93cbead897.png)


