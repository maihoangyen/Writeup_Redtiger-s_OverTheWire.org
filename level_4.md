# <div align="center"><p> Blind Injection/Level_4</p></div>
 ## Họ và tên: Mai Thị Hoàng Yến
 ## Ngày báo cáo: Ngày 30/4/2022
 ### MỤC LỤC
   [Blind Injection](#gioithieu)
   
### Nội dung báo cáo 
#### Blind Injection-level_4 <a name="gioithieu"></a>
- B1: Đây là màn hình chính của trang web. Phân tích trang web ta thấy người ta đã cho chúng ta biết thêm thông tin `table level4_secret và column keyword`.

  ![image](https://user-images.githubusercontent.com/101852647/166135828-a34c9508-9b0e-47b7-8683-c7f7c4423182.png)

- B2: Nhấn thử vào `click me`. Và thấy nó trả về `id=1` và dòng `Query returned 1 rows`. Tiếp tục thử `id=0` và `id=2` thì nó trả về dòng `Query returned 0 rows`. Vì vậy, chúng ta sẽ lấy `id=1` để khai thác.

   ![image](https://user-images.githubusercontent.com/101852647/166135899-58cdd1a2-c09c-4a70-ae17-b59e15aeac66.png)

   ![image](https://user-images.githubusercontent.com/101852647/166135905-bfdf7c70-d1ef-45dc-ab3c-6cc049ddc9ca.png)

   ![image](https://user-images.githubusercontent.com/101852647/166135913-acaea5f0-20ff-4efc-a539-9d10837f9591.png)

- B3: Chúng ta sẽ sử dụng burpsuite tìm xem thử keyword chúng ta cần tìm có độ dài bao nhiêu bằng câu lệnh `id=1 and 1=(select length(keyword)=1 from level4_secret)`.

   ![image](https://user-images.githubusercontent.com/101852647/166136005-db4a6801-d854-4a02-a95c-410cfa270f18.png)

- B4: Chúng ta sẽ add simple list từ 1->50 để payload.

   ![image](https://user-images.githubusercontent.com/101852647/166136056-a83caf7f-60ee-4c9e-8cfd-a9e15807d544.png)

- B5: Bắt đầu start attack và nhấn thử bất kỳ dòng nào thì thấy từ dòng 1->20 và từ 22->50 nó trả về dòng `Query returned 0 rows`.

   ![image](https://user-images.githubusercontent.com/101852647/166136117-7ca78ba7-daf9-45e0-9528-647c1392cc98.png)
   
- B6: Dòng 21 trả về cho chúng ta kết quả là `Query returned 1 rows`. CHúng ta đoán đây là độ dài của keyword.

   ![image](https://user-images.githubusercontent.com/101852647/166136162-8f1a2b71-1d66-4acd-b805-294e942632af.png)

- B7: Mặc dù đã thử rất nhiều cách payload khác nhau nhưng vẫn không khai thác được nên chúng ta thử sử dụng python để khai thác. Sau khi thử chạy file `level4.py` thì nó đã trả về kết quả cho chúng ta keyword.

   ![image](https://user-images.githubusercontent.com/101852647/166136240-cadb48af-48c1-4239-9dbd-78d8e23452f6.png)

- B8: Thử nhập keyword và chúng ta đã đăng nhập thành công.

    ![image](https://user-images.githubusercontent.com/101852647/166136254-e63acd68-5fa6-4c2c-9871-0895e593b31a.png)

