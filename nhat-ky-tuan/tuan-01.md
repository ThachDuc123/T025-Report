# Nhật ký tuần 01 · 09/11 – 15/11/2026

**Lead tuần này:** Thạch Trung Đức (Lead BBox) · Phí Minh Quân (Lead Segmentation)
**Dữ liệu / task CVAT:** Ảnh giao thông đô thị —
BBox: [Task 64](https://cvat.edufun.ai/tasks/64) ·
Segmentation: [Task 204](https://cvat.edufun.ai/tasks/204)

> Cập nhật hoàn thiện cả tuần theo mốc Chủ Nhật 15/11.

## 1. Thành viên và phân công BBox

| Thành viên | Vị trí | Phân công tuần này |
|---|---|---|
| Thạch Trung Đức | **Lead BBox** · Annotator | Job 167; chia job, xây dựng quy chuẩn Bounding Box, xử lý edge case, review các job BBox của nhóm |
| Phí Minh Quân | Annotator | Job 168 — gán nhãn BBox |
| Đinh Tuấn Thành | Annotator | Job 169 — gán nhãn BBox |
| Đinh Quang Thắng | Annotator | Job 170 — gán nhãn BBox |
| Lê Văn Trung Tính | Annotator | Job 171 — gán nhãn BBox |

## 2. Thành viên và phân công Segmentation

| Thành viên | Vị trí | Phân công tuần này |
|---|---|---|
| Phí Minh Quân | **Lead Segmentation** · Annotator | Job 870; chia job, thống nhất quy chuẩn mask, xử lý edge case, review các job Segmentation của nhóm |
| Thạch Trung Đức | Annotator | Job 869 — phân vùng đối tượng, kiểm tra đường biên và chất lượng mask |
| Đinh Tuấn Thành | Annotator | Job 871 — phân vùng đối tượng, đảm bảo mask đúng, không thiếu |
| Đinh Quang Thắng | Annotator | Job 872 — phân vùng đối tượng, kiểm tra vùng phân đoạn |
| Lê Văn Trung Tính | Annotator | Job 873 — phân vùng đối tượng, kiểm tra đường biên và tính liên tục của mask |

## 3. Công việc

Mức hoàn thành: ✅ xong **và đã qua review** · 🟡 đang làm (ghi %) · ⛔ bị chặn (ghi lý do) · ⬜ chưa bắt đầu

### BBox

| # | Nội dung công việc | Annotator | Reviewer | Hoàn thành | Ghi chú |
|---|---|---|---|---|---|
| 1 | Thiết lập quy chuẩn BBox và phân chia job | Thạch Trung Đức | — | ✅ 100% | Cách vẽ box, xử lý edge case |
| 2 | Job 167 — BBox/Polygon/Polyline, 20 ảnh | Thạch Trung Đức | Đinh Quang Thắng | ✅ 100% | Đã sửa các lỗi đánh box và chỉnh sửa đối tượng |
| 3 | Job 168 — BBox/Polygon/Polyline, 20 ảnh | Phí Minh Quân | Đinh Quang Thắng | ✅ 100% | Chờ phân bổ mã job chính thức |
| 4 | Job 170 — BBox/Polygon/Polyline, 20 ảnh | Đinh Quang Thắng | Đinh Tuấn Thành | ✅ 100% | Chú ý đối tượng bị che khuất |
| 5 | Job 169 — BBox/Polygon/Polyline, 20 ảnh | Đinh Tuấn Thành | Lê Văn Trung Tính | ✅ 100% | Đã sửa các lỗi đánh box và chỉnh sửa đối tượng |
| 6 | Job 171 — BBox/Polygon/Polyline, 20 ảnh | Lê Văn Trung Tính | Phí Minh Quân | ✅ 100% | Đã sửa các lỗi đánh box và chỉnh sửa đối tượng |
### Segmentation

| # | Nội dung công việc | Annotator | Reviewer | Hoàn thành | Ghi chú |
|---|---|---|---|---|---|
| 1 | Thiết lập quy chuẩn Segmentation và phân chia job | Phí Minh Quân | — | ✅ 100% | Quy chuẩn mask, vùng biên |
| 2 | Job 869 — Segmentation, 20 ảnh | Thạch Trung Đức | Đinh Tuấn Thành | ✅ 100% | |
| 3 | Job 870 — Segmentation, 20 ảnh | Phí Minh Quân | Đinh Tuấn Thành | ✅ 100% | 20 ảnh, theo status của Đức |
| 4 | Job 871 — Segmentation, 20 ảnh | Đinh Tuấn Thành | Lê Văn Trung Tính | ✅ 100% | Tránh mask chồng lấn / thiếu vùng |
| 5 | Job 872 — Segmentation, 20 ảnh | Đinh Quang Thắng | Thạch Trung Đức | ✅ 100% | Chú ý đường biên mask |
| 6 | Job 873 — Segmentation, 20 ảnh | Lê Văn Trung Tính | Đinh Quang Thắng | ✅ 100% | Chú ý tính liên tục của mask |

## Tổng kết

- Nhóm BBox + Polygon + Polyline: 1 Lead và 4 Annotator. Các nhãn Bounding Box gồm pedestrian, rider, car, truck, bus, train, motorcycle, bicycle, traffic light, traffic sign; Polygon gồm area/direct, area/alternative; Polyline gồm các nhãn Lane Marking theo guideline.
- Nhóm Semantic Segmentation: 1 Lead và 4 Annotator, sử dụng 19 class theo Semantic Segmentation Guideline.- Nhóm Segmentation: 1 Lead + 4 Annotator.
- Đã gán: Hoàn thành 
- Qua review lần đầu: Bbox còn đánh khá lỗi .
- Edge case mới: 

## Vướng mắc
- Không có - cố gắng khắc phục về sau nhất là Segmentation làm thống nhất hơn và Bbox cần gán nhãn chuẩn hơn

## Kế hoạch tuần 02
- Team đã hiểu cách chia việc - tuần 2 sẽ chia việc cụ thể hơn cố gắng hoàn thành job sớm.




