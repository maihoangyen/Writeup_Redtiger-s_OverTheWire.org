# <div align="center"><p> SQL-Injection/Level_6</p></div>
 ## Họ và tên: Mai Thị Hoàng Yến
 ## Ngày báo cáo: Ngày 02/5/2022
 ### MỤC LỤC
   [SQL-Injection](#gioithieu)
   
### Nội dung báo cáo 
#### SQL-Injection <a name="gioithieu"></a>
- B1: Đây là màn hình chính của trang web . Trang web cho chúng ta biết thêm thông tin là ` table level6_users` và `status 1`

  ![image](https://user-images.githubusercontent.com/101852647/166182323-7faffe4f-f301-4b49-a309-0c4aba66ed8f.png)

- B2: Nhấn vào thử click me thì trang web trả về chúng ta `user=1`.

  ![image](https://user-images.githubusercontent.com/101852647/166182425-05bc47f9-3355-42f6-bbf3-f9d770f451c5.png)

- B3: Bây giờ chúng ta dùng burpsuite để thử tìm cột bằng lệnh ` order by 1,2,3,4,,5,6#` bắt đầu từ 1->6 thì thấy khi đến vị trí thứ 6 nó thông báo lỗi chứng tỏ nó có 5 cột.

  ![image](https://user-images.githubusercontent.com/101852647/166182563-75a1241b-b088-470f-ae30-6f39ab00e610.png)

  ![image](https://user-images.githubusercontent.com/101852647/166182579-3cef1974-e09e-4939-b6eb-25bacbf040d1.png)

  ![image](https://user-images.githubusercontent.com/101852647/166182596-5fd057a8-c1ca-4f41-9930-3ac047f095d5.png)

- B4: Bây giờ thử tìm vị trí để chèn bằng câu lệnh `' union select 1,null,null,null,null#` nhưng vẫn không tìm được vị trí chèn . Mặc dù thử lại bằng câu lệnh`' union select username,null,null,null,null#` vẫn không được.

  ![image](https://user-images.githubusercontent.com/101852647/166182974-7b62c437-7bb0-4eb5-9012-72808049a23b.png)

  ![image](https://user-images.githubusercontent.com/101852647/166182988-696905f3-8c0f-4e41-bf30-2991ba28e8f7.png)

  ![image](https://user-images.githubusercontent.com/101852647/166182997-3ecd66e0-bf73-412f-b065-d67509d17785.png)

- B5: Chúng ta sẽ thử mã hóa hệ hex để chúng có thể đọc được lệnh chúng ta . Mã hóa câu lệnh `' union select 1,2,3,4,5#` về dạng hex và thử chèn vào các vị trí. 

  ![image](https://user-images.githubusercontent.com/101852647/166183303-5ba3efdb-eb15-4ddb-89c7-47fe0a5d350b.png)
  
- B6: Chúng ta sẽ chèn vào các vị trí từ 1->5 nó trả về là `User not found`. 
  
  ![image](https://user-images.githubusercontent.com/101852647/166183374-2b1c52ca-874b-4bbb-bcc4-f381539bd70e.png)
  
- B7: Khi chèn tới vị tí thứ hai thì thấy nó trả về cho ta kết quả còn các vị trí còn lại đều trả về là `User not found`. Chúng ta sẽ lợi dụng vị trí này để tìm được username và password.
  
  ![image](https://user-images.githubusercontent.com/101852647/166183426-e26ad0b7-a580-4076-8b07-d87e27cc7e11.png)
  
- B7: Sau bước trên kết quả trả về cho chúng ta vị trí thứ 2 và 4 thì bây giờ chúng ta sẽ mã hóa câu lệnh `' union select 1,username,3,password,5 from level6_users where status=1#` để khai thác username và password.

  ![image](https://user-images.githubusercontent.com/101852647/166183604-016c6ce0-fd31-447e-89a2-cbde24afa1c8.png)

  ![image](https://user-images.githubusercontent.com/101852647/166183701-0bc3dc76-9172-43c6-8db2-7209f98b464c.png)

- B8: Chúng ta lấy `username=admin` và `password=m0nsterk1ll` để đăng nhập.

  ![image](https://user-images.githubusercontent.com/101852647/166183854-5ca87df3-75a2-44b6-8cad-abf0769c3db2.png)
