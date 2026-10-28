# Ghi chú cho Claude

- Trả lời người dùng bằng tiếng Việt.
- Đây là trang CV một tệp (`index.html`). Token ở khối `:root` đầu tệp (nền tối, nhấn cam `--acc`, xanh chanh `--live`); giữ bộ nhận diện này.
- Trang CV là trang giới thiệu nên được có phần mở đầu lớn; các quy tắc "màn hình ứng dụng" bên dưới chỉ áp dụng cho phần dạng bảng/danh sách. Số liệu (năm kinh nghiệm, số trạm, số nhà máy) là của người dùng: giữ nguyên, không thêm số mới.

## Quy tắc thiết kế (luôn áp dụng khi làm giao diện)

Rút từ các repo người dùng gắn sao: hallmark, taste-skill, emilkowalski/skills, design.md. Áp dụng tự động cho mọi thay đổi giao diện trong repo này, cho đến khi người dùng yêu cầu đổi. Màu, font, cỡ chữ lấy từ token sẵn có của dự án (`:root`/theme), không tự đổi bộ nhận diện.

**Sàn chất lượng**
- Token màu chỉ khai báo ở `:root` (và khối dark mode); component dùng `var(--…)`, không mã màu thô.
- `:focus-visible` nhìn thấy trên mọi phần tử tương tác; tương phản chữ ≥ 4.5:1; vùng bấm ≥ 44px trên điện thoại.
- Không cuộn ngang ở 375px; dùng `overflow-x: clip` khi cần cắt. Kiểm tra cả 375px và 1280px.
- Có `prefers-reduced-motion`; hiệu ứng mới không được né.
- Không bịa số liệu, không lorem ipsum. Số 0 là 0, thiếu dữ liệu là "—" xám.

**Màn hình ứng dụng / công cụ**
- Không hero; tiêu đề danh từ + một dòng mô tả, nút chính cùng hàng.
- Một màu nhấn, chỉ cho hành động chính và mục đang chọn; màu nằm trên dữ liệu, không tô khung.
- Bảng trước thẻ: kẻ ngang mảnh, tiêu đề cột nhỏ xám kiểu câu, số căn phải `tabular-nums`, không sọc ngựa vằn.
- Số liệu tóm tắt là chữ, không ô biểu tượng; không sparkline trang trí.
- Mặt phẳng: viền HOẶC bậc tông, không chồng bóng + viền; bóng chỉ cho vật nổi (menu, hộp thoại, toast).
- Đủ 4 trạng thái: đang tải, trống (một câu + một hành động), lỗi (nói rõ cách sửa), đầy đủ. Xóa phải hỏi lại hoặc có hoàn tác.
- Nhãn trạng thái: nền nhạt + chữ đậm, có chữ đi kèm.
- Trạng thái quan trọng nằm trên URL hash để Back/tải lại giữ đúng chỗ.

**Chuyển động**
- Thao tác lặp nhiều lần (chuyển tab, phím tắt, lọc) không hiệu ứng. Chỉ animate `transform`, `opacity`, màu. Không bao giờ `transition: all`.
- Vào/ra dùng ease-out (`cubic-bezier(0.23, 1, 0.32, 1)`), không ease-in. Giao diện dưới 300ms: nhấn 100–160ms, popover 125–200ms, hộp thoại 200–300ms.
- Không xuất hiện từ `scale(0)` (bắt đầu 0.95–0.97 + opacity 0). Hover chuyển động chỉ trong `@media (hover: hover) and (pointer: fine)`.

**Không làm (dấu hiệu "AI làm")**
- Gradient tím–xanh, glow, kính mờ, màu tím/chàm làm nhấn, biểu đồ cầu vồng.
- Nhãn eyebrow in hoa giãn cách trên tiêu đề, nhãn mono nhỏ, đánh số 01/02/03 trang trí, chữ nghiêng một từ trong tiêu đề (trừ khi đã là dấu ấn có sẵn của dự án).
- Bento grid, thẻ lồng thẻ, một bán kính 12–16px cho mọi thứ, chín cỡ chữ gần bằng nhau.
- Dòng meta nối bằng dấu chấm giữa "·", chấm trạng thái phát sáng, emoji làm biểu tượng.
- Fade-up mọi thứ khi cuộn, thẻ nhấc lên khi rê chuột, nảy trên giao diện làm việc.
- Chữ chung chung: "liền mạch", "mạnh mẽ", "Bắt đầu ngay". Dùng động từ cụ thể của việc đó.
- Bỏ bớt trang trí chưa đủ: thay bằng nội dung thật, chi tiết riêng của chủ đề.
