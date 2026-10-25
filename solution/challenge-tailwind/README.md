# Challenge Ch02 — Trang sự kiện bằng Tailwind CSS v4

Trang `events.html` của bản CSS thuần, viết lại bằng **Tailwind CSS v4.3** qua CLI. Mục đích: so sánh cách "viết CSS riêng" với cách "utility-first".

## Chạy

Cần Node.js ≥ 22.

```bash
npm install          # cài tailwindcss + @tailwindcss/cli
npm run build        # src/input.css → tailwind.css (đã nén)
npm run dev          # tự build lại mỗi khi sửa events.html
```

Mở `events.html` bằng Live Server (ảnh và link dùng `../` trỏ về thư mục solution).

## Điểm cần chú ý

- Tailwind v4 **không còn** `tailwind.config.js`. Cấu hình nằm trong CSS: `@import "tailwindcss";` + `@theme { … }`.
- `@theme` chép token từ `../css/tokens.css`: `--color-primary` sinh ra `bg-primary`, `text-primary`…; `--breakpoint-sm/lg` đặt lại mốc `sm:`/`lg:` thành 640 px / 1024 px.
- `source(none)` + `@source "../events.html"`: chỉ quét đúng tệp HTML này để sinh class.
- Dark mode: tiền tố `dark:` (mặc định theo `prefers-color-scheme`).
- `:has()` trong Tailwind: `has-[[data-hot]]:border-warning` — card nào chứa phần tử có `data-hot` thì đổi viền.
- `tailwind.css` là tệp sinh ra, giữ lại để mở trang không cần build; không nộp `node_modules/`.

## Cấu trúc

```
challenge-tailwind/
├── package.json, package-lock.json
├── src/input.css     # @import "tailwindcss" + @theme
├── events.html       # Trang viết bằng class tiện ích
└── tailwind.css      # Kết quả build
```
