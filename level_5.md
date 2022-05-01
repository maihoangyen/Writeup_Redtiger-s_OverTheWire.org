# <div align="center"><p> Advanced login-bypass/Level_5</p></div>
 ## Họ và tên: Mai Thị Hoàng Yến
 ## Ngày báo cáo: Ngày 01/5/2022
 ### MỤC LỤC
   [Advanced login-bypass](#gioithieu)
   
### Nội dung báo cáo 
#### Advanced login-bypass <a name="gioithieu"></a>
- B1: Đây là màn hình chính của của trang web. Ở đây trang web cho chúng ta biết password đã được mã hóa md5.

  ![image](https://user-images.githubusercontent.com/101852647/166136389-343ad60b-153e-43c4-8de1-ebfb725ec92c.png)
  
- B2: Bây giờ chúng ta sẽ đi tìm xem nó có bao nhiêu cột bằng câu lệnh ` ' order by 1# ` thì nó trả về là `user not found`.

  ![image](https://user-images.githubusercontent.com/101852647/166136485-9db58848-ba60-4576-9c4b-bf2795d0db5e.png)

- B3: Bây giờ chúng ta sẽ đi tìm xem nó có bao nhiêu cột bằng câu lệnh ` ' order by 1,2# ` thì nó trả về là `user not found`.

  ![image](https://user-images.githubusercontent.com/101852647/166136521-070c85b8-dd27-40a9-9d12-3578dd4944e8.png)

- B4: Bây giờ chúng ta sẽ đi tìm xem nó có bao nhiêu cột bằng câu lệnh ` ' order by 1,2,3# ` thì nó trả về lỗi warning. Vậy chúng ta sẽ đoán nó có 2 cột.

  ![image](https://user-images.githubusercontent.com/101852647/166136550-bf046305-b762-4695-9c28-cde54d05e886.png)

- B5: Tiếp tục chúng ta nhập `username= ' union select 1,2#` và `password=pasword` nhưng vẫn không đăng nhập được. 

  ![image](https://user-images.githubusercontent.com/101852647/166136633-2c6f8153-0971-446a-9359-c48a8a4621b3.png)

- B6: Mặc dù đã thử đổi lại `username= ' union select 1,password#` và `password=pasword` nhưng đã xảy ra lỗi.

  ![image](https://user-images.githubusercontent.com/101852647/166136717-ae40bb53-b7fb-441a-80d2-c62c1c52f07a.png)
  
- B7: Do yêu cầu lúc đọc trang web là nó yêu yêu cầu password được mã hóa md5 nên tôi thử chuyển sang md5 xem sao.

  ![image](https://user-images.githubusercontent.com/101852647/166136738-c6d31c63-c524-46c9-85cd-fb494c6d65f2.png)

- B8: Copy đoạn mã hóa md5 và bắt đầu khai thác nhập lại `username= ' union select 1,'5f4dcc3b5aa765d61d8327deb882cf99
'#` và `password=pasword` thì may mắn là chúng ta đã đăng nhập thành công.

  ![image](https://user-images.githubusercontent.com/101852647/166136897-d4462c5f-e59d-43d8-a46a-54108597c87d.png)
  
- B9: Đây là màn hình sau khi chúng ta đã đăng nhập thành công.

  ![image](https://user-images.githubusercontent.com/101852647/166136868-17e9def1-1338-4f75-a3b8-f53d18cba9d4.png)

