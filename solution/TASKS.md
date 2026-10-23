# Ch01 — Danh sách nhiệm vụ (tài liệu cho giảng viên)

Dự án: **EduHub Web** · Chương 1 — Web hoạt động thế nào & HTML.
Mã nhiệm vụ dùng chung cho `de-bai.html`, `rubric.html`, các `<!-- TODO(ch1-Tk) -->` trong `starter/` và tệp này.

Tổng điểm bắt buộc: **100**. Challenge là điểm thưởng, cộng tối đa **10**.

| Mã | Cấp | Điểm gợi ý | Mô tả | Tệp | Tiêu chí đạt |
|---|---|---|---|---|---|
| ch1-T1 | Warm-up | 20 | Trang chủ dựng bằng thẻ semantic: `header` (logo + `nav` 4 liên kết), `main`, `section` sự kiện sắp tới (3 `article`), danh sách 6 CLB, FAQ bằng `<details>`/`<summary>`, `footer`. | `index.html`, `assets/` | Có `<!DOCTYPE html>`, `lang="vi"`, `meta charset` + `viewport`; đúng **một** `h1`, heading không nhảy cấp (h1 → h2 → h3); mọi `img` có `alt` có nghĩa, ảnh dưới màn hình đầu có `loading="lazy"`, có `width`/`height`; ≥ 3 `<details>`; đủ 6 CLB (Tin học, Tình nguyện, Tiếng Anh, Âm nhạc, Bóng đá, Kỹ năng mềm). |
| ch1-T2 | Applied | 20 | Trang lịch sự kiện dạng bảng 8 sự kiện (thời gian, tên, CLB, địa điểm, số chỗ). | `events.html` | Bảng có `caption`, `thead`/`tbody`/`tfoot`; tiêu đề cột `th scope="col"`, tên sự kiện `th scope="row"`; thời gian bọc `<time datetime="…">` đúng định dạng ISO; ít nhất 1 sự kiện liên kết sang `event-detail.html`. |
| ch1-T3 | Applied | 15 | Trang chi tiết một sự kiện (Workshop HTML của CLB Tin học). | `event-detail.html` | Nội dung trong `<article>` có `header`/`footer` riêng; thông tin chung dùng `<dl>`; có `<ol>` (nội dung) và `<ul>` (cần chuẩn bị); ảnh có `alt`; có liên kết quay lại `events.html` và sang `register.html`. |
| ch1-T4 | Applied | 25 | Form đăng ký thành viên dùng validation gốc của HTML. | `register.html` | Mọi ô có `<label for>` khớp `id`; nhóm bằng `<fieldset>` + `<legend>`; MSSV `required` + `pattern="[0-9]{10}"`; email `type="email" required`; mật khẩu `type="password" minlength="8"`; có `select` 6 CLB, nhóm `radio` năm học, `textarea`, `checkbox` đồng ý bắt buộc; nút `type="submit"`. Gõ MSSV 9 số hoặc email sai → trình duyệt chặn gửi. |
| ch1-T5 | Applied | 20 | Meta/SEO + xuất bản: `title` riêng từng trang, `meta description`, Open Graph (`og:title`, `og:description`, `og:image`, `og:url`), favicon; nav có `aria-current="page"`; repo GitHub + GitHub Pages. | 4 tệp `.html`, `README.md` | `npx -y html-validate@latest "*.html"` → 0 lỗi; mọi liên kết nội bộ mở được; link GitHub Pages chạy và ghi trong `README.md`; ≥ 3 commit có message rõ nghĩa. |
| ch1-T6 | Challenge | ≤ 10 | Accessibility nâng cao: liên kết "Bỏ qua, đến nội dung chính" ở đầu mọi trang, `aria-labelledby` cho các `section`, chạy Lighthouse. | 4 tệp `.html`, `README.md` | Lighthouse (Chrome DevTools, chế độ Mobile) trên bản GitHub Pages: Accessibility ≥ 95 và SEO ≥ 95; ảnh chụp kết quả đưa vào `README.md`; dùng được cả trang chỉ bằng phím Tab. |

## Ghi chú chấm

- Ch01 **không có CSS** — trang trông "thô" là đúng. Không trừ điểm giao diện. CSS thêm ở Ch02 (starter Ch02 = solution này).
- Không dùng thẻ trình bày cũ (`<font>`, `<center>`, `<b>` để làm tiêu đề, bảng để dàn trang) → trừ điểm ở nhiệm vụ tương ứng.
- 6 CLB trùng seed của mock API (`02_Projects/mock-api/db.json`); danh sách sự kiện ở Ch01–02 là dữ liệu tĩnh minh hoạ — từ Ch03 trang lấy sự kiện thật từ API.
- Open Graph cần URL tuyệt đối: sinh viên thay `ten-tai-khoan` bằng tài khoản GitHub của mình; kiểm tra bằng cách dán link vào Zalo/Facebook Messenger.
