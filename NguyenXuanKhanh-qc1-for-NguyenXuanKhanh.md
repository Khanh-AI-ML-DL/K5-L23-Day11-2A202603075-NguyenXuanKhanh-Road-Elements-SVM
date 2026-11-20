# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): NguyenXuanKhanh        Người kiểm (học viên): NguyenXuanKhanh  
Ngày: 21/11/2026                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): NguyenXuanKhanh-front.zip, NguyenXuanKhanh-fisheye.zip, revision 1  
Số ảnh kiểm: 6 (+ 0 ảnh thêm, ghi riêng): A01, A06, A09, A11, B04, B08   Số nhãn đã kiểm (shape + tag): 44 + 24 = 68

> Ghi chú phạm vi: phiếu kiểm trên lô của chính người nộp, bằng dữ liệu XML và `road_check lint`. Các mã cần nhìn ảnh (QC1-04, 06, 07, 08, 09, 10) mới kiểm phần thuộc tính trong XML, chưa đối chiếu pixel trên CVAT, nên cột "Số lỗi" của các mã này là "0*".

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | --- | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 8 | 0 (2 chưa có; coach xác nhận không thấy vạch: miễn) | nặng |
| QC1-03 position | sai thuộc tính / thừa | 13 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 13 | 0* | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 13 | 0 (A09, A11: coach bảo vạch đôi vẽ 2 đường cùng position) | chính |
| QC1-06 style, color, kind | sai thuộc tính | 13 | 0* | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 10 | 0* | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 8 | 0* | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 14 | 0* | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 14 | 0* | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 3 | 2 (1 ca chờ: edge_zone B04) | chính |
| QC1-12 file | lỗi file | 2 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-11 | B04 | lane#0 @(248,647) | chính | Lint báo lane chỉ 3 điểm trên ảnh fisheye (cần đặt điểm theo cung); coach đã xem, vẫn ghi nhận |
| 2 | QC1-11 | B08 | lane#0 @(60,745) | chính | Như trên: lane 3 điểm trên ảnh fisheye; coach đã xem, vẫn ghi nhận |

Không tính vào lỗi: A05, A06, A09 thiếu L1/R1 (QC1-02): coach đã xác nhận không thấy vạch, được miễn theo đặc tả bàn giao mục 2.

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A09 | Hai polyline cùng position L2 (vạch đôi): có là lỗi QC1-05 không? | Coach: vạch đôi vẽ 2 đường và để cùng position. Không phải lỗi |
| A11 | Hai polyline cùng position L1 (vàng, double): có là lỗi QC1-05 không? | Như A09. Không phải lỗi |
| A05, A06, A09 | Không vẽ L1/R1 vì không thấy vạch: có được miễn QC1-02 không? | Coach đã xác nhận: được miễn |
| B04 | traffic_sign#2 @(1063,170): tâm hộp ngoài 80 % bán kính, có cần bật `edge_zone` không? (QC1-11) | Chưa có. Người nộp báo đã bật trên CVAT nhưng file export hiện tại vẫn `edge_zone=false` |

## Quyết định
Lỗi nặng: 0   Lỗi chính: 2 / 68 nhãn = 2,9 %   Lỗi nhẹ: 0   Ca chờ lead: 1  
Quyết định (Release / Hold / Rework): **Release**  
Lý do (theo luật của phiếu): Không có lỗi nặng. Lỗi chính 2/68 = 2,9 %, chưa vượt 5 %. Ca chờ duy nhất (B04 edge_zone) nếu bị tính là lỗi chính thì thành 3/68 = 4,4 %, vẫn dưới 5 %, nên không làm đổi kết luận và không cần Hold.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).