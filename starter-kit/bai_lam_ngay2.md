# BÀI LÀM – ÔN TẬP NGÀY 2

- **Họ tên:**Lê Quang Hào
- **Lớp:**CNTT1
- **Link repository:**https://github.com/lequanghao2609-alt/CNTT1_Nhap-mon-CNTT_OnTap-Ngay2/upload
- **Hệ điều hành (Windows/macOS):** Windows

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```shell
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

PS C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh> get-location

Path
----
C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh


PS C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh> get-childitem


    Directory: C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        10/21/2026   3:15 PM                archive
d-----        10/21/2026   3:15 PM                data
d-----        10/21/2026   3:15 PM                docs
d-----        10/21/2026   3:15 PM                logs
d-----        10/21/2026   3:15 PM                media
-a----        10/21/2026   3:15 PM             83 .env
-a----        10/21/2026   3:15 PM           1402 bai_lam_ngay2.md


PS C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh> get-content logs\access.log | select-string "ERROR"

2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)


PS C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh>
PS C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh> get-content logs\access.log | select-string "ERROR" | set-content logs\error_report.txt
PS C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh> get-content logs\error_report.txt
2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)
PS C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh>


```

### 2 dòng lỗi đầu tiên trong error_report.txt

```text
2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)

```

## Bài 2. Đếm bằng pipeline

### Lệnh

```shell
PS C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh> (get-content logs\access.log | select-string "warning").count
4
PS C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh> (get-content logs\payment.log | select-string "error").count
3

```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
WARNING trong access.log:4
ERROR trong payment.log:3
```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
.\auto_warning.ps1

```

### Nội dung file logs/warning_report.txt

```text
=== CANH BAO THANH TOAN ===

2025-10-18 09:19:13 [WARNING] Cong thanh toan phan hoi cham
2025-10-18 09:28:16 [WARNING] Nhieu lan nhap sai ma OTP
2025-10-18 09:43:01 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:46:22 [WARNING] So du vi gan bang hoc phi
2025-10-18 09:49:43 [WARNING] So du vi gan bang hoc phi

```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell

PS C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh> "=== TONG HOP ACCESS LOG ===" > logs/tong_hop_ngay2.txt
PS C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh> Get-Content logs/access.log | Select-String "ERROR" >> logs/tong_hop_ngay2.txt
PS C:\Users\lequanghao\Downloads\starter-kit\starter-kit\trung-tam-tieng-anh> (Get-Content logs/payment.log | Select-String "WARNING").Count >> logs/tong_hop_ngay2.txt


```

### Nội dung file logs/tong_hop_ngay2.txt

```text
=== TONG HOP ACCESS LOG ===

2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:33:51 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:37:19 [ERROR] Ket noi may chu du lieu that bai
2025-10-18 08:49:43 [ERROR] Het thoi gian cho (timeout)
2025-10-18 08:53:11 [ERROR] Het thoi gian cho (timeout)


5

```

## Bài 5. Câu hỏi ngắn

- **a)>: Ghi nội dung vào file, xóa nội dung cũ nếu file đã tồn tại.   CÒN   >>: Ghi nối thêm nội dung vào cuối file, giữ nguyên nội dung cũ.
**
- **b)File tong_hop_ngay2.txt sẽ bị ghi đè, nội dung tổng hợp trước đó bị mất và chỉ còn các dòng ERROR được ghi bởi lệnh thứ hai.**
- **c)Vì đường dẫn tương đối giúp script chạy được trên nhiều máy khác nhau khi cấu trúc thư mục dự án được giữ nguyên, không phụ thuộc vào tên người dùng hay vị trí cụ thể trên máy.**

## Tự chấm (điền sau khi có đáp án)

- **Điểm tự chấm:** ..../100
- **Lỗi mình đã mắc và cách sửa:**
