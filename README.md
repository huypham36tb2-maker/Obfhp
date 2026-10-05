# Huy Pham Obf Studio

Obfuscate (làm rối) code **Python, Lua, JavaScript, HTML** ngay trên trình duyệt — không cần server, không upload code lên đâu cả, tất cả xử lý offline.

> **Owner:** Huy Pham
> **UI:** Dark Neon • Offline • 4 ngôn ngữ

---

## ✨ Tính năng

| Ngôn ngữ | Đầu ra | Giải mã bằng |
|---|---|---|
| 🐍 Python | Stub base64 + zlib deflate (nhiều lớp) | `exec()` sau khi decompress |
| 🌙 Lua | Stub base64 + inflate thuần Lua | `load()` sau khi decompress |
| 🟨 JavaScript | Stub base64 + DecompressionStream | `new Function(code)` |
| 🌐 HTML | Trang HTML chứa payload base64 | `document.write()` sau giải mã |

- **4 preset**: Balanced (3 lớp), Compact (1 lớp), Deep Wrap (8 lớp), Unicode (5 lớp)
- **Khoá Python**: chỉ chạy trên phiên bản Python mong muốn (3.8 → 3.13)
- **Đóng dấu tác giả**: nhúng tên bạn vào file output
- **Tải file / sao chép / xoá** ngay trong giao diện
- **Tự đoán ngôn ngữ** khi nạp file theo đuôi `.py`, `.lua`, `.js`, `.html`

---

## 🚀 Cách dùng

1. Mở file `huypham_obf.html` bằng trình duyệt (Chrome, Edge, Cốc Cốc, Firefox...).
2. Chọn **ngôn ngữ** tương ứng ở hàng nút (Python / Lua / JS / HTML).
3. Dán code vào ô **CODE CẦN OBF** (hoặc bấm **Nạp file** để chọn file từ máy).
4. Chọn **Preset** và chỉnh **Số lớp bọc** nếu muốn.
5. (Tuỳ chọn) Nhập **Đóng dấu tác giả** — sẽ xuất hiện trong file output.
6. Bấm **🔐 OBFUSCATE NGAY**.
7. Kết quả hiện bên dưới → **Sao chép** hoặc **Tải file** về máy.

---

## 📁 File output

- Python: `HuyPham_Obf.py`
- Lua: `HuyPham_Obf.lua`
- JavaScript: `HuyPham_Obf.js`
- HTML: `HuyPham_Obf.html`

Chạy file output bằng trình thông dịch / trình duyệt tương ứng là code gốc được thực thi.

---

## ⚠️ Lưu ý quan trọng

- **Obfuscate ≠ bảo mật tuyệt đối.** Đây là lớp che mắt, làm khó đọc code, KHÔNG mã hoĩá an toaàn.
- là Với ** toPython / Lua**: nếu môi trường chạy không có `zlib` (Python) hoặc `inflate` (Lua), hãy chọn preset **Compact** (1 lớp, chỉ base64) để chắc chắn chạy được. Trình duyệt hiện đại đều có `CompressionStream` nên output thường dùng deflate.
- Với **JavaScript**: output ưu tiên `DecompressionStream` (Chrome/Edge/Firefox mới). Nếu chạy Node.js cũ, output có fallback dùng `require('zlib')`.
- Với **HTML**: output dùng `document.write()` để render trang gốc — nghàn bộ nội dung HTML gốc sẽ được "viết lại" khi tải.
- **Không nên** obfuscate code chứa secrets, token, API key... vì về bản chất vẫn giải mã được.

---

## 🧪 Test nhanh

**Python:**
```python
print("Hello Huy Pham")
