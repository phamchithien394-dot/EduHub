# EduHub Web — Ch02 (solution)

Bản mẫu chương 2 môn **IN4529 — Lập trình Front End**: 4 trang của Ch01 được tạo kiểu bằng **CSS thuần hiện đại** — design token, mobile-first với 2 breakpoint, Grid/Flexbox, nesting, `:has()`, dark mode.

## Chạy

Không cần cài gì thêm ngoài trình duyệt (Chrome/Edge/Firefox/Safari bản 2024 trở đi).

- Cách 1: mở thư mục bằng VS Code → chuột phải `index.html` → **Open with Live Server**.
- Cách 2: `npx -y http-server . -p 8080` rồi mở <http://localhost:8080>.

Xem dark mode: DevTools → ⋮ → More tools → **Rendering** → *Emulate CSS media feature prefers-color-scheme* → `dark`.

## Kiểm tra

```bash
npx -y html-validate@latest "*.html"     # kỳ vọng: không in lỗi, exit 0
```

Responsive: DevTools → Toggle device toolbar, thử 375 / 768 / 1280 px. Trong Console:
`document.documentElement.scrollWidth <= innerWidth` phải là `true`.

## Cấu trúc

```
solution/
├── index.html, events.html, event-detail.html, register.html
├── css/
│   ├── main.css         # Tệp duy nhất HTML liên kết: @layer + @import
│   ├── tokens.css       # Design token (màu, chữ, khoảng cách, bo góc, đổ bóng, breakpoint) + dark mode
│   ├── base.css         # Reset, kiểu thẻ HTML trần, focus, prefers-reduced-motion
│   ├── layout.css       # Container, header, footer, hero, lưới card, lưới trang chi tiết
│   └── components.css   # Nút, card, badge, FAQ, bảng, hộp thông tin, form (BEM + nesting)
├── assets/              # Ảnh SVG tự vẽ (giống Ch01)
├── challenge-tailwind/  # Bài challenge: trang sự kiện viết bằng Tailwind CSS v4
├── TASKS.md             # Danh sách nhiệm vụ ch2-T1…T7 (cho giảng viên)
└── README.md
```

## Breakpoint

| Tên | Điều kiện | Thay đổi chính |
|---|---|---|
| (mặc định) | điện thoại | 1 cột, menu xuống dòng |
| sm | `@media (width >= 40rem)` — 640 px | header dính đầu trang, form 2 cột |
| lg | `@media (width >= 64rem)` — 1024 px | hero 2 cột, trang chi tiết 2 cột, footer 1 hàng |

Lưới card dùng `repeat(auto-fit, minmax(min(16rem, 100%), 1fr))` nên tự đổi số cột, không cần media query.

## Ghi chú

- Font: `"Be Vietnam Pro"` nếu máy đã cài, không thì font hệ thống — không tải font từ Internet.
- So với Ch01, HTML chỉ thêm class, thẻ `<link>` tới `css/main.css`, vài thẻ bọc (`div`), lưới 8 card trên `events.html` (Ch03 sẽ sinh card này từ API) và nhãn "Sắp hết chỗ"/"Còn … chỗ". Nội dung giữ nguyên.
- `assets/club-tin-hoc.svg` đã sửa ký tự `</>` thành `&lt;/&gt;` (bản Ch01 là XML lỗi nên ảnh không hiện).
