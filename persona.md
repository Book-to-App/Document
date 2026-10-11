# Vị Thuận Thiên (Heritage & Elemental Nutrition — Book to App)

| Mục | Nội dung |
|---|---|
| Dự án | Vị Thuận Thiên (Heritage & Elemental Nutrition — Book to App) |
| Môn học | PRM393 (Lab 02: AI-Assisted UI/UX Design & Lab 03: Design to Working App) |
| Nhóm thực hiện | Mai Lê Nguyên, Nguyễn Duy Trường, Đặng Thuận Phát, Nguyễn Quốc Huy |
| Phiên bản | 1.1.0 (Hoàn thiện kết quả phỏng vấn, thử nghiệm prototype và trích dẫn sách) |
| Ngày phê duyệt nội bộ | 03/10/2026 |
| Tài liệu | `ux/persona.md`: Persona, Problem Statement và Tiêu chí thành công |
| Phụ trách | Nguyễn Quốc Huy · Phỏng vấn hỗ trợ: Nguyễn Duy Trường |

---

## 1. Persona chính: Trần Minh Anh

| Mục | Nội dung |
|---|---|
| Họ tên, tuổi | Trần Minh Anh, 25 tuổi |
| Nghề nghiệp | Nhân viên văn phòng mới đi làm (Junior Data Analyst) |
| Nơi ở | Thuê trọ ở Cầu Giấy, Hà Nội; sống một mình; gian bếp nhỏ (bếp từ đơn, tủ lạnh mini 90L) |
| Thói quen ăn uống | Thường ăn ngoài hoặc nấu nhanh sau giờ làm, ít khi lên kế hoạch bữa ăn trước |
| Thiết bị | Android tầm trung (Xiaomi Redmi Note 12), thường thao tác một tay lúc đi xe bus/đi bộ về phòng |

### Bối cảnh hằng ngày (tình huống điển hình)

Minh Anh tan làm lúc 18:30, trời Hà Nội vào tiết Hàn Lộ chuyển mưa phùn lạnh (18°C) và cổ họng bắt đầu đau rát, mệt mỏi hụt hơi sau cả ngày làm việc trong phòng điều hòa. Tủ lạnh chỉ còn ít nguyên liệu lẻ mua từ đầu tuần (thịt gà, một củ gừng nhỏ, vài nhánh hành lá). Cô đã kiệt sức, không muốn vắt óc nghĩ món và chưa biết nấu gì cho ấm bụng, giải cảm mà không phải tốn tiền gọi đồ ăn nhanh nhiều dầu mỡ.

### Mục tiêu

- Ăn đúng với thời tiết và tình trạng cơ thể (giải hàn, êm cổ họng).
- Tận dụng hết các nguyên liệu sẵn có trong tủ lạnh, tránh bỏ phí đồ ăn cũ.
- Nấu được món hoàn chỉnh trong vòng 30 phút với dụng cụ bếp đơn giản.

### Nỗi đau (pain points)

- Thông tin Đông y trên mạng xã hội và diễn đàn quá nhiễu loạn, bài thuốc phức tạp khó phân biệt đúng sai.
- Thường xuyên bỏ phí rau củ, thịt thừa vì không biết kết hợp các nguyên liệu lẻ.
- Tan làm về mệt mỏi nên lười đọc nhiều bước hoặc đưa ra quyết định phức tạp.
- Các app dinh dưỡng hiện hành bắt nhập số liệu cân đo, tính calo/macro rất mất thời gian và máy móc.

### Nhu cầu tiếp cận (accessibility)

- Thường dùng ngoài trời lúc chập tối hoặc trong phòng trọ thiếu sáng, cần độ tương phản thị giác cao (WCAG 2.1 AA >= 4.5:1).
- Thao tác một tay khi đang di chuyển hoặc cầm đồ, các nút bấm hành động chính bắt buộc nằm ở nửa dưới màn hình.
- Màn hình nhỏ cần cỡ chữ rõ ràng (tối thiểu 14sp cho nội dung), hỗ trợ tùy chọn chữ lớn.

### Ảnh hưởng của persona lên thiết kế

| Đặc điểm persona | Quyết định thiết kế liên quan |
|---|---|
| Thao tác một tay | Một nút chính (Primary FilledButton) mỗi màn hình, đặt ở nửa dưới; vùng chạm tối thiểu 48 x 48 dp |
| Dùng ngoài trời, thiếu sáng | Tương phản chữ >= 4.5:1 (Mực trên Kem đạt 13.5:1), chữ nội dung >= 14 sp, không chỉ dùng màu đơn độc để báo trạng thái |
| Mệt, lười quyết định | Gợi ý tối đa 1 đến 2 món thay vì danh sách dài; chạm trực quan vào Body Map 2D thay vì nhập form số liệu |
| Không tin thông tin trên mạng | Mỗi món có lý do y lý trích dẫn rõ tên sách, chương/trang; luôn có khuyến cáo an toàn "không thay thế bác sĩ" |
| Nguyên liệu lẻ trong tủ lạnh | Bước quét tủ lạnh có kiểm duyệt (Human-in-the-loop), người dùng được quyền thêm/sửa/xóa chip trước khi tìm món |

---

## 2. Problem statement (1 câu)

> Người trẻ sống một mình ở đô thị khó biết nên ăn gì khi thời tiết đổi mùa và cơ thể không khoẻ, dẫn đến ăn uống tuỳ tiện và bỏ phí nguyên liệu trong tủ lạnh.

---

## 3. Tiêu chí thành công (đo được)

> Từ lúc mở app (đã đăng nhập) đến lúc thấy gợi ý món phù hợp: **không quá 6 lần chạm và không quá 45 giây**.

### Cách đo

- **Người tham gia:** 5 bạn sinh viên cùng lớp PRM393, chưa từng tiếp xúc hay dùng thử bản thiết kế app trước đây.
- **Công cụ:** Prototype bấm được trên Figma (trang 06), chạy trực tiếp trên điện thoại Android (màn hình 360 x 800 dp).
- **Nhiệm vụ giao:** *"Bạn vừa tan làm lúc 18:30, trời mưa lạnh, bạn hơi đau rát họng, trong tủ lạnh còn thịt gà, gừng, hành lá. Hãy dùng app để tìm món ăn phù hợp và lưu vào sổ tay."*
- **Điểm bắt đầu:** Màn hình Trang chủ S02 (đã đăng nhập sẵn).
- **Điểm kết thúc:** Màn hình S06 hiện gợi ý món ăn và bấm *"Lưu vào Sổ tay"*.
- **Ghi nhận:** Đếm số lần chạm vào điều khiển, bấm giờ thời gian thực hiện, ghi lại chỗ do dự hoặc thao tác nhầm.
- **Tiêu chí đạt:** Ít nhất 4 trên 5 người đạt cả hai ngưỡng (**<= 6 lần chạm** và **<= 45 giây**).

### Kết quả thử nghiệm (thực hiện ngày 02/10/2026)

| Người thử | Số lần chạm | Thời gian (giây) | Đạt? | Ghi chú (chỗ vướng) |
|---|---|---|---|---|
| 1 (Lê Hoàng Nam) | 5 | 28s | Đạt | Thao tác rất nhanh, chạm đúng vùng cổ họng và bấm tiếp tục ngay. |
| 2 (Phạm Thu Thảo) | 6 | 36s | Đạt | Dừng lại đọc thẻ lý do y lý ở S06 khoảng 10 giây trước khi bấm Lưu. |
| 3 (Trần Quốc Bảo) | 5 | 31s | Đạt | Bỏ qua bước chụp tủ lạnh ở S04 vì dùng luôn chip nguyên liệu có sẵn. |
| 4 (Đỗ Minh Khang) | 7 | 48s | Chưa đạt | Nhầm lẫn giữa nút "Chẩn vị hôm nay" và thẻ mẹo dưỡng sinh ở S02 (bị chạm thừa 1 lần); mất thời gian tìm hiểu. |
| 5 (Vũ Thùy Linh) | 5 | 34s | Đạt | Thao tác mượt mà, phản hồi tốt về chuyển cảnh loading nồi đất bốc khói. |

**Kết luận:** 
- **Tỷ lệ đạt:** **4/5 người (80%)** thỏa mãn trọn vẹn cả 2 tiêu chí (<= 6 lần chạm và <= 45 giây). Thời gian hoàn thành trung bình là **35.4 giây** và số lần chạm trung bình là **5.6 lần**.
- **Điều chỉnh thiết kế sau thử nghiệm:** Ở màn hình Trang chủ S02, khối *"Chẩn vị hôm nay"* đã được tinh chỉnh loại bỏ hoàn toàn các chip triệu chứng chọn nhanh nằm cạnh nút bấm để tránh làm phân tán sự chú ý, bảo đảm chỉ có một hành động chính duy nhất giúp người dùng mới không bị chạm nhầm như trường hợp của Người thử số 4.

---

## 4. Phỏng vấn nhanh (cơ sở thực nghiệm của persona)

- **Số người phỏng vấn:** 4 bạn sinh viên/nhân viên văn phòng mới đi làm, mỗi người phỏng vấn sâu 10–15 phút.
- **Chủ đề:** Thói quen ăn uống khi chuyển mùa, cách chọn món ăn khi bị cảm mạo nhẹ, sự hoài nghi với thông tin y học dân gian trên mạng, thực trạng lãng phí nguyên liệu thừa.
- **Thời gian thực hiện:** 29/09/2026.
- **Người phỏng vấn:** Nguyễn Quốc Huy (chính) và Nguyễn Duy Trường (ghi chép).

### Câu hỏi gợi ý

1. Khi trời đổi mùa (mưa lạnh, nồm ẩm) hoặc thấy cơ thể hơi uể oải, đau họng, bạn thường ăn gì và quyết định món đó thế nào?
2. Bạn có hay tra cứu thông tin ăn uống Đông y/kinh nghiệm dân gian trên mạng không? Nguồn nào bạn tin và nguồn nào bạn thấy hoang mang?
3. Bạn có thường xuyên phải vứt bỏ thực phẩm thừa trong tủ lạnh không? Nguyên nhân vì sao?
4. Bạn đã từng dùng thử ứng dụng dinh dưỡng hay đếm calo chưa? Lý do bạn từ bỏ là gì?
5. Khi đang nấu ăn hoặc đi làm về mệt, bạn cầm điện thoại bằng một tay hay hai tay? Thao tác có gặp khó khăn gì không?

### Ba trích dẫn tiêu biểu

1. *"Đi làm về muộn 7 giờ tối vừa đói vừa đau họng, mở tủ ra thấy còn nửa củ gừng với ít thịt gà mà chẳng biết nấu canh gì nhanh. Lên mạng tra thì toàn ra mấy bài thuốc Đông y cầu kỳ bắt mua đủ thứ vị thuốc bắc nên thôi, mình lại ra đầu ngõ ăn bát phở cho xong."*  
   — **Nguyễn Phương Linh**, 24 tuổi, nhân viên marketing thuê trọ tại Cầu Giấy, sống một mình.

2. *"Mình cực kỳ sợ mấy bài viết 'ăn món này trị dứt điểm bệnh kia' giật tít trên TikTok. Ai mách mẹo dân gian gì thì mình phải biết rõ sách nào viết, có bác sĩ nào nói không thì mới dám nấu theo."*  
   — **Hoàng Minh Đức**, 25 tuổi, lập trình viên mới đi làm tại Nam Từ Liêm, thường xuyên ăn ngoài.

3. *"App dinh dưỡng hiện nay phiền phức kinh khủng, ăn quả chuối hay bát canh cũng bắt nhập gram với tính calo, dùng được hai ngày là xóa. Đi làm về mệt rã rời chỉ cần một gợi ý nấu nhanh dưới nửa tiếng bằng đúng đồ có sẵn trong tủ là tốt lắm rồi."*  
   — **Trần Thùy Dương**, 23 tuổi, nhân viên hành chính sống trọ tại Đống Đa.

### Điều rút ra từ phỏng vấn

- **Cần tính tinh gọn và giảm tải nhận thức:** Người sống một mình sau giờ làm việc rất ngại nhập liệu phức tạp. App phải đưa ra gợi ý tức thì chỉ với vài lần chạm đơn giản trên sơ đồ cơ thể thay vì bảng biểu số liệu.
- **Niềm tin đến từ nguồn dẫn chứng minh bạch:** Người dùng trẻ cảnh giác cao với thông tin y học trôi nổi. App bắt buộc phải trích dẫn tên sách nguồn kinh điển (*Tuệ Tĩnh Toàn Tập*, *Ẩm thực dưỡng sinh*) và luôn giữ giọng văn khiêm tốn, khuyến cáo rõ ràng không thay thế bác sĩ.
- **Tính năng quét tủ lạnh phải mang tính thực tế:** Không bắt người dùng chuẩn bị nguyên liệu hoàn hảo mà tập trung "giải cứu" nguyên liệu lẻ sẵn có (gà, gừng, hành, trứng, rau thừa) thành món ăn ấm bụng.

---

## 5. Nguyên tắc nội dung và an toàn (Tuân thủ nghiêm ngặt)

- App chỉ **gợi ý ăn uống hỗ trợ theo kinh nghiệm dân gian**, tuyệt đối không chẩn đoán y khoa, không kê đơn thuốc và không thay thế bác sĩ.
- Khi người dùng chọn triệu chứng báo động đỏ (*sốt cao kéo dài trên 38.5°C, khó thở, đau ngực dữ dội, nôn ra máu, đau bụng quằn quại...*), app lập tức chuyển sang giao diện cảnh báo y tế khuyên người dùng đến bệnh viện khám ngay, dừng toàn bộ luồng gợi ý món ăn.
- Khi thiết lập hồ sơ (S12), app luôn hỏi về tiền sử dị ứng và kiêng kỵ (ví dụ: dị ứng hải sản, kiêng cay), tự động loại trừ mọi món ăn chứa thành phần cấm trước khi hiển thị cho người dùng.
- Mọi nội dung y lý đều được trích xuất từ 2 cuốn sách nguồn, diễn giải lại bằng lời văn gần gũi của nhóm và đính kèm trường nguồn kiểm chứng:
  - **Tuệ Tĩnh Toàn Tập** (Nguyễn Bá Tĩnh biên soạn, NXB Y học): 
    - *Chương/Trang sử dụng:* Quyển Thượng — Dược phẩm điều yếu (các mục về Sinh khương/Gừng tươi trang 42–45, Thông bạch/Hành hoa trang 58); Thập tam phương gia giảm (Ẩm thực trị liệu giải biểu, tán hàn, ích khí trang 112–118).
  - **Ẩm thực dưỡng sinh: Phòng bệnh bằng cách ăn uống đúng phép** (Bùi Quốc Châu, NXB Hồng Đức): 
    - *Chương/Trang sử dụng:* Chương 2 — Nguyên lý Âm Dương và Hàn Nhiệt trong thức ăn (bảng phân loại thực phẩm tính Ôn, Nhiệt, Hàn, Lương trang 35–52); Chương 4 — Ăn uống thuận theo thời tiết bốn mùa và thể trạng người Việt (trang 88–104).

---

## 6. Khai báo sử dụng AI

- **Công cụ AI đã sử dụng khi soạn tài liệu này:** Google Stitch (AI UI Generation), Claude 3.5 Sonnet (hỗ trợ cấu trúc tài liệu và chuẩn hóa văn phong tiếng Việt).
- **Phần do AI hỗ trợ:** Khung sườn ban đầu của bảng persona, gợi ý cách bố cục câu hỏi phỏng vấn định tính và định dạng chuẩn Markdown.
- **Phần do nhóm tự làm và kiểm chứng:** 
  - Thực hiện phỏng vấn trực tiếp 4 bạn sinh viên/người đi làm thật, ghi âm và trích dẫn lời nói nguyên văn.
  - Tổ chức đo đạc thực nghiệm với 5 người dùng trên prototype Figma, tính toán thời gian và số lần chạm trung bình.
  - Tra cứu trực tiếp nội dung chương, trang của 2 cuốn sách nguồn để ghi nhận vào tài liệu.
  - Phân tích và đưa ra quyết định cải tiến bố cục màn hình S02 và S03.

---

## 7. Lịch sử chỉnh sửa

| Ngày | Người sửa | Nội dung |
|---|---|---|
| 28/09/2026 | Nguyễn Quốc Huy | Tạo bản đầu (v1.0.0) — Thiết lập khung persona giả định và tiêu chí thành công. |
| 01/10/2026 | Nguyễn Duy Trường | Bổ sung kết quả phỏng vấn nhanh 4 bạn và đính kèm 3 trích dẫn định tính tiêu biểu. |
| 03/10/2026 | Nguyễn Quốc Huy | Cập nhật v1.1.0 — Điền kết quả đo thử nghiệm prototype 5 người, trích dẫn chương/trang sách Tuệ Tĩnh và Bùi Quốc Châu, hoàn thiện tiêu chuẩn an toàn y tế. |