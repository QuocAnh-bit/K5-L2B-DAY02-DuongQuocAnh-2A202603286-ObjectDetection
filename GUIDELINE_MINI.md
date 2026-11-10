# Mini guideline — bài làm cá nhân

> Điền nội dung này trước khi bắt đầu gán nhãn. Giữ lại các quyết định sau khi self-QC.

## Định nghĩa lớp

| Lớp | Cách nhận biết |
| --- | --- |
| `car` | Xe con, gồm sedan, SUV, taxi và xe bán tải. |
| `truck` | Xe tải chở hàng hoặc xe đầu kéo. |
| `bus` | Xe buýt hoặc xe khách, thường có nhiều cửa sổ dọc thân. |
| `van` | Xe van hoặc minivan chở hàng hay chở người, thường có thân liền và khoang sau vuông. |

## Quy tắc chung

- Box bám sát vật thể nghĩa là: Vẽ sát phần xe nhìn thấy và lấy ít nền nhất có thể. Mỗi xe có một box.
- Vật thể bị che khuất: Nếu vẫn nhận ra loại xe, vẽ box bao phần xe nhìn thấy.
- Vật thể bị cắt bởi rìa ảnh: Vẽ box đến mép ảnh, chỉ bao phần xe còn trong khung.
- Vật thể rất nhỏ/mơ hồ: Phóng to để xem. Nếu vẫn chưa chắc là loại xe nào, ghi lại tên ảnh để hỏi giảng viên.
- Box bị trùng: Nếu hai box bao cùng một xe, giữ box có nhãn đúng. Nếu hai xe che nhau, mỗi xe vẫn có một box riêng.

## Ghi lại quyết định cho ít nhất ba ca mơ hồ

| `drive_001.jpg` | Box `car` ID 12. Xe có nóc liền khối giống van nhưng thân ngắn. | Chọn `car`. | Dáng xe ngắn và giống ô tô con hơn xe van. |
| `drive_025.jpg` | Box `car` ID 324. Xe trông dài giống van, có thể do ảnh chụp lúc xe đang chạy. | Chọn `car`. | Nhìn tổng thể, dáng xe giống ô tô con. |
| `drive_030.jpg` | Box `van` ID 426. Xe trông giống SUV nhưng thân dài hơn và có cửa trượt. | Chọn `van`. | Thân dài và cửa trượt là hai dấu hiệu giúp phân biệt chiếc xe này với SUV. |
