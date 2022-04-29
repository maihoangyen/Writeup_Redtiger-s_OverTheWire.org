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

- B3: Chúng ta nhấn vào siêu liên kết thứ 2 `Admin`. Ngoài biết thêm thông tin chúng ta hãy để ý trên thanh url có một đoạn mã hóa đó là ` usr=`

  ![image](https://user-images.githubusercontent.com/101852647/165913436-ec15079f-c7bf-4964-a7ad-29e231ba8791.png)
  
  ![image](https://user-images.githubusercontent.com/101852647/165913793-01474bee-2b5e-4fa1-8066-423c65f17e3d.png)

