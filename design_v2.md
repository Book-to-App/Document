# VỊ THUẬN THIÊN — DESIGN BRIEF & SPECIFICATION (DESIGN.md)
> **Dự án:** Vị Thuận Thiên (PRM393 - Lab 02 & Lab 03)  
> **Nền tảng:** Android (Mục tiêu 360 x 800 dp, đáp ứng tốt 412 dp và tablet >= 600 dp)  
> **Tiêu chuẩn thiết kế:** Material Design 3 (M3) — HCT Tone-based Color System & Accessibility (WCAG 2.1 AA)  
> **Phiên bản:** 2.0 (Cập nhật chuẩn hóa M3 Color Tokens & Surface Containers)

---

## 1. Định vị sản phẩm & Người dùng mục tiêu

### 1.1 Định vị
**Vị Thuận Thiên** là ứng dụng trợ lý ăn uống cá nhân hóa "thuận theo trời và theo người" dành cho người Việt. Ứng dụng tích hợp ngữ cảnh thời tiết thực tế (Open-Meteo), lắng nghe thể trạng trực quan qua sơ đồ cơ thể (Body Map), nhận diện nguyên liệu sẵn có trong tủ lạnh (Multimodal AI) để đưa ra gợi ý 1–2 món ăn Việt truyền thống phù hợp, kèm lời giải thích theo y lý dân gian.

### 1.2 Persona đại diện
* **Họ và tên:** Trần Minh Anh (25 tuổi).
* **Nghề nghiệp / Nơi ở:** Nhân viên văn phòng mới đi làm, thuê trọ tại Hà Nội, không gian bếp nhỏ, thường ăn ngoài hoặc nấu nhanh sau giờ làm. Thiết bị sử dụng: Android tầm trung.
* **Bối cảnh điển hình:** 18:30 tan làm, trời chuyển mùa mưa lạnh, cơ thể hơi mệt và đau rát cổ họng. Tủ lạnh còn ít nguyên liệu lẻ (thịt gà, gừng, hành lá). Cần một gợi ý món ấm bụng, nấu nhanh dưới 30 phút mà không tốn công suy nghĩ hay đọc các bài thuốc phức tạp.
* **Nỗi đau (Pain points):** Thông tin Đông y trên mạng nhiễu loạn; ứng dụng dinh dưỡng hiện nay bắt tính calo/macro rườm rà; rau củ mua về thường bị bỏ phí.
* **Problem Statement (1 câu):** Người trẻ sống một mình ở đô thị khó biết nên ăn gì khi thời tiết đổi mùa và cơ thể không khỏe, dẫn đến ăn uống tùy tiện và lãng phí nguyên liệu trong bếp.
* **Tiêu chí thành công (đo được):** Từ khi mở app (đã đăng nhập) đến khi nhận được gợi ý món ăn: **dưới 45 giây và không quá 6 lần chạm**.

---

## 2. Nguyên tắc y lý từ sách nguồn (Book to App)

App kế thừa tri thức y học cổ truyền dân tộc từ 2 bộ sách, tuân thủ nguyên tắc "Nam dược trị Nam nhân" và ẩm thực trị liệu:
1. **Tuệ Tĩnh Toàn Tập (Nguyễn Bá Tĩnh - NXB Y học):**
   * *Triết lý cốt lõi:* Lấy sản vật thảo mộc gần gũi quanh vườn nhà làm phương tiện bồi bổ, điều hòa khí huyết.
   * *Ứng dụng vào app:* Trích xuất lý do y lý cho từng món (ví dụ: dùng gừng, hành, tía tô có tính ấm để phát tán phong hàn khi gặp mưa lạnh).
2. **Ẩm thực dưỡng sinh (Bùi Quốc Châu - NXB Hồng Đức):**
   * *Triết lý cốt lõi:* Phòng bệnh qua ăn uống đúng cách theo phân loại tính chất: Hàn (lạnh), Lương (mát), Ôn (ấm), Nhiệt (nóng), Bình (trung tính).
   * *Ứng dụng vào app:* Làm bộ tiêu chuẩn chấm điểm và lọc món ứng viên trước khi đưa vào mô hình AI.

> **Nguyên tắc an toàn (bắt buộc):**  
> Ứng dụng chỉ đưa ra gợi ý ẩm thực bồi bổ hỗ trợ dân gian, **tuyệt đối không chẩn đoán y khoa, không kê đơn thuốc và không thay thế bác sĩ**. Luôn lọc dị ứng của người dùng trước khi hiển thị. Khi phát hiện các triệu chứng báo động đỏ (*sốt cao kéo dài, khó thở, đau ngực dữ dội, nôn ra máu...*), app lập tức chuyển sang màn hình cảnh báo khuyên người dùng đến cơ sở y tế.

---

## 3. Hệ thống màu chuẩn Material Design 3 (M3 Color System)

Tuân thủ nguyên tắc của Material 3: **Màu sắc và độ tương phản được quyết định hoàn toàn bởi giá trị Tone (0 - 100) trong không gian màu HCT**, loại bỏ bóng đổ nặng và thay thế bằng hệ thống **Tone-based Surface Containers**.

### 3.1 Key Seed Color
* **Primary Seed:** `#2F5D4B` (Hành Mộc — Xanh thực vật mộc mạc Á Đông).
* **Secondary Seed:** `#A7432A` (Hành Hỏa — Đỏ gạch nung ấm áp).
* **Tertiary Seed:** `#C98B1F` (Hành Kim — Vàng thổ hoàng, sao đánh giá).
* **Neutral Seed:** Ngả ấm sắc Kem tự nhiên (`#FBF6EA`).

### 3.2 Bảng phân bổ Color Roles & Tokens (M3 Light Theme)

| M3 Token Role | Hex Code | Tone HCT | Vai trò & Áp dụng trong giao diện | WCAG Contrast Ratio |
| :--- | :---: | :---: | :--- | :---: |
| **`primary`** | `#2F5D4B` | Tone 40 | Nút chính (FilledButton "Chẩn vị hôm nay"), icon tiêu điểm | Trắng trên Primary: **7.53:1** (Đạt AAA) |
| **`onPrimary`** | `#FFFFFF` | Tone 100 | Chữ & icon hiển thị trên nền `primary` | Đạt chuẩn AA/AAA |
| **`primaryContainer`** | `#DDEBE3` | Tone 90 | Chip thể trạng đã chọn, nền thẻ nổi bật mức vừa | Chữ trên Container: **9.2:1** (Đạt AAA) |
| **`onPrimaryContainer`** | `#002114` | Tone 10 | Chữ & icon nằm trên `primaryContainer` | Đạt chuẩn AAA |
| **`secondary`** | `#A7432A` | Tone 40 | Màu nhấn thứ cấp (ấm áp, cảnh báo mức vừa) | Trắng trên Secondary: **5.60:1** (Đạt AA) |
| **`onSecondary`** | `#FFFFFF` | Tone 100 | Chữ trên nền `secondary` | Đạt chuẩn AA |
| **`secondaryContainer`** | `#F6DDD5` | Tone 90 | Nền thẻ thời tiết oi bức (Hỏa), chip phân loại nhiệt | Đạt chuẩn AA |
| **`onSecondaryContainer`**| `#3E0400` | Tone 10 | Chữ trên `secondaryContainer` | Đạt chuẩn AAA |
| **`tertiary`** | `#825500` | Tone 40 | Nhấn phụ, sao đánh giá chất lượng món ăn (Rating) | Chữ trên Tertiary: **4.99:1** (Đạt AA) |
| **`onTertiary`** | `#FFFFFF` | Tone 100 | Chữ/icon trên nền `tertiary` | Đạt chuẩn AA |
| **`tertiaryContainer`** | `#F6E7C4` | Tone 90 | Huy hiệu tiết khí, chip mức độ triệu chứng nhẹ | Đạt chuẩn AAA |
| **`onTertiaryContainer`** | `#291800` | Tone 10 | Chữ trên `tertiaryContainer` | Đạt chuẩn AAA |
| **`surface`** | `#FBF6EA` | Tone 98 | Nền tổng thể màn hình (Scaffold Background) | Mực trên Surface: **13.51:1** (Đạt AAA) |
| **`onSurface`** | `#1B1C18` | Tone 10 | Chữ nội dung chính, tiêu đề màn hình | Đạt chuẩn AAA |
| **`surfaceVariant`** | `#E2E4D8` | Tone 90 | Nền thanh tìm kiếm, phân cách nhẹ | Đạt chuẩn AA |
| **`onSurfaceVariant`** | `#45483F` | Tone 30 | Chữ phụ đề, văn bản mô tả phụ (Muted text) | **5.79:1** trên Kem (Đạt AA) |
| **`surfaceContainerLowest`** | `#FFFFFF` | Tone 100| Nền thẻ món ăn (DishCard), Modal Dialog | Đạt phân cấp thị giác M3 |
| **`surfaceContainerLow`** | `#F5F0E4` | Tone 96 | Nền thẻ công thức nấu ăn, thẻ thời tiết | Đạt phân cấp thị giác M3 |
| **`surfaceContainer`** | `#EFEADE` | Tone 94 | Nền NavigationBar (Bottom tab), Search bar | Đạt phân cấp thị giác M3 |
| **`surfaceContainerHigh`** | `#E9E5D9` | Tone 92 | Nền Bottom Sheet Body Map trượt lên | Đạt phân cấp thị giác M3 |
| **`surfaceContainerHighest`** | `#E3DFD3`| Tone 90 | Nền chip chưa chọn, vùng đệm thứ cấp | Đạt phân cấp thị giác M3 |
| **`outline`** | `#75796E` | Tone 50 | Viền trường nhập (TextFormField), viền thẻ | Tương phản viền **>= 3.0:1** |
| **`outlineVariant`** | `#C5C8BA` | Tone 80 | Đường gạch chia Divider, viền phụ | Đạt chuẩn M3 |
| **`error`** | `#BA1A1A` | Tone 40 | Trạng thái lỗi mạng, nút hành động hủy/xóa | Trắng trên Error: **6.06:1** (Đạt AA) |
| **`onError`** | `#FFFFFF` | Tone 100 | Chữ trên nền nút xóa/lỗi | Đạt chuẩn AA |
| **`errorContainer`** | `#FFDAD6` | Tone 90 | Thẻ cảnh báo triệu chứng nguy hiểm cần đi khám | Đạt chuẩn AA |
| **`onErrorContainer`** | `#410002` | Tone 10 | Chữ thông báo khuyên đi khám trong errorContainer| Đạt chuẩn AAA |

### 3.3 Biến thể Custom Color theo Ngũ Hành (Thời tiết động)
Giữ nguyên độ tương phản của chữ (`onSurface`), chỉ thay đổi sắc thái thẻ và màu minh họa:
* **Hành Thủy (Mưa, lạnh < 20°C):** Token mở rộng `#2C4A6B` (Chàm lạnh) | Nền Container: `#DCE6F0`.
* **Hành Hỏa (Nắng nóng, oi bức > 32°C):** Dùng nhóm `secondary` (`#A7432A` / `#F6DDD5`).
* **Hành Kim (Khô hanh, nhiều gió):** Dùng nhóm `tertiary` (`#825500` / `#F6E7C4`).
* **Hành Thổ (Nồm ẩm đặc trưng miền Bắc):** Mã màu `#705D00` | Nền Container: `#EADFC6`.
* **Hành Mộc (Dịu mát, nắng nhẹ):** Trở về nhóm `primary` mặc định (`#2F5D4B` / `#DDEBE3`).

---

## 4. Hệ thống Typography & Spacing (Hệ thống biến số)

### 4.1 Phông chữ (Hỗ trợ tiếng Việt hoàn chỉnh qua Google Fonts)
* **Tiêu đề (Headlines & Titles):** `Noto Serif` (Weight 600 - 700) — Mang âm hưởng truyền thống, trang trọng, gợi nét khắc mộc.
* **Nội dung & Giao diện (Body & Labels):** `Be Vietnam Pro` (Weight 400, 500, 600) — Hiện đại, hình học rõ ràng, tối ưu hiển thị trên màn hình nhỏ.

### 4.2 Thang kích thước chữ (Type Scale)
* **Display Small:** 32sp / Line-height 40sp (Đậm) — Số đo lớn, điểm nhấn nhiệt độ.
* **Headline Medium:** 24sp / Line-height 32sp (Noto Serif Bold) — Tiêu đề trang chính.
* **Title Large / Medium:** 18sp / 24sp — Tiêu đề thẻ món ăn, tiêu đề nhóm.
* **Body Large (Nội dung chính):** 16sp / Line-height 24sp (Tối thiểu cho bài đọc công thức).
* **Body Medium (Nội dung phụ):** 14sp / Line-height 20sp (Quy định bắt buộc: **không dùng body < 14sp**).
* **Label Medium / Small:** 12sp / Line-height 16sp (Chỉ dùng cho chú thích nhỏ, badge, nhãn phụ).

### 4.3 Lưới khoảng cách (Spacing Grid) & Bo góc (Shape)
* **Lưới 4dp căn bản:** `4dp`, `8dp`, `12dp`, `16dp` (Lề màn hình chuẩn), `24dp`, `32dp`, `48dp`.
* **Vùng chạm tối thiểu (Touch Target):** **$48 \times 48\text{ dp}$** cho tất cả các nút bấm, chip và vùng chạm trên Body Map.
* **Thang bo góc (Corner Radius):**
  * `Radius 8dp`: Chips nguyên liệu, Tag thể trạng.
  * `Radius 12dp`: Nút bấm (Button), Hộp nhập liệu (Text Field).
  * `Radius 20dp`: Thẻ nội dung (Cards — Weather Card, Dish Card).
  * `Radius 28dp`: Bottom Sheet (Sơ đồ thể trạng, bộ lọc).

---

## 5. Danh mục 13 màn hình & Cấu trúc điều hướng

Ứng dụng sử dụng cấu trúc **NavigationBar 4 Tab chính** ở đáy màn hình:
1. **S01 — Đăng nhập (Login):** Logo, giới thiệu, nút Google Sign-In, khuyến cáo an toàn ngắn gọn.
2. **S02 — Trang chủ / Chẩn Vị (Tab 1):** Thẻ thời tiết thời gian thực, nhịp 24 tiết khí, nút chính *"Chẩn vị hôm nay"*, banner Remote Config.
3. **S03 — Sơ đồ thể trạng (Body Map):** Tương tác chạm hình thể 2D (trước/sau), mở Bottom Sheet chọn mức độ, công tắc chuyển dạng danh sách (Trợ năng TalkBack).
4. **S04 — Tủ lạnh Thuận Thiên:** Chụp/chọn ảnh tủ lạnh, chip nguyên liệu nhận diện có thể thêm/xóa/sửa (Human-in-the-loop).
5. **S05 — Đang xử lý AI:** Hoạt cảnh nồi đất ninh sôi, chuỗi 4 bước kể chuyện (*Đọc trời ➔ Nghe cơ thể ➔ Xem trong bếp ➔ Chọn món*), nút Hủy.
6. **S06 — Thuận Thiên Món (Kết quả):** Gợi ý 1–2 món ăn bồi bổ, lý do y lý, nguyên liệu tận dụng, nút *"Lưu vào Sổ tay"*, nút *"Xem công thức"*.
7. **S07 — Chi tiết công thức:** Thành phần, định lượng, các bước nấu dưới 30 phút, lưu ý kiêng kỵ.
8. **S08 — Sổ tay Thuận Thiên (Tab 2):** Danh sách món đã lưu, lọc theo triệu chứng, sắp xếp ngày/đánh giá, hỗ trợ Real-time Firestore.
9. **S09 — Chi tiết Sổ tay (Xem/Sửa/Xóa):** Ghi chú cá nhân, chấm điểm sao, nút Xóa kèm Dialog xác nhận và thanh Snackbar Hoàn tác (Undo).
10. **S10 — Lịch sử chẩn vị (Tab 3):** Dòng thời gian ghi nhận các lần chẩn vị (thời tiết, thể trạng, món gợi ý).
11. **S11 — Trung tâm thông báo:** Danh sách thông báo đẩy từ FCM, chạm để điều hướng thông minh vào màn hình đích.
12. **S12 — Hồ sơ & Cài đặt (Tab 4):** Thông tin người dùng, cài đặt dị ứng, cỡ chữ, cờ Remote Config, nút kích hoạt Crashlytics test.
13. **S13 — Xuất báo cáo PDF:** Xem trước dữ liệu tuần, tiến trình tải lên Cloudinary, tạo liên kết mở PDF an toàn.

---

## 6. Quy chuẩn 9 Component bắt buộc & State tương ứng

1. **Button:** Biến thể *Primary* (`filled`), *Secondary* (`outlined`), *Text*, *Danger* (Xóa). Đủ 4 state: *Default, Pressed, Disabled, Loading*.
2. **Text Field:** Viền `outline`, viền focus `primary` 2dp. Đủ 5 state: *Default, Focused, Filled, Error (kèm icon + text lỗi), Disabled*.
3. **Card:** Nền `surfaceContainerLowest/Low`, bo góc 20dp, viền `outlineVariant`. State: *Default, Pressed (InkWell ripple)*.
4. **Navigation Bar:** 4 mục cố định, nhãn luôn hiển thị, thanh chỉ thị trạng thái active dùng `primaryContainer`.
5. **App Bar:** Tiêu đề Noto Serif, vùng nút Back và nút Action (Chuông S11) đạt tối thiểu $48 \times 48\text{ dp}$.
6. **Dialog:** Dùng cho xác nhận thao tác nguy hiểm (Xóa món). Nút xác nhận dùng `error`, nút giữ lại dùng `TextButton`.
7. **Loading State:** 
   * Toàn màn hình: Hoạt cảnh chuỗi bước nồi đất ở S05.
   * Danh sách: Khung xương (Skeleton / Shimmer) 3 dòng tại S08, S10.
8. **Empty State:** Biểu tượng mộc mạc + thông điệp tích cực + 1 nút hành động duy nhất (Ví dụ: *"Sổ tay còn trống — Bắt đầu chẩn vị"*).
9. **Error State:** Thông báo bằng ngôn ngữ đời thường, giải thích nguyên nhân rõ ràng và cung cấp 2 lối thoát: Nút *"Thử lại"* và *"Xem gợi ý ngoại tuyến"*.

---

## 7. Quy tắc Accessibility (A11y) & Ràng buộc cấm

* **Độ tương phản:** Luôn kiểm tra đạt chuẩn WCAG 2.1 AA (Tỷ lệ >= 4.5:1 cho text thường, >= 3:1 cho thành phần đồ họa lớn).
* **Đa kênh thông tin:** Không bao giờ dùng màu sắc đơn độc để biểu thị trạng thái. Vùng đã chọn trên Body Map phải có biểu tượng dấu kiểm và huy hiệu số lượng đi kèm nhãn văn bản.
* **Trợ năng màn hình:** Luôn có nút gạt *"Xem dạng danh sách"* thay thế cho Body Map để tương thích trọn vẹn với trình đọc màn hình TalkBack.
* **Điều cấm kỵ (Strict Don'ts):**
  * Không dùng hiệu ứng chuyển màu (Gradient) sặc sỡ hoặc bóng đổ mờ đục, nặng nề.
  * Không sử dụng phông chữ nhỏ hơn 14sp cho phần văn bản nội dung.
  * Không dùng thuật ngữ chẩn đoán mang tính hù dọa hoặc cam đoan chữa khỏi bệnh.