# CRM Timeline Tracker (Team Progress)

Repository này dùng để **quản lý tiến độ xây dựng hệ thống CRM** của team bằng:

* Web offline: `KPI.html`
* File dữ liệu tiến độ: `data/KPI.csv`
* Git để **chia sẻ tiến độ giữa các thành viên**

Mục tiêu:

* Không cần hệ thống online
* Mỗi người cập nhật tiến độ công việc trên máy cá nhân
* Cuối ngày export CSV và đẩy lên Git
* Mọi người pull về để xem tiến độ toàn team

---

# Cấu trúc repository

```
CRM-Timeline
│
├─ KPI.html
├─ data
│  └─ KPI.csv
│
├─ README.md
└─ .gitignore
```

`data/tasks.csv` là **file dữ liệu chính của toàn team**.

---

# Cách sử dụng

## 1. Cập nhật tiến độ công việc

Mỗi thành viên:

1. Mở file

```
KPI.html
```

2. Cập nhật task:

* đánh dấu Done
* cập nhật Progress %
* cập nhật Status
* thêm ghi chú nếu cần

3. Sau khi cập nhật xong

```
Export CSV
```

4. Lưu file CSV và **thay thế file**

```
data/KPI.csv
```

---

# Quy trình cập nhật mỗi ngày

Trước khi cập nhật:

```
git pull
```

Sau khi export CSV và thay thế `KPI.csv`:

```
git add data/KPI.csv
git commit -m "Daily progress update - YYYY-MM-DD"
git push
```

Ví dụ:

```
git commit -m "Daily progress update - 2026-03-04"
```

---

# Cách xem tiến độ của team

Chỉ cần:

```
git pull
```

Sau đó:

1. Mở `KPI.html`
2. Chọn **Import CSV**
3. Chọn file

```
data/KPI.csv
```

Hệ thống sẽ hiển thị:

* tổng số task
* số task đã hoàn thành
* % tiến độ tổng
* task đang làm / bị block / quá hạn

---

# Quy tắc cập nhật dữ liệu

Khi cập nhật CSV cần đảm bảo:

* Task Done → Progress phải = **100**
* Không sửa cấu trúc cột CSV
* Không xóa ID task
* Không chỉnh tay CSV nếu không cần thiết

---

# Các cột dữ liệu CSV

File `KPI.csv` gồm các cột:

```
id
module
title
start
end
status
progress
notes
updated_at
```

Không thay đổi tên cột.

---

# Nguyên tắc làm việc của team

* Mỗi người **cập nhật tiến độ task mình phụ trách**
* Cuối ngày **phải push CSV mới**
* Trước khi làm việc luôn **git pull**
* Không commit file CSV lỗi

---

# Mục tiêu

Giúp toàn team:

* theo dõi tiến độ CRM
* biết được công việc đã hoàn thành
* biết % tiến độ của dự án
* không cần hệ thống quản lý online


