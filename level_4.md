# <div align="center"><p> Get an error/Level_4</p></div>
 ## Họ và tên: Mai Thị Hoàng Yến
 ## Ngày báo cáo: Ngày 30/4/2022
 ### MỤC LỤC
   [Get an error](#gioithieu)
   
### Nội dung báo cáo 
#### Get an error-level_4 <a name="gioithieu"></a>
- B1: Đây là màn hình chính của trang web. Phân tích trang web thì thấy người ta đã cho chúng ta biết tên table `level4_secret` cột `keyword`.

  ![image](https://user-images.githubusercontent.com/101852647/166101959-60d71821-ba61-4140-b333-d17b38ebe9a7.png)
  
- B2: Nhấn vào `click me` sẽ thấy trên thanh url có `id=1` và dòng `Query returned 1 rows` . Tiếp tục thử `id=0` và `id=2` thì thấy trang web trả về dòng `Query returned 0 rows`. Vậy mình sẽ lấy `id=1`.

  ![image](https://user-images.githubusercontent.com/101852647/166102055-40c59970-5a8a-4078-a39b-fe9eca743a06.png)

  ![image](https://user-images.githubusercontent.com/101852647/166102042-ce471b63-0893-4579-bc64-9f9710c925b1.png)
  
  ![image](https://user-images.githubusercontent.com/101852647/166102064-467bab60-e942-4d2e-a06c-d30489961eb2.png)

- B3: Để tìm keyword trước tiên chúng ta tìm độ dài của nó bằng câu lệnh`id=1 and 1=(select length(keyword)=1 from level4_secret)`. Sử dụng intruder của burpsuite khai thác cho nhanh bằng cách add 1 và bắt đầu payload.

  ![image](https://user-images.githubusercontent.com/101852647/166102208-7d567370-1551-4b45-986a-3b7ef5dec9ab.png)

- B4: Add payload thứ 1 với simple list từ 1->50 .

  ![image](https://user-images.githubusercontent.com/101852647/166102330-3f5067b0-4c46-4241-962b-08c0c634f498.png)

- B5: 


- B6: Bắt đầu start attack và nhấn thử từng dòng xem thì thấy từ 1->20 và từ 22->50 nó đều trả về `Query returned 0 rows`. Chỉ duy nhất 1 dòng 21 là nó trả về `Query returned 1 rows`. Như vậy, chúng ta có thể mạnh dạn đoán đây là độ dài của từ khóa mà mình cần tìm.

  ![image](https://user-images.githubusercontent.com/101852647/166102426-628e233a-6d46-4d27-9e63-c7a93ca439f3.png)

  ![image](https://user-images.githubusercontent.com/101852647/166102435-2169d520-5c60-4351-964b-4ab474ce8d98.png)

- B7: Mặc dù đã thử payload rất nhiều lần nhưng vẫn không có kết quả trả về nên chúng ta sẽ thử dùng python để khai thác. Chúng ta sẽ sử dụng file `level4.py` để khai thác.

  ![image](https://user-images.githubusercontent.com/101852647/166102490-a80234a9-715e-4095-8afc-0a230b6624d5.png)

- B8: Sau khi chạy thử file `level4.py` thì nó đã trả về cho chúng ta keyword là `killstickswithbr1cks!`.

  ![image](https://user-images.githubusercontent.com/101852647/166102536-9b43a528-ee78-4e48-9a61-059ee41b562f.png)

- B9: Chạy thử keyword và chúng ta đã đăng nhập thành công.

  ![image](https://user-images.githubusercontent.com/101852647/166102575-e3ab9610-0b1a-4382-a782-47326edae0b2.png)
