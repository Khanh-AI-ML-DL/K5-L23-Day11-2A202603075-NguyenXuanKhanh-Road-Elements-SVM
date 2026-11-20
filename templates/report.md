# Báo cáo cá nhân — Ngày 11
Họ tên: Nguyễn Xuân Khánh               Mã học viên: 2A202603075  
Phiên bản CVAT (Help → About): v2.xx  <!-- TỰ ĐIỀN: mở CVAT → Help → About -->  
Guideline: Road v1.0    Lần nộp (`revision` trong manifest): 1  
Thời điểm export (ngày giờ trên CVAT): 2026-11-20 — job front cập nhật 18:49 UTC, job fisheye 18:43 UTC (manifest tạo 18:52 UTC)    

## 1. Kiểm project
 Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | Đúng | lane/road_curb = polyline; crosswalk/drivable = polygon; traffic_light/traffic_sign = rectangle (khớp `<meta>` trong XML) |
| Thuộc tính và giá trị | Đúng | lane: position L1/R1/L2/R2/other, style, color, kind; drivable: area_type; đèn/biển: color/type/group/facing/edge_zone |
| 4 tag ảnh | Đúng | camera, timeofday, weather, source; mỗi tag có thuộc tính `value`. 20/20 ảnh đủ 4 tag |
 
Cách kết thúc polyline trên bản CVAT này: bấm phím **N**  
Cách đặt tag ảnh trên bản CVAT này: công cụ **Tag** ở thanh bên trái, đặt camera trước, rồi mở Details kiểm giá trị (CVAT tự điền giá trị đầu danh sách)
## 2. Số lượng đã gán
 Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 33 | 11 | 4 | 22 | 23 | 20 |
| front-extra (đã làm 0 / 4) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| fisheye | 8 | 6 | 3 | 7 | 5 | 3 | 1 |
| fisheye-extra (đã làm 0 / 4) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
 
Tổng: 20 ảnh, 138 hình + 80 tag. Lint lúc tạo manifest: nặng 4, chính 6, nhẹ 1.

## 3. Bảng ca khó
| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do                                                                                                                                        |
| --- | --- | --- | --- |----------------------------------------------------------------------------------------------------------------------------------------------|
| A05 | lane L1, R1 | Vẽ vạch / không vẽ | Không vẽ | Ảnh không thấy vạch sơn; coach đã xác nhận, nên được miễn QC1-02 theo guideline mục 2 đặc tả bàn giao                                        |
| A06 | lane R1 | Vẽ / không vẽ | Không vẽ | Bên phải không thấy vạch; coach đã xác nhận, được miễn QC1-02                                                                                |
| A09 | lane R1 | Vẽ / không vẽ | Không vẽ | Không thấy vạch bên phải; coach đã xác nhận, được miễn QC1-02                                                                                |
| A09 | lane L2 (kind=double) | Một polyline / hai polyline | Hai polyline | Vạch đôi gồm hai nét song song, mỗi nét một đường; lint nhắc "vạch đứt có bị tách không" nhưng đây là vạch liền, không phải vạch đứt bị tách |
| A11 | lane L1 (yellow, double) | Một polyline / hai polyline | Hai polyline | Như A09: vạch vàng đôi hai nét song song , theo như thầy chỉ dẫn trên lớp                                                                    |
| B03, B04, B08 | lane (3 điểm) | Thêm điểm / giữ nguyên | Giữ nguyên | Đoạn vạch ngắn, gần thẳng trên ảnh; coach đã xem và xác nhận, nên không sửa                                                                  |
| B04 | traffic_sign #2 | edge_zone bật / tắt | Tắt (false) | Lint chỉ gợi ý; tâm hộp gần ngưỡng 80 % bán kính, đã tự đo lại bằng mắt                                                                      |
| A10 | traffic_sign #2 | Bỏ / giữ | Giữ | Hộp thấp hơn 8 px nên không bắt buộc, nhưng giữ vì biển phụ rõ                                                                               |
| A08 | drivable | direct × 2 | Giữ | Hai vùng direct cho hai đoạn đường; cần coach xác nhận <!-- TỰ KIỂM: có đúng không? -->                                                      |
 
<!-- Các dòng "Lý do" ở trên được soạn từ dữ liệu file và log lint. Bạn hãy đọc lại và sửa cho đúng với những gì bạn thực sự thấy trên ảnh. -->
 
## 4. Phiếu QC 1 nhận được
Bạn kiểm lô của tôi: <!-- tên bạn kia -->  Quyết định nhận được: <!-- điền khi nhận phiếu -->  
| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
| --- | ---: | --- | --- |
| (chưa nhận phiếu) | | | |
 
## 5. Kiểm file export
| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | --- | --- | --- | --- |
| NguyenXuanKhanh-front.zip | Có (`road_check lint` đọc được 12 ảnh) | A01: 9 / 9 | A02: 6 / 6 | Có, `camera=front` ở cả 12 ảnh |
| NguyenXuanKhanh-fisheye.zip | Có (đọc được 8 ảnh) | B01: 3 / 3 | B02: 3 / 3 | Có, camera fisheye_front / rear / left / right đúng theo FV / RV / MVL / MVR |
 
`contains_images` = false ở cả hai file (xem manifest).
 
## 6. Ảnh chụp màn hình
<!-- TỰ CHÈN 4 ảnh: (1) tab Labels của project; (2) một ảnh front đã gán đủ; (3) một ảnh fisheye, phóng to đoạn polyline cong; (4) đoạn XML có <polyline label="lane"> -->
 
## 7. Tự đánh giá
Lỗi bạn mắc nhiều nhất hôm nay (theo mã QC1-xx), và cách tránh ở Ngày 20: QC1-11 (fisheye lane chỉ 3 điểm) và QC1-05 (vạch đôi tách thành hai polyline). Lần sau đặt điểm dày theo cung ở vòng ngoài ngay khi vẽ, và quyết định trước một vạch đôi là một hay hai polyline rồi ghi vào bảng ca khó.  
Nhãn của bạn đi vào model ở đâu? Chọn một lỗi đã sửa và nói nó làm model học sai thế nào: Nhãn lane đi vào model phát hiện làn. Nếu polyline fisheye chỉ nối thẳng hai đầu thay vì theo cung, model học vạch thẳng ở vùng rìa, nên ước lượng vị trí làn sai chính ở vòng ngoài ảnh, nơi hình méo nhiều nhất.
 
## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor
| y | 720 | 680 | 640 | 600 | 560 |
| --- | ---: | ---: | ---: | ---: | ---: |
| x của chúng tôi |  |  |  |  |  |
| x của bạn kia |  |  |  |  |  |

Trả lời 3 câu:

1. Năm số x đó chính là đích mà một model row-anchor học cho vạch này. Nếu bạn dừng polyline sớm 40 px, hàng nào đổi thành "không có làn"?
2. So với bạn được kiểm (cùng ảnh): ở hàng 720 và hàng 560, hai bạn lệch nhau bao nhiêu pixel? Lệch ở hàng nào ảnh hưởng LKA nhiều hơn (slide 25)?
3. Nếu polyline vẽ từ xa về gần (ngược quy tắc 2), cách tính trên có đổi không? Script nào sẽ gặp khó?
