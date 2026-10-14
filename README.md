# Tìm từ khóa trong file 
**1. Mục đích: Đọc nội dung file `audit_login.log` xong lọc các dòng có `ERROR` và đếm kết quả *(qua đường ống Pipeline | )***

**2. Phân tích**
  - HĐH PowerShell
  - Get-ChildItem `-Recurse *.log `liệt kê tất cả các file có đuôi `.log`
  - Đọc nội dung trong file: `Get-Content`
  - Lọc từ khóa: select-string `ERROR`
  - Đếm kết quả: Measure-Object `-Line`

**3. Cách giải**
>`
(Get-ChildItem -Recurse *.log | Get-Content | select-string “TIMEOUT” |  Where-Object { $_ -notmatch " NOT TIMEOUT"}).Count`

**4. Bảng so sánh**
| Power Shell | Git Bash | Dùng để |
| :---: | :---: | :---: |
| Get-ChildItem -Recurse *.log | find . -name "*.log" | dùng để tìm tất cả file .log |
| Get-Content | cat file.log | dùng để xem nội dung của file |
| select-string "..." | grep "..." file.log | dùng để tìm dòng chứa từ khóa trong file |
| Where-Object | cat file.log / grep "error" | dùng để chỉ giữ lại những dòng thỏa điều kiện |
