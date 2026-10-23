# Checkpoint – Chương 1 (Frontend)

## 1. Các bước từ lúc gõ URL đến lúc thấy trang. DNS làm gì?

1. Trình duyệt phân tích URL (giao thức, tên miền, đường dẫn).
2. **DNS** dịch tên miền (vd. `example.com`) thành địa chỉ IP của server. DNS giống "danh bạ điện thoại" của Internet.
3. Trình duyệt mở kết nối TCP tới IP đó (nếu là HTTPS thì có thêm bước bắt tay TLS để mã hóa).
4. Trình duyệt gửi HTTP request (vd. `GET /index.html`).
5. Server xử lý và trả về HTTP response (status code + HTML).
6. Trình duyệt đọc HTML, gặp CSS/JS/ảnh thì gửi thêm request để tải về.
7. Trình duyệt dựng DOM + CSSOM, tính layout, vẽ (render) và hiển thị trang.

## 2. Status code 404 và 500 khác nhau thế nào? Lỗi nào do phía client?

| Mã | Tên | Ý nghĩa | Phía lỗi |
|----|-----|---------|----------|
| 404 | Not Found | Server hoạt động bình thường nhưng không tìm thấy tài nguyên được yêu cầu (sai đường dẫn, trang bị xóa) | **Client** (nhóm 4xx) |
| 500 | Internal Server Error | Server gặp lỗi khi xử lý (code backend lỗi, DB sập...) | **Server** (nhóm 5xx) |

**Đáp án:** 404 là lỗi do phía client.

## 3. Vì sao nên dùng `<main>`, `<nav>` thay vì `<div>`? Kể 2 lợi ích.

Đây là các thẻ ngữ nghĩa (semantic HTML).

1. **Dễ đọc, dễ bảo trì code:** nhìn thẻ là biết vùng đó làm gì (điều hướng, nội dung chính).
2. **Hỗ trợ SEO và khả năng truy cập (accessibility):** công cụ tìm kiếm hiểu cấu trúc trang tốt hơn; trình đọc màn hình cho phép người khiếm thị nhảy nhanh tới `<nav>` hoặc `<main>`.

## 4. Viết một ô nhập MSSV bắt buộc, đúng 10 chữ số, có label

```html
<label for="mssv">Mã số sinh viên</label>
<input
  type="text"
  id="mssv"
  name="mssv"
  required
  pattern="[0-9]{10}"
  maxlength="10"
  inputmode="numeric"
  title="MSSV gồm đúng 10 chữ số"
/>
```

Giải thích:

- `required`: bắt buộc nhập.
- `pattern="[0-9]{10}"`: đúng 10 chữ số.
- `maxlength="10"`: không cho gõ quá 10 ký tự.
- `inputmode="numeric"`: hiện bàn phím số trên điện thoại.
- `for` của `<label>` khớp với `id` của `<input>`: bấm vào label là focus vào ô nhập.

## 5. `git add` và `git commit` khác nhau ở đâu?

- **`git add`**: đưa thay đổi từ thư mục làm việc vào **staging area** (vùng chuẩn bị), tức là chọn những gì sẽ được lưu ở lần commit tới.
- **`git commit`**: **lưu snapshot** những gì đang ở staging area vào lịch sử repository, kèm message mô tả.

Ví dụ:

```bash
git add index.html
git commit -m "Thêm form MSSV"
```

Luồng làm việc: **Working directory → (git add) → Staging area → (git commit) → Repository**
