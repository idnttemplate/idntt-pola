# idntt pola tracker – hướng dẫn từ A đến Z (GitHub Pages, miễn phí, không cần thẻ/PayPal)

Cấu trúc thư mục:
- `index.html` – toàn bộ trang web
- `data/items.json` – danh sách pola (ban đầu rỗng, web tự cập nhật)
- `img/` và `th/` – ảnh lớn và ảnh nhỏ (tự được tạo khi bạn upload)
- `.nojekyll` – file trống, giúp GitHub Pages phục vụ đúng (không được xóa)

## A. Tạo tài khoản GitHub
1. Vào https://github.com/signup và đăng ký (miễn phí).
2. Tên người dùng (username) sẽ nằm trong địa chỉ web: `https://USERNAME.github.io/...` nên hãy chọn tên bạn thích.

## B. Tạo repository (kho chứa)
1. Bấm dấu `+` góc trên bên phải → **New repository**.
2. Repository name: ví dụ `idntt-pola` (sẽ là phần cuối của địa chỉ web).
3. Chọn **Public** (gói free của GitHub Pages cần repo công khai).
4. **Không** tick "Add a README file". Bấm **Create repository**.

## C. Đưa file lên
1. Giải nén file zip trên máy.
2. Ở trang repo vừa tạo, bấm liên kết **uploading an existing file**.
3. Mở thư mục đã giải nén, chọn **tất cả** (gồm `index.html`, thư mục `data`, `.nojekyll`, `README.md`) rồi kéo thả vào trang GitHub.
   - Nếu không thấy `.nojekyll`, bật "Hidden items" trong File Explorer.
   - Nếu thư mục `data` không kéo thả được, bấm "Add file → Create new file", gõ `data/items.json`, nội dung là `[]`.
4. Kéo xuống bấm **Commit changes**.

## D. Bật GitHub Pages
1. Vào repo → **Settings** → **Pages** (cột bên trái).
2. Mục Build and deployment → Source: **Deploy from a branch**.
3. Branch: chọn **main** và thư mục **/ (root)** → **Save**.
4. Đợi 1–3 phút, tải lại trang Settings → Pages sẽ hiện địa chỉ: `https://USERNAME.github.io/idntt-pola/`.
5. Mở địa chỉ đó để kiểm tra: web hiện ra, chưa có ảnh nào là đúng.

## E. Tạo token để bạn (admin) được thêm/xóa ảnh
Token là "chìa khóa" cho phép web ghi vào repo của bạn. Chỉ bạn giữ nó.
1. Bấm ảnh đại diện góc trên bên phải GitHub → **Settings** → kéo xuống cuối cột trái → **Developer settings**.
2. **Personal access tokens** → **Fine-grained tokens** → **Generate new token**.
3. Điền:
   - Token name: `pola-admin`
   - Expiration: chọn thời hạn (ví dụ 1 năm). Hết hạn thì tạo token mới.
   - Repository access: **Only select repositories** → chọn repo `idntt-pola`.
   - Permissions → **Repository permissions** → **Contents: Read and write**. Các quyền khác để mặc định.
4. Bấm **Generate token** và **sao chép token ngay** (chỉ hiện một lần, bắt đầu bằng `github_pat_`). Lưu vào nơi an toàn.

## F. Sử dụng
1. Mở web → bấm **Sign in** → dán token → Sign in.
2. Bấm **＋ Add image**: chọn nhiều ảnh cùng lúc (tối đa 100 ảnh mỗi lần lưu), chọn shop / member / era / round / date (áp dụng chung cho cả lô), rồi **Save**. Ảnh được nén sẵn trên trình duyệt rồi đẩy lên GitHub bằng một lần commit.
3. Nút ✎ sửa thông tin từng ảnh, 🗑 xóa ảnh.
4. Sau khi lưu, người xem sẽ thấy thay đổi sau khoảng 1–2 phút (GitHub Pages cần build lại). Riêng bạn khi đang đăng nhập thì thấy ngay.
5. Dùng máy chung thì bấm **Sign out** sau khi xong (token được lưu trong trình duyệt khi đăng nhập).

## G. Tùy chỉnh
Mở `index.html` bằng Notepad (hoặc sửa ngay trên GitHub: bấm file → biểu tượng bút chì), tìm đầu phần `<script>`:
- `NAMES`: tên member (thứ tự id1 → id24, id3/id22–24 còn trống)
- `SHOPS`: danh sách shop có sẵn (tùy chọn)
- `ROUNDS`: 21 mục round (1.0 … 17.0, POB, Luckydraw, Album Inclusion, etc.)
- `ERAS`: 3 era
- `CFG`: chỉ cần điền `owner` và `repo` nếu sau này dùng tên miền riêng; còn dùng `github.io` thì tự nhận.

## H. Giới hạn miễn phí (theo tài liệu GitHub Pages)
- Repo nên dưới 1 GB, trang đã đăng tối đa 1 GB. Ảnh sau khi nén (~100–400 KB ảnh lớn + ~20–40 KB ảnh nhỏ) cho 2000 pola khoảng 0,3–1 GB, nên hãy theo dõi dung lượng nếu số ảnh tăng nhiều.
- Băng thông mềm 100 GB/tháng, mỗi giờ tối đa khoảng 10 lần build (mỗi lần Save là một lần build).
- Nếu gần chạm 1 GB, nên chuyển sang Cloudflare Pages (kết nối cùng repo này) hoặc chia ảnh sang repo khác.

## I. Hủy web
Xóa repo: Settings → kéo xuống cuối → **Delete this repository**. Không có thẻ hay PayPal nào liên kết nên không cần gỡ gì thêm. Nhớ xóa luôn token ở Developer settings.
