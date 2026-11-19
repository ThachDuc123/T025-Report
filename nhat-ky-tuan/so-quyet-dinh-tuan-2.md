# Sổ quyết định – Tuần 2

**Thời gian ghi nhận:** 18/11/2026

Đây là sổ quyết định riêng của tuần 2. Mã quyết định được đánh số lại từ QĐ-001; mã trong file tuần 2 độc lập với mã ở tuần 1.

## Danh sách quyết định

| Mã | Nội dung | Ngày | Trạng thái |
|---|---|---|---|
| [QĐ-001](#qđ-001) | Facial Landmark-50 | 18/11/2026 | Hiệu lực |
| [QĐ-002](#qđ-002) | HumanPose-17 | 18/11/2026 | Hiệu lực |

---

## QĐ-001

**Quy tắc gán nhãn Facial Landmark-50**

- **Tình huống:** Gán landmark khuôn mặt người lái trong cabin xe bằng CVAT; thường gặp mặt nghiêng, mắt nhắm/nheo, miệng mở/đóng, che khuất, ảnh mờ/thiếu sáng và pre-label sai hoặc dồn điểm.
- **Cách xử lý:**
  - Gán đúng **7 skeleton/50 landmark**, giữ nguyên tên class và Point ID 0–49: `longmaytrai` (0–4), `longmayphai` (5–9), `songmui` (10–13), `mattrai` (14–21), `matphai` (22–29), `moingoai` (30–41), `moitrong` (42–49). Chỉ chọn người lái; không có mặt thì bỏ qua frame.
  - Xác định trái/phải theo khuôn mặt hiển thị, không theo mirror. Đặt điểm đúng đường biên giải phẫu; skeleton theo topology guideline, contour kín theo chiều kim đồng hồ, bắt đầu từ điểm trái nhất. `moitrong` nằm trong `moingoai`, không bắt chéo.
  - Mỗi điểm dùng property CVAT: **Visible** khi nhìn thấy; **Occluded** khi bị che nhưng còn căn cứ nội suy; **Outside** khi ngoài ảnh hoặc không còn căn cứ xác định. Không dùng Hidden thay Outside, không tạo attribute mới.
  - Khi che khuất, áp dụng ngưỡng tối thiểu: mắt 4/8; lông mày 3/5; môi ngoài 6/12; môi trong 4/8; sống mũi 2/4. Đạt ngưỡng thì hoàn thiện contour và đánh Occluded cho điểm bị che; dưới ngưỡng chỉ hoàn thiện khi còn bằng chứng, nếu không thì Outside cả skeleton tương ứng.
  - Mặt nghiêng: chỉnh từng cụm, không dồn điểm vào giữa. Mắt nhắm/nheo vẫn đủ 8 điểm; miệng mở phải tách môi trong/ngoài và đặt điểm 44, 48 trước; miệng đóng vẫn giữ đủ 8 điểm môi trong. Pre-label đúng vẫn phải kiểm tra đủ điểm và state.
  - Sai số: **±5 px** với Visible, **±20 px** với Occluded. Case không chắc chắn tạo Issue/comment (`UNCERTAIN_CLASS`, `UNCERTAIN_BOUNDARY`, `UNCERTAIN_SCOPE`, `ATTRIBUTE_CHECK`, `LOW_VISIBILITY`), trao đổi majority voting và chuyển mentor; không tự đoán.
  - Trước khi Submit, kiểm tra đủ 7 skeleton/50 điểm, class, state, topology, trái/phải và sai số; không đặt điểm lên vật thể che; kiểm tra toàn bộ dữ liệu **2 lần**. Reviewer kiểm tra taxonomy, completeness, accuracy, topology, consistency và case escalation.
- **Lý do chốt:** Chuẩn hóa vị trí và thứ tự 50 điểm giúp dữ liệu đồng nhất; state thể hiện đúng mức độ quan sát; ngưỡng che khuất và quy tắc contour hạn chế nội suy tùy ý, giữ cấu trúc khuôn mặt.
- **Phạm vi áp dụng:** Ảnh người lái trong cabin xe, CVAT, kích thước 1280 × 720, batch 150 ảnh/nhóm theo guideline Face Landmark-50 V1; áp dụng cho annotator, reviewer và mentor.

**Trạng thái:** Hiệu lực

---

## QĐ-002

**Quy tắc gán nhãn HumanPose-17**

- **Tình huống:** Gán pose người lái trong cabin xe bằng CVAT; pre-label có thể sai, keypoint chồng nhau hoặc bị che bởi nội thất/cơ thể; người lái có thể quay lưng, vặn mình, ảnh mờ hoặc không có người lái.
- **Cách xử lý:**
  - Chỉ dùng một skeleton `person` với đúng **17 keypoint**, không thêm/đổi label hoặc attribute; chỉ annotate người lái, không có người lái thì bỏ qua.
  - Quy ước trái/phải theo khung hình: **R là ID chẵn 2–16 ở bên phải ảnh; L là ID lẻ 3–17 ở bên trái ảnh**, kể cả khi người quay mặt/lưng, vặn mình hoặc ảnh xoay 90°. Không suy luận theo giải phẫu.
  - Đặt đúng mốc: Nose ở chóp mũi; Eye ở tâm đồng tử (mắt nhắm là tâm khe mí); Ear ở ống tai; Shoulder/Elbow ở tâm khớp; Wrist ở nếp gấp cổ tay; Hip ở tâm khớp háng; Knee ở giữa xương bánh chè; Ankle ngang mắt cá. Không đặt cổ tay lên vành vô-lăng hoặc hông theo mép quần.
  - Mỗi điểm dùng property CVAT: **Visible** khi thấy trực tiếp; **Occluded** khi bị che nhưng có thể suy ra từ khớp liền kề/tư thế/tỷ lệ cơ thể; **Outside** khi ngoài ảnh hoặc không còn căn cứ. Không dùng Hidden thay Outside, không tạo attribute mới.
  - Chỉnh pre-label sai; hai keypoint Visible không được trùng tọa độ. Khi bị che, chỉ nội suy và đánh Occluded nếu có căn cứ; không có căn cứ thì Outside. Khi người quay/vặn mình không đảo R/L; kiểm tra chuỗi vai–khuỷu–cổ tay liên tục.
  - Sai số: **±5 px** với Visible, **±20 px** với Occluded. Case chưa rõ tạo Issue/comment (`UNCERTAIN_CLASS`, `UNCERTAIN_BOUNDARY`, `UNCERTAIN_SCOPE`, `ATTRIBUTE_CHECK`, `LOW_VISIBILITY`), trao đổi majority voting và chuyển mentor; không tự đoán.
  - Trước khi Submit, kiểm tra đúng một skeleton, đủ 17 điểm, state rõ, R/L đúng, chuỗi tay/chân hợp lý, sai số đạt yêu cầu và Issue đã được xử lý/chuyển reviewer; kiểm tra toàn bộ dữ liệu **2 lần**. Reviewer kiểm tra taxonomy, completeness, keypoint accuracy, trái/phải, topology, consistency và escalation.
- **Lý do chốt:** Quy ước R/L theo ảnh tránh đảo nhãn khi đổi hướng; định nghĩa rõ vị trí khớp giúp đặt điểm thống nhất; state và điều kiện nội suy ngăn tạo tọa độ không có căn cứ, đồng thời giữ topology skeleton.
- **Phạm vi áp dụng:** Ảnh người lái trong cabin xe, CVAT, kích thước 960 × 540, batch 150 ảnh/nhóm theo guideline HumanPose-17 V1; áp dụng cho annotator, reviewer và mentor.

**Trạng thái:** Hiệu lực
