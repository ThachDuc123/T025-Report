# Nhật ký tuần 01 · 09/11 – 15/11/2026

**Lead tuần này:** Thạch Trung Đức (Lead BBox) · Phí Minh Quân (Lead Segmentation)
**Dữ liệu / task CVAT:** Ảnh giao thông đô thị —
BBox: [Task 64](https://cvat.edufun.ai/tasks/64) ·
Segmentation: Task 204

> Cập nhật hoàn thiện cả tuần theo mốc Chủ Nhật 15/11. Số liệu chưa có nguồn được ghi rõ
> "chưa có số liệu" thay vì bịa thêm.

## 1. Thành viên và phân công BBox

| Thành viên | Vị trí | Phân công tuần này |
|---|---|---|
| Thạch Trung Đức | **Lead BBox** · Annotator | Job 167; chia job, xây dựng quy chuẩn Bounding Box, xử lý edge case, review các job BBox của nhóm |
| Phí Minh Quân | Annotator | Job 1xx (mã chờ xác nhận) — gán nhãn BBox, kiểm tra vị trí và kích thước box |
| Đinh Quang Thắng | Annotator | Job 170 — gán nhãn BBox, kiểm tra các đối tượng xe và người |
| Đinh Tuấn Thành | Annotator | Job 169 — gán nhãn BBox, đảm bảo nhãn chính xác, không bỏ sót đối tượng |
| Lê Văn Trung Tính | Annotator | Job 171 — gán nhãn BBox, kiểm tra tính nhất quán giữa các ảnh |

## 2. Thành viên và phân công Segmentation

| Thành viên | Vị trí | Phân công tuần này |
|---|---|---|
| Phí Minh Quân | **Lead Segmentation** · Annotator | Job 869; chia job, thống nhất quy chuẩn mask, xử lý edge case, review các job Segmentation của nhóm |
| Thạch Trung Đức | Annotator | Job 8xx (mã chờ xác nhận) — phân vùng đối tượng, kiểm tra đường biên và chất lượng mask |
| Đinh Quang Thắng | Annotator | Job 872 — phân vùng đối tượng, kiểm tra vùng phân đoạn |
| Đinh Tuấn Thành | Annotator | Job 871 — phân vùng đối tượng, đảm bảo mask đúng, không thiếu |
| Lê Văn Trung Tính | Annotator | Job 873 — phân vùng đối tượng, kiểm tra đường biên và tính liên tục của mask |

Nguyên tắc: người không review job do chính mình gán — job 167 (Đức gán) và job 869 (Quân gán)
do thành viên khác trong nhóm review chéo, người review cụ thể cần được Lead ghi nhận.

## 3. Công việc

Mức hoàn thành: ✅ xong **và đã qua review** · 🟡 đang làm (ghi %) · ⛔ bị chặn (ghi lý do) · ⬜ chưa bắt đầu

### BBox

| # | Nội dung công việc | Annotator | Reviewer | Hoàn thành | Ghi chú |
|---|---|---|---|---|---|
| 1 | Thiết lập quy chuẩn BBox và phân chia job | Thạch Trung Đức | — | ⬜ 0% | Cách vẽ box, xử lý edge case |
| 2 | Job 167 — BBox/Polygon/Polyline, 20 ảnh | Thạch Trung Đức | Review chéo trong nhóm | 🟡 Gán xong 100%, chờ review cuối | Xem [thachtrungduc_tuan1.md](thachtrungduc_tuan1.md) |
| 3 | Job 170 — BBox | Đinh Quang Thắng | Thạch Trung Đức | ⬜ 0% | Chú ý đối tượng bị che khuất |
| 4 | Job 169 — BBox | Đinh Tuấn Thành | Thạch Trung Đức | ⬜ 0% | Chú ý box không lệch |
| 5 | Job 171 — BBox | Lê Văn Trung Tính | Thạch Trung Đức | ⬜ 0% | Chú ý nhất quán nhãn giữa các ảnh |
| 6 | Job 1xx — BBox (mã chờ xác nhận) | Phí Minh Quân | Thạch Trung Đức | ⬜ 0% | Chờ phân bổ mã job chính thức |
| 7 | Tổng hợp và kiểm tra chất lượng dữ liệu BBox | Thạch Trung Đức | Nhóm BBox | ⬜ 0% | Kiểm tra dữ liệu sau export từ CVAT |

### Segmentation

| # | Nội dung công việc | Annotator | Reviewer | Hoàn thành | Ghi chú |
|---|---|---|---|---|---|
| 1 | Thiết lập quy chuẩn Segmentation và phân chia job | Phí Minh Quân | — | ⬜ 0% | Quy chuẩn mask, vùng biên |
| 2 | Job 869 — Segmentation, 20 ảnh | Phí Minh Quân | Review chéo trong nhóm | 🟡 Đang làm | |
| 3 | Job 872 — Segmentation | Đinh Quang Thắng | Phí Minh Quân | ⬜ 0% | Chú ý đường biên mask |
| 4 | Job 871 — Segmentation | Đinh Tuấn Thành | Phí Minh Quân | ⬜ 0% | Tránh mask chồng lấn / thiếu vùng |
| 5 | Job 873 — Segmentation | Lê Văn Trung Tính | Phí Minh Quân | ⬜ 0% | Chú ý tính liên tục của mask |
| 6 | Job 8xx — Segmentation (mã chờ xác nhận) | Thạch Trung Đức | Phí Minh Quân | 🟡 Đang làm | 20 ảnh, theo status của Đức |
| 7 | Tổng hợp và kiểm tra chất lượng dữ liệu Segmentation | Phí Minh Quân | Nhóm Segmentation | ⬜ 0% | Kiểm tra mask, vùng thiếu, đường biên |

## Tổng kết

- Nhóm BBox: 1 Lead + 4 Annotator — nhãn `xe_may`, `o_to`, `nguoi`.
- Nhóm Segmentation: 1 Lead + 4 Annotator.
- Đã gán: Job 167 — 20/20 ảnh gán xong (chưa qua review cuối); các job khác chưa có số liệu.
- Qua review lần đầu: chưa tổng hợp được.
- Edge case mới: [P-004](../problem-backlog.md#p-004) — cách gán nhãn xe ở xa.

## Vướng mắc

- [P-004](../problem-backlog.md#p-004): chưa rõ tiêu chí gán nhãn xe ở xa — đã hỏi Coach, chờ trả lời.
- Đối tượng bị che khuất: quy tắc vẽ box chưa thống nhất — Lead BBox phụ trách.
- Đường biên mask khó xác định với đối tượng bị che — Lead Segmentation phụ trách.
- Nhãn giữa các thành viên có nguy cơ không đồng nhất — cần kiểm tra chéo và thống nhất guideline.
- Mã job của hai Lead (BBox 1xx, Segmentation 8xx) chưa được xác nhận — chờ phân bổ chính thức.
- Dữ liệu sau khi export từ CVAT cần kiểm tra lại trước khi chốt.

## Kế hoạch tuần 02

- Xác nhận mã job 1xx / 8xx và hoàn thiện phân bổ cho từng thành viên ở cả hai nhóm.
- Hoàn thành annotation BBox và Semantic Segmentation theo job được giao.
- Hai Lead review dữ liệu nhóm mình; thành viên sửa annotation chưa đạt sau phản hồi.
- Chốt cách xử lý edge case (xe ở xa, đối tượng bị che, đường biên mask) và cập nhật [problem-backlog](../problem-backlog.md).
- Kiểm tra dữ liệu sau export; tổng hợp số ảnh hoàn thành, tỷ lệ lỗi và kết quả review cho báo cáo tuần 02.

## Status từng thành viên

**Thạch Trung Đức (Lead BBox)**

- **Done — Đã hoàn thành:** Gán nhãn BBox/Polygon/Polyline Job 167 — 20 ảnh.
- **Doing — Đang làm:** Job 8xx Segmentation (20 ảnh); chờ các thành viên xong BBox để chia việc review.
- **Blocked — Vướng mắc:** Tiêu chí gán nhãn xe ở xa — xem [P-004](../problem-backlog.md#p-004).
- **Link — Link code/demo:** Chưa có.
- **Questions — Câu hỏi cho Coach:** Với xe ở xa, tiêu chí nào để quyết định có gán nhãn và cách vẽ bounding box?

**Phí Minh Quân (Lead Segmentation)**

- *Chưa nhận được báo cáo từ thành viên — cần bổ sung trước khi chốt tuần.*

**Đinh Quang Thắng · Đinh Tuấn Thành · Lê Văn Trung Tính**

- *Chưa nhận được báo cáo từ thành viên — cần bổ sung trước khi chốt tuần.*
