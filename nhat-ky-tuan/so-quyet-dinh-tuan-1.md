# Sổ quyết định – Tuần 1

**Thời gian ghi nhận:** 13/11/2026

Các quyết định trong tuần 1 được giữ nguyên mã và nội dung đã ban hành.

## Danh sách quyết định

| Mã | Nội dung | Ngày | Trạng thái |
|---|---|---|---|
| [QĐ-001](#qđ-001) | Bounding Box, Polygon và Polyline | 13/11/2026 | Hiệu lực |
| [QĐ-002](#qđ-002) | Semantic Segmentation | 13/11/2026 | Hiệu lực |

---

## QĐ-001

**Quy tắc gán nhãn Bounding Box, Polygon và Polyline**

- **Tình huống:** Gán nhãn ảnh giao thông 1280 × 720 bằng CVAT; cần thống nhất class và loại shape cho object, vùng có thể di chuyển và vạch/ranh giới làn đường. Các lỗi thường gặp là thiếu/thừa object, box quá rộng, polygon sai biên và polyline nối qua đoạn không có bằng chứng.
- **Cách xử lý:**
  - Chỉ dùng class trong taxonomy; không tự tạo, đổi tên hoặc gộp class. Object instance dùng **Rectangle/Bounding Box**; drivable area (`area/direct`, `area/alternative`) dùng **Polygon**; lane marking dùng **Polyline**.
  - Mỗi object có một box riêng, box bám sát extreme points; box được phép overlap khi object thực sự gần hoặc che nhau. Không gán bóng, reflection hoặc hình trên billboard/màn hình thành object thật.
  - Object bị che hoặc cắt biên vẫn annotate nếu còn đủ bằng chứng; nếu phần che/cắt không quá 80% thì phải annotate, trên 80% vẫn khuyến khích nếu xác định được class và vị trí. Bật `occluded` khi bị object khác che, `truncated` khi bị biên ảnh cắt; có cả hai thì bật cả hai.
  - Polygon phải khép kín, bám biên drivable area, đủ vùng nhưng không lấy thừa nền; không để các cạnh tự giao cắt. Dùng ít điểm ở đoạn thẳng, tăng điểm ở đoạn cong/biên phức tạp.
  - Polyline không khép kín, đi theo tim lane marking, không nối tắt qua đoạn mất vạch/bằng chứng; giữ hướng nhất quán nếu batch yêu cầu và dừng tại điểm không còn quan sát được.
  - Khi chưa rõ class, boundary, scope hoặc attribute, tạo Issue/comment (`UNCERTAIN_CLASS`, `UNCERTAIN_BOUNDARY`, `UNCERTAIN_SCOPE`, `ATTRIBUTE_CHECK`, `LOW_VISIBILITY`), trao đổi theo majority voting và chuyển mentor/lead; không tự đoán.
  - Trước khi nộp, kiểm tra đúng class/shape, đủ object, box sát, polygon/polyline đúng hình học, attribute đúng và kiểm tra toàn bộ dữ liệu **2 lần**. Reviewer kiểm tra taxonomy, completeness, geometry, attributes và consistency.
- **Lý do chốt:** Một shape phù hợp với từng loại đối tượng giúp giữ đúng hình học; box riêng bảo toàn từng object; quy tắc che khuất/cắt biên tránh bỏ sót; quy trình Issue và review hạn chế suy đoán, đảm bảo cùng một tình huống được gán nhãn thống nhất.
- **Phạm vi áp dụng:** Ảnh giao thông `.jpg`, kích thước 1280 × 720, thư mục `images`, công cụ CVAT; áp dụng cho annotator và reviewer đối với các nhóm object instance, drivable area và lane marking trong guideline V1.

**Trạng thái:** Hiệu lực

---

## QĐ-002

**Quy tắc gán nhãn Semantic Segmentation**

- **Tình huống:** Gán nhãn semantic segmentation ảnh giao thông bằng CVAT; mỗi pixel thuộc một class semantic, không tách identity giữa các instance cùng class. Cần tránh sai class, mask chồng lấn, pixel bỏ sót và boundary không sát.
- **Cách xử lý:**
  - Chỉ dùng đúng **19 class** trong taxonomy và color map đã quy định; không tạo, đổi tên hoặc gộp class. Màu RGB chỉ hỗ trợ hiển thị, phân loại dựa trên ngữ nghĩa và bằng chứng trong ảnh; không dùng annotation/ground truth có sẵn.
  - Mask phải bám sát boundary; hai class khác nhau không được chiếm cùng pixel. Không để sót pixel ở vùng đã xác định rõ class, nhưng không tự lấp vùng chưa rõ bằng class suy đoán.
  - Giữ đúng hình dạng/kích thước object, đặc biệt pole, biển báo, đèn tín hiệu, xe hai bánh và người; không lấy thừa background. Không gán reflection, bóng đổ hoặc hình trên billboard/màn hình thành object thật, trừ khi guideline riêng yêu cầu.
  - Phân biệt các cặp dễ nhầm: `road`/`sidewalk` theo mặt đường và lối đi bộ; `building`/`wall` theo bề mặt công trình và tường độc lập; `wall`/`fence` theo kết cấu đặc hay có khe hở; `vegetation`/`terrain` theo cây bụi/tán lá hay bề mặt địa hình; `person`/`rider` theo người đi bộ hay người điều khiển/ngồi trên xe. Tách phần đèn và cột/giá đỡ theo class tương ứng. Phân loại car/truck/bus theo phương tiện thực tế; thiếu bằng chứng thì tạo Issue.
  - Trên CVAT, kiểm tra đúng Job/Organization và label set; dùng Mask/Brush cho vùng phức tạp, Polygon cho vùng lớn có biên rõ nếu workflow cho phép; làm vùng lớn trước, sau đó vùng nhỏ; zoom và chỉnh opacity để kiểm boundary; dùng Lock/Hide/filter tránh sửa nhầm; save thường xuyên.
  - Case chưa rõ class/boundary/scope hoặc visibility phải tạo Issue/comment, trao đổi majority voting và chuyển mentor/lead; không tự đặt quy tắc.
  - Trước khi nộp, kiểm tra đúng 19 class và color map, mask không chồng lấn, không sót pixel đã rõ, boundary chính xác, không tô vùng bị che/ngoài ảnh, không trùng object, xử lý Issue còn mở và kiểm tra toàn bộ dữ liệu **2 lần**. Reviewer kiểm tra taxonomy, completeness, polygon accuracy, overlap, consistency và escalation.
- **Lý do chốt:** Gán class ở cấp pixel cần boundary chính xác và không overlap để tránh mâu thuẫn nhãn; quy tắc phân biệt class giúp giảm nhầm lẫn; chỉ dùng bằng chứng quan sát được giúp mask phản ánh đúng ảnh thay vì suy đoán.
- **Phạm vi áp dụng:** Ảnh giao thông `.jpg`, kích thước 1280 × 720, thư mục `segmentation/images`, công cụ CVAT; áp dụng cho 19 class semantic và các annotator/reviewer theo guideline V1.

**Trạng thái:** Hiệu lực
