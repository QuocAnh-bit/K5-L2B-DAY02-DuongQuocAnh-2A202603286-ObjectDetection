# Báo cáo cá nhân — Ngày 2 Object Detection

## 1. Thông tin học viên

- Họ tên: Dương Quốc Anh
- MSSV: `2A202603286`
- Email: qanhanh@gmail.com
- Lớp: K5-L2B
- [Repo bài làm](https://github.com/QuocAnh-bit/K5-L2B-DAY02-DuongQuocAnh-2A202603286-ObjectDetection)
- Link Colab đã chạy: (https://colab.research.google.com/drive/1UtEpoj-vtvGsRuK2fKD9PcQsVOIhcixJ#scrollTo=NMiV8JZS4T-3)

## 2. Schema và mini guideline

Theo [mini guideline](../../GUIDELINE_MINI.md), bài dùng bốn lớp `car`, `truck`, `bus`, `van`. Mỗi xe có một box sát phần nhìn thấy. Xe bị cắt khung thì vẽ đến mép ảnh.

| Ảnh | Quyết định | Lý do |
| --- | --- | --- |
| `drive_001.jpg`, box 12 | `car` | Nóc liền giống van nhưng thân ngắn, dáng giống xe con. |
| `drive_025.jpg`, box 324 | `car` | Xe trông dài trong ảnh, nhưng dáng tổng thể giống xe con. |
| `drive_030.jpg`, box 426 | `van` | Thân dài hơn SUV và có cửa trượt. |

- Cần giảng viên làm rõ: thứ tự ID của gold set. Khi đối chiếu, gold có dấu hiệu dùng `car`, `van`, `truck`, `bus`, trong khi `data.yaml` dùng `car`, `truck`, `bus`, `van`.

## 3. Annotation và self-QC

- Số file nhãn train: **50**.
- Checker báo ** 45/50 file đúng cấu trúc**. Bản xuất ban đầu có 631 dòng trùng hệt nhau đã được gộp. ID lớp được kiểm tra khi chuyển đổi giữa bản chấm và bản train.



## 4. Gold QC và rework

| Chỉ số | Trước rework, sau khi quy đổi ID | Sau rework |
| --- | ---: | ---: |
| TP | 491 | 582 |
| FP | 188 | 102 |
| FN | 162 | 71 |
| Precision | 0,7231 | 0,8509 |
| Recall | 0,7519 | 0,8913 |
| F1 | 0,7372 | 0,8706 |
| `mean_iou_of_matches` | 0,8617 | 0,9391 |
| `passed` | `false` | `true` |

Lần chấm thô trước khi đối chiếu thứ tự ID có F1 = 0,5871. Bảng trên dùng mốc đã quy đổi ID để so sánh trước và sau rework. [Kết quả chấm cuối](../../outputs/annotation_evaluation.json)



## 5. Kết quả YOLO

- Runtime: Google Colab, GPU `device=0`.
- Cấu hình ghi trong `args.yaml`: `yolo26n.pt`, `epochs=50`, `imgsz=640`, `batch=-1`. [Nếu có thay đổi so với notebook, ghi lý do].
- Best checkpoint trong phiên chạy: `/content/Day2-Lab/outputs/yolo26_runs/vehicle_annotation/weights/best.pt`.

| Chỉ số trên 10 ảnh eval | Giá trị |
| --- | ---: |
| Precision | 0,4665 |
| Recall | 0,5973 |
| mAP50 | 0,4929 |
| mAP50–95 | 0,3567 |


## 6. Khó khăn và cách xử lý

| Bước | Lỗi quan sát | Cách xử lý | Kết quả |
| --- | --- | --- | --- |
| Xuất nhãn CVAT | Có các dòng box giống hệt nhau. | Gộp các dòng trùng trong cùng ảnh và kiểm tra cấu trúc YOLO. | Checker đạt 50/50 file. |
| Chấm gold | Lệnh ban đầu trỏ vào thư mục ngoài khi gold bị lồng hai cấp. | Trỏ tới thư mục chứa các file `.txt`. | Chạy được bộ chấm. |
| Đối chiếu ID | ID gold có dấu hiệu khác thứ tự trong `data.yaml`. | Quy đổi ID khi so sánh và kiểm tra lại điểm. | Kết quả sau rework đạt F1 0,8706. |

## 7. Tự đánh giá theo rubric

Theo [rubric của bài](../../RUBRIC.md), đã có 50 file nhãn qua checker, mini guideline với ba ca mơ hồ, kết quả gold QC đạt và số liệu YOLO trên 10 ảnh eval. 

## 8. Công cụ AI và tài liệu tham khảo

- Dùng YOLO v7 trong CVAT để gợi ý box. sửa lại các box không đúng nhãn và không có trong dataset của yolo.

