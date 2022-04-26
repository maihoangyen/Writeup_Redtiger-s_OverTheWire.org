# <div align="center"><p> Sql_injection-level2 </p></div>
 ## Họ và tên: Mai Thị Hoàng Yến
 ## Ngày báo cáo: Ngày 26/4/2022
 ### MỤC LỤC
   [Simple SQL-Injection](#gioithieu)
   
### Nội dung báo cáo 
#### Simple SQL-Injection-level_1 <a name="gioithieu"></a>
- B1: Đầu tiên chúng ta phân tích một chút về trang web bên dưới. Ở đây, có thể thấy người ta đã gợi ý cho chúng ta tên user là `Hornoxe` , tên bảng là `Tablename: level1_users` và `Category: 1`. Đây là những thông tin cần thiết để khai thác được username và password.

   ![image](https://user-images.githubusercontent.com/101852647/165264257-d39704db-e32e-4129-b392-6a533f14b9ca.png)

- B2: Bây giờ, chúng ta sẽ khai thác bằng cách sử dụng công cụ burpsuite. Chúng ta nhấn vào  `Category: 1` thì nó trả về cho chúng ta `My cats are sweet.Miau`.

   ![image](https://user-images.githubusercontent.com/101852647/165264836-f3bca570-a15b-40dd-a14b-fae378419c09.png)

- B3: Chúng ta tiếp tục nhập `cat=2` xem có gì xảy ra không thì thấy nó trả về cho chúng ta dòng `This category does not exist!`. Như vậy, chúng ta sẽ sử dụng `cat=1` để khai thác tiếp.

   ![image](https://user-images.githubusercontent.com/101852647/165265085-0b14f734-203c-4f97-9665-d4e02eea8abb.png)

- B4: Tiếp tục chúng ta sử dụng câu lệnh ` cat=1 order by 1--` để xem thử nó có bao nhiêu cột. Chúng ta nhìn thấy nó trả về dòng `My cats are sweet.Miau`. Như vậy chúng ta sẽ tiếp tục khai thác xem nó còn bao nhiêu cột nữa.

   ![image](https://user-images.githubusercontent.com/101852647/165265835-b2e178af-ab0e-45d9-86d7-2140d1694dd6.png)
   
- B5: Tiếp tục chúng ta sử dụng câu lệnh ` cat=1 order by 1,2--` để xem thử nó có bao nhiêu cột.

   ![image](https://user-images.githubusercontent.com/101852647/165266430-da3460c0-f2ba-49cf-964d-14dbd90fd894.png)

- B6: Tiếp tục chúng ta sử dụng câu lệnh ` cat=1 order by 1,2,3--` để xem thử nó có bao nhiêu cột.

   ![image](https://user-images.githubusercontent.com/101852647/165266654-e2f29a9e-2ece-435b-af95-b1b2db7772f3.png)

- B7: Tiếp tục chúng ta sử dụng câu lệnh ` cat=1 order by 1,2,3,4--` để xem thử nó có bao nhiêu cột.

   ![image](https://user-images.githubusercontent.com/101852647/165266708-9ebb83ef-517a-424a-b05f-d5e18284a99e.png)

- B8: Tiếp tục chúng ta sử dụng câu lệnh ` cat=1 order by 1,2,3,4,5--` để xem thử nó có bao nhiêu cột. Đến bước thứ 5 chúng ta thấy nó xuất hiện `This category does not exist!` chứng tỏ là nó sẽ có 4 cột. 

   ![image](https://user-images.githubusercontent.com/101852647/165266776-f1e0f561-61a1-4d30-8a5b-6e27adabc893.png)
   
- B9: Chúng ta sẽ sử dụng câu lệnh ` cat=1 union select 1,null,null,null from level1_user` để xem thử là nó chúng ta sẽ lấy được username và password ở vị trí nào. Ở vị trí thứ 1 ta thấy nó trả về chúng ta dòng `This category does not exist!`. Tiếp tục khai thác. 

  ![image](https://user-images.githubusercontent.com/101852647/165267782-7d30bb78-fa49-4700-bd7f-11e44dd6ca6c.png)

- B10: Tương tự như vậy, chúng ta sẽ sử dụng câu lệnh ` cat=1 union select null,1,null,null from level1_user`.

  ![image](https://user-images.githubusercontent.com/101852647/165268000-eb27e406-fba9-47c8-b937-7fbf44debb48.png)

- B11: Tương tự như vậy, chúng ta sẽ sử dụng câu lệnh ` cat=1 union select null,null,1,null from level1_user`. Ở vị trí này chúng ta thấy nó đã xuất hiện số `1` ngay dưới dòng `My cats are sweet.Miau`.Chính là nó.

  ![image](https://user-images.githubusercontent.com/101852647/165268119-4459025e-8cbb-4567-af11-7a8522d1a981.png)
  
- B12: Tương tự như vậy, chúng ta sẽ sử dụng câu lệnh ` cat=1 union select null,null,null,1 from level1_user`. Ở vị trí này chúng ta thấy nó đã xuất hiện số `1` ngay dưới dòng `My cats are sweet.Miau` . Như vậy, chúng ta có thể sử dụng vị trí thứ 3,4 để khai thác username và password.

  ![image](https://user-images.githubusercontent.com/101852647/165269086-e9de7fc0-e066-4780-aa8a-dc8074371a9b.png)

- B13: Bây giờ chúng ta sẽ sử dụng câu lệnh ` cat=1 union select 1,1,username,password from level1_users`. Chúng ta đã lấy thành công username `Hornoxe` và password `thatwaseasy`.

  ![image](https://user-images.githubusercontent.com/101852647/165270001-ed9b3440-8649-4347-9e5a-2c4c8b98483e.png)

- B14: Bây giờ chúng ta thử đăng nhập xem thử thành công không. Như vậy là chúng ta đã đăng nhập thành công rồi (^_^).

  ![image](https://user-images.githubusercontent.com/101852647/165270387-a52e77e9-e676-40c2-8aa0-9e59e805169b.png)
