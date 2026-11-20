# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): NguyenXuanKhanh        Người kiểm (học viên): NguyenXuanKhanh  
Ngày: 21/11/2026                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): NguyenXuanKhanh-front.zip, NguyenXuanKhanh-fisheye.zip, revision 1  
Số ảnh kiểm: 6 (+ 0 ảnh thêm, ghi riêng): A01, A06, A09, A11, B04, B08   Số nhãn đã kiểm (shape + tag): 44 + 24 = 68

> Ghi chú phạm vi: đây là phiếu kiểm trên lô của chính người nộp, bằng dữ liệu XML và `road_check lint`. Các mã cần nhìn ảnh (QC1-04, 06, 07, 08, 09, 10) mới kiểm phần thuộc tính trong XML, chưa đối chiếu pixel trên CVAT, nên cột "Số lỗi" của các mã này là "0*".

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm |                                              Số lỗi | Mức |
| --- | --- | ---: |----------------------------------------------------:| --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 |                                                   0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 8 | 0 (2 chưa có, Thầy  xác nhận không thấy vạch: miễn) | nặng |
| QC1-03 position | sai thuộc tính / thừa | 13 |                                                   0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 13 |                                                  0* | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 13 |                                      0 (2 ca mơ hồ) | chính |
| QC1-06 style, color, kind | sai thuộc tính | 13 |                                                  0* | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 10 |                                                  0* | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 8 |                                                  0* | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 14 |                                                  0* | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 14 |                                                  0* | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 3 |                                      2 (1 ca mơ hồ) | chính |
| QC1-12 file | lỗi file | 2 |                                                   0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- |  |
| 1 | QC1-11 | B04 | lane#0 @(248,647) | chính |Để 2 điểm vẫn báo lỗi , để 3 điểm vẫn báo lỗi , chưa hiểu gán sai như thê nào |
| 2 | QC1-11 | B08 | lane#0 @(60,745) | chính | Để 2 điểm vẫn báo lỗi , để 3 điểm vẫn báo lỗi , chưa hiểu gán sai như thê nào|

Không tính vào lỗi: A06 thiếu R1 và A09 thiếu R1 (QC1-02), coach đã xác nhận không thấy vạch, được miễn theo đặc tả bàn giao mục 2.

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có)                                         |
| -- | --- |----------------------------------------------------------|
| A09 | Hai polyline cùng position L2, đều kind=double: vạch đôi vẽ thành hai nét có được tính là một vạch đứt bị tách (QC1-05) không? | Thầy bảo "Với vạch đôi , vẽ 2 đường và để cùng positaion |
|A11 | Hai polyline cùng position L1 (vàng, double): như A09, tính là lỗi QC1-05 không? | Như Hình A09                                             ||
|A05 , A    06 , A09 | lane L1/R1 không vẽ vì ảnh không thấy vạch sơn: được miễn QC1-02 theo guideline mục 2 đặc tả bàn giao không? | Coach đã xác nhận, nên được miễn QC1-02 theo guideline mục 2 đặc tả bàn giao |
| B04 | traffic_sign#2 @(1063,170): tâm hộp ngoài 80 % bán kính, `edge_zone` đang tắt; có cần bật không? (QC1-11) | B04 em có lưu rồi , nhưng QC vẫn  ko tính                |

## Quyết định
Lỗi nặng: 0   Lỗi chính: 2 / 68 nhãn = 2,9 %   Lỗi nhẹ: 0   Ca chờ lead: 3  
Quyết định (Release / Hold / Rework): **Hold**  
Lý do (theo luật của phiếu): Không có lỗi nặng và 2,9 % lỗi chính chưa vượt 5 %. Tuy nhiên có 3 ca mơ hồ chưa có lời đáp
Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).