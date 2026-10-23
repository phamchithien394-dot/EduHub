# EduHub Web — Ch01 (solution)

Bản mẫu chương 1 môn **IN4529 — Lập trình Front End**: 4 trang HTML tĩnh, chưa có CSS (CSS thêm ở Ch02).

## Chạy

Không cần cài gì thêm ngoài trình duyệt.

- Cách 1: mở thư mục bằng VS Code → chuột phải `index.html` → **Open with Live Server**.
- Cách 2: `npx -y http-server . -p 8080` rồi mở <http://localhost:8080>.

## Kiểm tra

```bash
# Cần Node.js 24 LTS (html-validate mới yêu cầu Node >= 22.22)
npx -y html-validate@latest "*.html"     # kỳ vọng: không in lỗi, exit 0
```

## Cấu trúc

```
solution/
├── index.html          # Trang chủ: giới thiệu, 3 sự kiện sắp tới, 6 CLB, FAQ (<details>)
├── events.html         # Lịch sự kiện dạng bảng
├── event-detail.html   # Chi tiết một sự kiện
├── register.html       # Form đăng ký thành viên (validation gốc HTML)
├── assets/             # Ảnh SVG tự vẽ + og-image.png (1200×630) cho Open Graph
│   └── og-cover.svg    # Bản gốc để vẽ lại og-image.png
├── TASKS.md            # Danh sách nhiệm vụ ch1-T1…T6 (cho giảng viên)
└── README.md
```

## Ghi chú

- Thẻ `og:url`/`og:image` dùng `https://ten-tai-khoan.github.io/eduhub-web/` — thay bằng địa chỉ GitHub Pages thật.
- Form gửi bằng `method="get"` về chính trang để thấy dữ liệu trên thanh địa chỉ; Ch03 chuyển sang gọi API `POST /api/auth/register`.
