# Ch02 — Danh sách nhiệm vụ (tài liệu cho giảng viên)

Dự án: **EduHub Web** · Chương 2 — CSS hiện đại & Responsive.
Mã nhiệm vụ dùng chung cho `de-bai.html`, `rubric.html`, các `/* TODO(ch2-Tk) */` trong `starter/css/` và tệp này.

Tổng điểm bắt buộc: **100**. Challenge là điểm thưởng, cộng tối đa **10**.

Starter đã có sẵn HTML của 4 trang (nội dung Ch01 + class BEM + `<link rel="stylesheet" href="css/main.css">` + lưới card sự kiện ở `events.html`). Sinh viên chỉ viết CSS trong `css/`.

| Mã | Cấp | Điểm gợi ý | Mô tả | Tệp | Tiêu chí đạt |
|---|---|---|---|---|---|
| ch2-T1 | Warm-up | 15 | Design token bằng custom properties: palette gốc, màu theo vai trò (semantic), font, cỡ chữ `clamp()`, khoảng cách, bo góc, đổ bóng, ghi chú breakpoint; dark mode bằng `prefers-color-scheme`. | `css/tokens.css` | Đủ 5 màu palette (`#003F87`, `#00C4CC`, `#001D45`, `#F0F7FF`, `#1A1A2E`); component chỉ đọc màu qua `var(--color-…)`, không viết mã màu trực tiếp; khối `@media (prefers-color-scheme: dark)` chỉ đổi giá trị token; có `color-scheme: light dark`; font là system-ui stack (không tải font ngoài); ≥ 1 cỡ chữ dùng `clamp()`. |
| ch2-T2 | Warm-up | 15 | Tổ chức cascade bằng `@layer` + `@import`; base: `box-sizing`, reset margin bằng `:where()`, kiểu chữ body, ảnh không tràn, vòng focus, `prefers-reduced-motion`. | `css/main.css`, `css/base.css` | `main.css` khai báo `@layer tokens, base, layout, components;` rồi `@import … layer(…)` 4 tệp; HTML chỉ liên kết `main.css`; `img { max-inline-size: 100% }`; `:focus-visible` có outline ≥ 2px nhìn rõ trên cả nền sáng và tối; bật "Giảm chuyển động" (DevTools → Rendering) thì animation/transition tắt. |
| ch2-T3 | Applied | 20 | Khung trang mobile-first: `.container`, header + menu bằng Flexbox, footer, hero 1 → 2 cột, nút `.btn`, skip link hiện khi Tab. | `css/layout.css`, `css/components.css` | Ở 375 px menu xuống dòng, không tràn ngang; ở ≥ 640 px header dính đầu trang (`position: sticky`); hero 2 cột ở ≥ 1024 px; link trang hiện tại nổi bật nhờ selector `[aria-current="page"]`; nút và link menu cao ≥ 44 px. Media query viết kiểu mobile-first (`width >= …`), đúng 2 mốc 40rem và 64rem. |
| ch2-T4 | Applied | 20 | Lưới card sự kiện và CLB bằng Grid `repeat(auto-fit, minmax(…, 1fr))`; card BEM dùng nesting gốc; `:has()` làm nổi card có badge "Sắp hết chỗ"; FAQ `<details>` có biểu tượng xoay. | `css/layout.css`, `css/components.css` | `.card-grid` không dùng media query mà vẫn 1 cột ở 375 px, 2 cột ở 768 px, 3–4 cột ở 1280 px; ảnh card `aspect-ratio: 16/9` + `object-fit: cover`; các card cùng hàng cao bằng nhau, dòng "Còn … chỗ" nằm đáy card; card có `.badge--hot` đổi viền **chỉ nhờ** `.card:has(.badge--hot)` (không thêm class mới vào HTML); hover có `transition`. |
| ch2-T5 | Applied | 15 | Trang chi tiết dàn bằng `grid-template-areas` (1 cột → 2 cột, hộp thông tin dính bên phải); `<dl>` 2 cột; bảng lịch cuộn ngang trong khung riêng. | `css/layout.css`, `css/components.css` | Ở ≥ 1024 px `event-detail.html` có cột phải "Thông tin chung" `position: sticky`; `grid-area` chỉ gán trong media query; ở 375 px bảng trong `events.html` cuộn trong `.table-wrap`, trang **không** có thanh cuộn ngang. |
| ch2-T6 | Applied | 15 | Form đăng ký: ô nhập full width, 2 cột từ 640 px, nhóm radio dạng viên thuốc tô nền bằng `:has(input:checked)`, báo lỗi bằng `:user-invalid`, focus rõ. | `css/components.css` | `fieldset` không làm tràn ngang (`min-inline-size: 0`); gõ MSSV 9 số rồi rời ô → viền đỏ, mở trang lần đầu thì chưa đỏ; chọn "Năm 3" → viên "Năm 3" đổi nền; dùng được bằng bàn phím. |
| ch2-T7 | Challenge | ≤ 10 | Viết lại trang lịch sự kiện bằng Tailwind CSS v4 (CLI), token đưa vào `@theme`. | `challenge-tailwind/` | `npm install && npm run build` sinh `tailwind.css`; không có `tailwind.config.js`; `@theme` chứa màu/font/breakpoint lấy từ `tokens.css`; dùng `dark:`, `sm:`/`lg:` và `has-[…]:`; trang không cuộn ngang ở 375 px; không nộp `node_modules`. |

## Ghi chú chấm

- Kiểm chứng chung cho mọi bài: `npx -y html-validate@latest "*.html"` → 0 lỗi; DevTools chế độ thiết bị ở 375 / 768 / 1280 px không có thanh cuộn ngang (`document.documentElement.scrollWidth <= innerWidth` trong Console); chuyển Rendering → `prefers-color-scheme: dark` thấy giao diện tối dễ đọc.
- Không dùng float để dàn trang, không dùng `!important` (trừ khối `prefers-reduced-motion`), không dùng ID selector để tạo kiểu → trừ điểm ở nhiệm vụ tương ứng.
- Màu viết thẳng (`#003f87`) trong `components.css` thay vì `var(--color-…)` → trừ ở ch2-T1.
- `tokens.css` là nguồn token cho Ch04: tên `--color-*`, `--font-*`, `--radius-*`, `--shadow-*`, `--breakpoint-*` trùng namespace `@theme` của Tailwind v4.
- Bản CSS thuần dùng nesting gốc, `:has()`, `:user-invalid`, cú pháp media range (`width >= 40rem`) — cần Chrome/Edge/Firefox/Safari bản 2024 trở đi.
