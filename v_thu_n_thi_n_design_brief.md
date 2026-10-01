# Vị Thuận Thiên — Design Brief & Design System Specification (`DESIGN.md`)

> **Dự án:** Vị Thuận Thiên (Heritage & Elemental Nutrition — Book to App)  
> **Môn học:** PRM393 (Lab 02: AI-Assisted UI/UX Design & Lab 03: Design to Working App)  
> **Nhóm thực hiện:** Mai Lê Nguyên, Nguyễn Duy Trường, Đặng Thuận Phát, Nguyễn Quốc Huy  
> **Phiên bản:** 1.0.0 (Baseline commit trước khi kích hoạt prompt Stitch AI)  
> **Ngày phê duyệt nội bộ:** 28/09/2026  

---

## 1. Tổng quan sản phẩm & Persona

### 1.1 Tôn chỉ định vị (Value Proposition)
**Vị Thuận Thiên** là ứng dụng trợ lý dinh dưỡng và ẩm thực dưỡng sinh cá nhân hóa dựa trên nguyên lý *"Thuận theo trời đất, thuận theo cơ thể"*. App kết hợp tri thức y học dân gian Việt Nam với công nghệ AI hỗ trợ:
- **Đọc trời:** Cập nhật thời tiết, độ ẩm, tiết khí thực tế (Open-Meteo).
- **Nghe cơ thể:** Thao tác trực tiếp trên bản đồ thể trạng tương tác 2D (Body Map).
- **Xem trong bếp:** Tận dụng nguyên liệu sẵn có trong tủ lạnh gia đình (Vision AI).
- **Gợi ý món ăn:** Đề xuất 1–2 món ăn bài thuốc thực dưỡng Việt thuần khiết kèm phân tích y lý rõ ràng, dễ nấu trong 30 phút.

### 1.2 Persona mục tiêu
- **Họ và tên:** Trần Minh Anh (25 tuổi).
- **Nghề nghiệp:** Chuyên viên văn phòng, sống độc thân tại phòng trọ Hà Nội.
- **Thói quen & bối cảnh:** Tan làm lúc 18:30 trong tình trạng mệt mỏi, thời tiết miền Bắc đổi mùa mưa lạnh đột ngột, có triệu chứng chớm đau rát họng, tủ lạnh còn một ít nguyên liệu rời (thịt gà, gừng, hành lá).
- **Điểm đau (Pain points):** Thông tin Đông y trên mạng xáo trộn thiếu kiểm chứng; ngại các app tính calo phức tạp bắt cân đo gram; dễ lãng phí thực phẩm thừa; dễ ăn uống qua loa dẫn đến giảm đề kháng.
- **Tiêu chí thành công đo được (Success Metric):** Từ khi mở app (đã đăng nhập) đến khi nhận được gợi ý món ăn chuẩn xác: **$\le 6$ lần chạm** và **$\le 45$ giây**.

---

## 2. Nền tảng tri thức nguồn (Book to App) & An toàn y tế

Tài liệu thiết kế kế thừa trực tiếp từ 02 tác phẩm kinh điển y học dân gian:
1. **Tuệ Tĩnh Toàn Tập (Đại y thiền sư Nguyễn Bá Tĩnh - NXB Y học):**
   - *Triết lý:* "Nam dược trị Nam nhân" — sử dụng thảo mộc, gia vị và sản vật địa phương Việt Nam gần gũi (gừng, tía tô, hành hoa, hạt sen...) để bồi bổ và quân bình tạng phủ.
   - *Ứng dụng:* Cung cấp trường giải thích y lý dân gian (`reason`) và công thức thực dưỡng cho các món ăn (`S06`, `S07`).
2. **Ẩm thực dưỡng sinh (Lương y Bùi Quốc Châu - NXB Hồng Đức):**
   - *Triết lý:* Phân định tính chất thức ăn theo Hàn - Nhiệt - Ôn - Lương - Bình; phối ngũ cân bằng Âm - Dương theo khí hậu và trạng thái cơ thể.
   - *Ứng dụng:* Thiết lập ma trận chấm điểm sàng lọc món ăn rule-based (`dishes.json`) tương ứng 5 biến thể Ngũ hành/thời tiết và triệu chứng Body Map.

### Nguyên tắc an toàn y tế bắt buộc (Safety First)
- **Tuyên bố trách nhiệm (Disclaimer):** Mọi màn hình kết quả và màn hình đăng nhập đều hiển thị dòng khuyến cáo: *"Vị Thuận Thiên gợi ý ăn uống hỗ trợ phục hồi theo kinh nghiệm dân gian, không có chức năng chẩn đoán hay thay thế phác đồ điều trị của bác sĩ."*
- **Sàng lọc dị ứng (Allergy Exclusion):** Tự động lọc bỏ hoàn toàn các món có chứa thành phần kiêng kỵ được cài đặt trong hồ sơ người dùng (`S12`).
- **Phát hiện dấu hiệu nguy hiểm (Red Flags):** Khi người dùng chọn các triệu chứng cảnh báo cấp cứu (sốt cao co giật, khó thở, đau ngực dữ dội, nôn ra máu, đau bụng quằn quại), hệ thống **ngay lập tức chặn luồng gợi ý món** và hiển thị màn hình cảnh báo y tế khẩn cấp, hướng dẫn đến cơ sở y tế gần nhất.

---

## 3. Ngôn ngữ thị giác & Giọng điệu (Brand Voice & Tone)

- **Giọng văn (Microcopy):** Bình tĩnh, mực thước, ấm áp, thấu hiểu; xưng hô thân mật, mộc mạc; tuyệt đối không dùng từ ngữ giật gân, đe dọa bệnh lý hay thuật ngữ học thuật khó hiểu.
- **Phong cách thị giác (Visual Style):** Á Đông tối giản (Vietnamese Heritage Minimalist).
  - Tận dụng khoảng trắng thoáng đãng (Breathing space).
  - Nền giấy mộc (Kem/Thổ), nét vẽ thanh thoát phảng phất chất tranh khắc gỗ dân gian.
  - Hình khối bo góc mềm mại, gần gũi với thiên nhiên; từ chối dải màu gradient bóng bẩy, loại bỏ drop-shadow cường độ cao.

---

## 4. Hệ thống Design Tokens (Theme: Light Mode làm chuẩn)

### 4.1 Bảng màu cốt lõi & Tỷ lệ tương phản WCAG 2.1 AA/AAA

| Tên Token (Variable) | Mã Hex | Ý nghĩa / Ứng dụng | Cặp kiểm tra tương phản | Tỷ lệ Contrast | Đánh giá WCAG |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `color/text-primary` (Mực) | `#262A26` | Chữ chính, tiêu đề, icon chính | Mực trên Kem (`#FBF6EA`) | **13.51:1** | Đạt (AAA) |
| `color/primary` (Mộc) | `#2F5D4B` | Nút chính, liên kết, trạng thái active | Mộc trên Kem (`#FBF6EA`) | **6.98:1** | Đạt (AAA) |
| `color/on-primary` | `#FFFFFF` | Chữ / icon hiển thị trên nền Mộc | Trắng trên Mộc (`#2F5D4B`) | **7.53:1** | Đạt (AAA) |
| `color/secondary` (Hỏa) | `#A7432A` | Điểm nhấn ấm, tag cảnh báo nhẹ | Hỏa trên Kem (`#FBF6EA`) | **5.60:1** | Đạt (AA) |
| `color/accent` (Kim) | `#C98B1F` | Nhãn tiết khí, huy hiệu, sao rating | Mực (`#262A26`) trên Kim | **4.99:1** | Đạt (AA) |
| `color/info` (Thủy) | `#2C4A6B` | Nhấn theo thời tiết lạnh/mưa | Thủy trên Kem (`#FBF6EA`) | **8.47:1** | Đạt (AAA) |
| `color/text-muted` | `#5E6258` | Phụ đề, mô tả thứ cấp, metadata | Muted trên Kem (`#FBF6EA`) | **5.79:1** | Đạt (AA) |
| `color/outline` | `#7A7E72` | Viền ô nhập liệu, đường phân tách card | Viền trên Kem (UI elements $\ge 3:1$) | **3.85:1** | Đạt (UI AA) |
| `color/error` | `#B3261E` | Trạng thái lỗi hệ thống, hủy nguy hiểm | Lỗi trên Kem (`#FBF6EA`) | **6.06:1** | Đạt (AA) |
| `color/surface-container` (Thổ) | `#EADFC6` | Nền thẻ (card), chip nguyên liệu, tag | Mực (`#262A26`) trên Thổ | **11.01:1** | Đạt (AAA) |
| `color/surface` | `#FFFDF7` | Nền nội dung nổi bật, modal sheet | Mực (`#262A26`) trên Surface | **15.20:1** | Đạt (AAA) |
| `color/background` (Kem) | `#FBF6EA` | Màu nền canvas ứng dụng | — | — | — |

### 4.2 Biến thể màu nhấn Ngũ Hành theo thời tiết (Weather-Adaptive Theme)
*Lưu ý: Chỉ thay đổi màu minh họa và màu nhấn (tint), giữ nguyên token `color/text-primary` để luôn đảm bảo tính tiếp cận.*
- **Hành Thủy (`#2C4A6B` / Tint `#DCE6F0`):** Áp dụng khi trời mưa, lạnh ($< 20^\circ\text{C}$). Nhấn mạnh món tính ấm (gừng, tía tô).
- **Hành Hỏa (`#A7432A` / Tint `#F6DDD5`):** Áp dụng khi trời oi bức, nắng nóng ($\ge 32^\circ\text{C}$). Nhấn mạnh món thanh nhiệt, giải độc.
- **Hành Kim (`#C98B1F` / Tint `#F6E7C4`):** Áp dụng khi thời tiết khô hanh, gió lạnh. Nhấn mạnh món nhuận phế, bổ âm.
- **Hành Thổ (`#8A6D3B` / Tint `#EADFC6`):** Áp dụng khi trời nồm ẩm, chuyển mùa. Nhấn mạnh món kiện tỳ, trừ thấp, ấm bụng.
- **Hành Mộc (`#2F5D4B` / Tint `#DDEBE3`):** Áp dụng khi tiết trời mát mẻ, nắng nhẹ. Nhấn mạnh món dưỡng can, rau xanh tươi mới.

### 4.3 Kiểu chữ (Typography)
- **Display / Heading Font:** `Noto Serif` (Google Fonts) — Đậm nét cổ điển, thể hiện sự tĩnh tại và bề dày tri thức y lý.
- **Body / Interface Font:** `Be Vietnam Pro` (Google Fonts) — Thiết kế tối ưu hóa hiển thị tiếng Việt, dấu thanh cân đối, hình học hiện đại.
- **Thang kích thước & Giãn dòng (Type Scale):**
  - `Display Large`: $32\,\text{sp}$ / Line-height $40\,\text{dp}$ (Noto Serif Bold)
  - `Headline Medium`: $24\,\text{sp}$ / Line-height $32\,\text{dp}$ (Noto Serif SemiBold)
  - `Title Medium`: $18\,\text{sp}$ / Line-height $24\,\text{dp}$ (Be Vietnam Pro SemiBold)
  - `Body Large`: $16\,\text{sp}$ / Line-height $24\,\text{dp}$ (Be Vietnam Pro Regular)
  - `Body Medium`: $14\,\text{sp}$ / Line-height $20\,\text{dp}$ (Be Vietnam Pro Regular — **ngưỡng nhỏ nhất cho nội dung văn bản đọc**)
  - `Label Small`: $12\,\text{sp}$ / Line-height $16\,\text{dp}$ (Be Vietnam Pro Medium — chỉ dùng cho badge/tag/caption phụ)

### 4.4 Khoảng cách (Spacing Grid) & Bo góc (Corner Radius)
- **Lưới cơ sở:** Bội số của $4\,\text{dp}$.
- **Hệ thống Spacing:**
  - `space/0.5` = $2\,\text{dp}$ | `space/1` = $4\,\text{dp}$ | `space/2` = $8\,\text{dp}$
  - `space/3` = $12\,\text{dp}$ | `space/4` = $16\,\text{dp}$ (Lề màn hình chuẩn)
  - `space/6` = $24\,\text{dp}$ | `space/8` = $32\,\text{dp}$ | `space/12` = $48\,\text{dp}$
- **Hệ thống Radius:**
  - `radius/xs` = $4\,\text{dp}$
  - `radius/sm` = $8\,\text{dp}$ (Chips, nhãn, tag)
  - `radius/md` = $12\,\text{dp}$ (Button, Text Field, ô nhập liệu)
  - `radius/lg` = $20\,\text{dp}$ (Thẻ Card, Banner)
  - `radius/xl` = $28\,\text{dp}$ (Bottom Sheet, Dialog)
- **Độ nổi (Elevation):** Ưu tiên Tonal Surface (phân biệt cấp bậc bằng sắc độ màu nền), hạn chế dùng drop shadow nặng:
  - `Elevation 0`: Nền màn hình (`#FBF6EA`).
  - `Elevation 1`: Thẻ card (`#FFFDF7` hoặc viền `outline` $1\,\text{dp}$).
  - `Elevation 2`: App bar khi cuộn nội dung, NavigationBar dưới cùng.
  - `Elevation 3`: Modal Bottom Sheet, Dialog pop-up.

---

## 5. Danh mục 13 màn hình chuẩn hóa

| ID | Tên màn hình | Phân cấp điều hướng | Mục đích & Trọng tâm tương tác |
| :--- | :--- | :--- | :--- |
| **S01** | Đăng nhập (Authentication) | Ngoài Tab Bar | Logo nhận diện, thông điệp định vị, nút Google Sign-In, khuyến cáo an toàn. |
| **S02** | Trang chủ Chẩn Vị (Home) | Tab 1 (Gốc) | Thẻ thời tiết & tiết khí, nút chính *"Chẩn vị hôm nay"*, chuông thông báo, banner RC. |
| **S03** | Sơ đồ thể trạng (Body Map) | Con của S02 | Canvas cơ thể 2D chạm vùng, bottom sheet chọn triệu chứng, công tắc chế độ Danh sách. |
| **S04** | Tủ lạnh Thuận Thiên (Fridge) | Con của S02 | Chụp/quét ảnh nguyên liệu tủ lạnh, danh sách chip (sửa/xóa/thêm), nút bỏ qua. |
| **S05** | Chuỗi xử lý AI (Processing) | Con của S02 | Hoạt họa nồi đất sôi, 4 bước kể chuyện (*Đọc trời $\rightarrow$ Nghe mình $\rightarrow$ Xem bếp $\rightarrow$ Chọn món*), nút Hủy. |
| **S06** | Thuận Thiên Món (Result) | Con của S02 | 1–2 gợi ý món, lý do y lý, nguyên liệu tủ lạnh tận dụng, nút Lưu vào Sổ tay & Nấu ngay. |
| **S07** | Công thức chi tiết (Recipe) | Con của S06/S09 | Thành phần, định lượng, các bước nấu dưỡng sinh, lưu ý bảo tồn dược tính. |
| **S08** | Sổ tay Thuận Thiên (Notebook) | Tab 2 (Gốc) | Danh sách món đã lưu, bộ lọc triệu chứng/thể trạng, sắp xếp thời gian/rating, thanh tìm kiếm. |
| **S09** | Chi tiết món Sổ tay (Note Edit) | Con của S08 | Xem ghi chú cảm nhận, chấm điểm sao, cập nhật ghi chú thực dưỡng, nút Xóa món. |
| **S10** | Lịch sử chẩn vị (History) | Tab 3 (Gốc) | Dòng thời gian (timeline) các lần chẩn vị: thời tiết lúc đó, triệu chứng ghi nhận, món đề xuất. |
| **S11** | Trung tâm thông báo (Notif) | Từ chuông S02 | Danh sách thông báo đẩy FCM, badge chưa đọc, chạm điều hướng sâu tới màn hình chỉ định. |
| **S12** | Hồ sơ & Cài đặt (Profile) | Tab 4 (Gốc) | Thông tin tài khoản, danh sách dị ứng kiêng kỵ, cỡ chữ hiển thị, khu vực công cụ kiểm thử. |
| **S13** | Xuất báo cáo tuần (PDF Export) | Con của S12 | Xem trước số liệu thể trạng trong tuần, nút Xuất PDF, hiển thị link xem/tải sau khi upload. |

---

## 6. Đặc tả UX các màn hình phức tạp

### 6.1 Body Map tương tác (`S03`)
- **Bố cục:** Tỷ lệ khung người chuẩn hóa $0.0 \rightarrow 1.0$ vẽ bằng vector Path, tự động co giãn theo `LayoutBuilder` ở cả bề rộng $360\,\text{dp}$ và $412\,\text{dp}$.
- **8 phân vùng chạm:** Đầu/Mặt, Cổ họng, Lồng ngực, Bụng trên (Tỳ Vị), Bụng dưới, Lưng/Thắt lưng (công tắc lật trước/sau), Hai tay, Hai chân.
- **Quy tắc công thái học & Vùng chạm:**
  - Mọi vùng chạm tối thiểu **$48 \times 48\,\text{dp}$** (các vùng hẹp như Cổ, Cổ tay được bọc thêm `hitBox` vô hình).
  - Khi người dùng chạm: Vùng chạm lập tức sáng nhẹ (viền Mộc + màu nền loang nhẹ $30\%$ opacity), máy rung nhẹ (Haptic feedback), đồng thời kéo Modal Bottom Sheet chứa danh sách chip triệu chứng tương ứng với 3 mức độ: *Nhẹ | Vừa | Nặng*.
  - Chỉ báo trực quan: Vùng đã chọn hiển thị số lượng triệu chứng bằng Badge chấm tròn có số, không phụ thuộc duy nhất vào màu sắc.
- **Trợ năng (Accessibility Mode):** Có nút chuyển đổi rõ ràng *"Xem dạng danh sách"* ở góc trên. Chuyển đổi toàn bộ sang danh sách thẻ có nhãn ngữ nghĩa (Semantics) hỗ trợ chuẩn mực cho trình đọc màn hình TalkBack.

### 6.2 Chuỗi xử lý AI kể chuyện (`S05`)
- Thay thế hoàn toàn thanh loading/spinner đơn điệu bằng trải nghiệm thị giác tĩnh tâm.
- Minh họa hoạt họa nồi đất sôi mộc mạc, lần lượt chạy qua 4 trạng thái nội dung có thời gian đệm mượt mà:
  1. *"Đang nhóm lửa... Đọc thời tiết Hà Nội ($18^\circ\text{C}$, mưa lạnh)"*
  2. *"Nghe ngóng thể trạng (chớm đau rát họng, mức độ nhẹ)"*
  3. *"Xem trong góc bếp (thịt gà, củ gừng, nhánh hành lá)"*
  4. *"Cân bằng âm dương, chọn món thuận thiên..."*
- **Kiểm soát thời gian:** Sau 12 giây chưa có phản hồi từ mạng, hiển thị gợi ý: *"Đang mất nhiều thời gian hơn bình thường... Bạn muốn tiếp tục đợi hay xem ngay gợi ý cơ bản không cần mạng?"* kèm nút Hủy an toàn.

---

## 7. Quy tắc thiết kế Component & Microcopy trạng thái

### 7.1 Quy tắc Component hệ thống
1. **Nút bấm (Buttons):** Chiều cao tối thiểu $48\,\text{dp}$. Mỗi màn hình chỉ có **duy nhất 1 nút Primary** (Filled Button nền Mộc) nằm ở nửa dưới màn hình để dễ chạm một tay. Các nút phụ dùng OutlinedButton hoặc TextButton.
2. **Ô nhập liệu (Text Fields):** Viền bo góc $12\,\text{dp}$, viền thường màu `outline` $1\,\text{dp}$, khi focus chuyển sang viền `primary` $2\,\text{dp}$. Thông báo lỗi luôn đi kèm icon cảnh báo và chữ giải thích cụ thể dưới ô nhập.
3. **Thẻ Card:** Bo góc $20\,\text{dp}$, sử dụng màu nền `surface-container` (`#EADFC6`) hoặc `surface` (`#FFFDF7`), khoảng cách padding nội dung chuẩn $16\,\text{dp}$.
4. **Hộp thoại (Dialogs):** Dialog xóa món thuộc dạng hành động nguy hiểm: Nút xác nhận xóa dùng màu `error` (`#B3261E`), nút giữ lại là OutlinedButton.

### 7.2 Microcopy cho các trạng thái đặc thù
- **Empty State (`S08`):** Hình vẽ niêu đất/lá cây tĩnh lặng. Câu chữ: *"Sổ tay của bạn còn trống. Sau mỗi lần chẩn vị, hãy lưu lại món ăn bạn yêu thích vào đây nhé."* $\rightarrow$ Nút hành động: *"Bắt đầu chẩn vị"*.
- **Error State (`S05` / `S13`):** Tránh mã lỗi kỹ thuật. Câu chữ: *"Chưa thể kết nối với đất trời do mạng internet chập chờn. Bạn kiểm tra lại wifi/4G hoặc xem gợi ý thực dưỡng ngoại tuyến nhé."* $\rightarrow$ 2 nút: *"Thử lại"* và *"Xem gợi ý cơ bản"*.
- **Hành động phục hồi (Undo):** Khi người dùng xóa một món khỏi Sổ tay (`S09`), hệ thống chuyển về `S08` kèm SnackBar xuất hiện trong 5 giây: *"Đã xóa món khỏi Sổ tay"* kèm nút tương tác *"Hoàn tác"*.

---

## 8. Nguyên tắc cấm kỵ trong thiết kế (Design Constraints)

- **CẤM** sử dụng gradient đa sắc rực rỡ mang phong cách Cyberpunk/Neon hoặc đổ bóng đen đục nặng nề.
- **CẤM** cỡ chữ nội dung (body text) nhỏ hơn **$14\,\text{sp}$**.
- **CẤM** vùng chạm (touch target) nhỏ hơn **$48 \times 48\,\text{dp}$**.
- **CẤM** sử dụng màu sắc đơn độc để biểu thị trạng thái (luôn kết hợp icon, văn bản hoặc viền nét).
- **CẤM** sử dụng từ ngữ mang tính khẳng định điều trị y khoa ("chữa khỏi", "trị dứt điểm bệnh", "thuốc đặc trị").
- **CẤM** để xuất hiện bất kỳ màn hình cụt (dead-end screen) nào trong Prototype: mọi màn hình đều có nút quay lại (Back) hoặc đường dẫn về Trang chủ.