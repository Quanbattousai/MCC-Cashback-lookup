# Tra cứu MCC hoàn tiền

Webapp tĩnh (1 file `index.html`) tra cứu mã MCC / tên cửa hàng → xem thẻ tín dụng VIB, Techcombank, VPBank nào hoàn tiền và nhóm nào cao nhất.

## Chạy thử tại máy
Mở thẳng `index.html` bằng trình duyệt là xong (không cần server).

## Deploy kiểu GitHub (push là tự cập nhật)

### 1. Tạo repo và push
```bash
cd <thư-mục-chứa-index.html>
git init
git add index.html README.md
git commit -m "init: MCC cashback lookup"
git branch -M main
# tạo repo trên GitHub trước (web hoặc: gh repo create mcc-lookup --public --source=. --push)
git remote add origin https://github.com/<user>/<repo>.git
git push -u origin main
```

### 2a. Nối Vercel
- vercel.com → Add New → Project → Import repo vừa tạo.
- Framework Preset: **Other**. Build command: để trống. Output directory: `./` (gốc).
- Deploy. Từ nay mỗi lần `git push` lên `main` → Vercel tự build lại.

### 2b. Hoặc nối Netlify
- app.netlify.com → Add new site → Import an existing project → chọn repo.
- Build command: để trống. Publish directory: `.` (gốc).
- Deploy. Push là tự deploy.

## Ghi chú
- Phải giữ tên file trang chủ là `index.html`.
- Cửa hàng người dùng tự thêm được lưu bằng `localStorage` (theo trình duyệt + domain), không đồng bộ đa thiết bị.
- Dữ liệu tỷ lệ hoàn tiền: VIB map theo MCC (chính xác); Techcombank & VPBank theo nhóm ngành (tham khảo, "lên tới").
- Muốn gắn domain riêng: Settings → Domains ở Vercel/Netlify, trỏ CNAME.
