# <div align="center"><p> SQL-Injection/Level_10</p></div>
 ## Họ và tên: Mai Thị Hoàng Yến
 ## Ngày báo cáo: Ngày 07/5/2022
 ### MỤC LỤC
   [SQL-Injection](#gioithieu)
   
### Nội dung báo cáo 
#### SQL-Injection <a name="gioithieu"></a>
- B1: Đây là trang web của level10.

  ![image](https://user-images.githubusercontent.com/101852647/167065644-f55a2142-2190-4683-8ff7-e64a76b210b0.png)

- B2: Ta sẽ sử dụng burpsuite để khai thác vì chúng ta không thể chèn trực tiếp trên trang web được. Ta thấy sau khi nhấn login thì nó trả về cho chúng ta 1 chuỗi mã hóa.

  ![image](https://user-images.githubusercontent.com/101852647/167065807-dd594352-fbe9-46c6-97f8-70c6a3e51484.png)

- B3: Chúng ta sẽ đi decode để xem ta lấy được thông tin gì không. Kết quả trả về `a:2:{s:8:"username";s:6:"Monkey";s:8:"password";s:12:"0815password";}` Sau khi decode chúng ta thấy được tên đăng nhập và password nhưng đây không phải là thứ ta cần vì từ đầu trang web đã gợi ý cho chúng ta là đăng nhập với tên là `TheMaster`.

  ![image](https://user-images.githubusercontent.com/101852647/167065940-7f82d868-0f55-4022-ba28-a96aa4eebb7f.png)

- B4: Bây giờ chúng ta sẽ copy đoạn decode này và sửa chúng theo mục đích khai thác của chúng ta `a:2:{s:8:"username";s:9:"TheMaster";s:8:"password";s:8:"password";}`. Sau đó, chúng ta sẽ lấy nó và đem đi encode và lấy chuỗi encode đó thử đăng nhập. Nhưng kết quả trả về là đăng nhập sai.

  ![image](https://user-images.githubusercontent.com/101852647/167066327-ff70508e-5981-46ee-b42c-d02d7da0c0bb.png)
  
  ![image](https://user-images.githubusercontent.com/101852647/167066649-f946114c-25f9-49ab-9186-ea47562685cb.png)


- B5: Nếu vậy thì chúng ta sẽ cho giá trị mặc định của password luôn luôn đúng với `Boolean=True` tương ứng với `b:1` và câu lệnh khai thác như sau `a:2:{s:8:"username";s:9:"TheMaster";s:8:"password";b:1;}`. Ta sẽ encode và thử đăng nhập.

  ![image](https://user-images.githubusercontent.com/101852647/167066781-ca889466-f4bc-4a8d-8ea4-6156576d92b9.png)

- B6: Sau khi nhập `YToyOntzOjg6InVzZXJuYW1lIjtzOjk6IlRoZU1hc3RlciI7czo4OiJwYXNzd29yZCI7YjoxO30=` thì đã đăng nhập thành công.

  ![image](https://user-images.githubusercontent.com/101852647/167066898-abce1a87-1b3f-4c56-bac1-d73ef89ca33c.png)
