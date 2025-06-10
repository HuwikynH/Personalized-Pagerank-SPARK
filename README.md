### Hướng dẫn cài đặt Apache Spark và PySpark trên Windows

#### BƯỚC 1: Cài Java JDK
- **Tải JDK 11**: Tải bản JDK 11 từ trang chính thức (https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) hoặc dùng OpenJDK.
- **Cài đặt**: Chạy file cài đặt, ghi nhớ đường dẫn thư mục cài đặt (VD: `C:\Program Files\Java\jdk-11`).
- **Cấu hình biến môi trường**:
  - Mở "Advanced System Settings" → "Environment Variables".
  - Tạo biến mới: `JAVA_HOME` = đường dẫn đến thư mục JDK (VD: `C:\Program Files\Java\jdk-11`).
  - Thêm `%JAVA_HOME%\bin` vào biến `Path`.
- **Kiểm tra**: Mở CMD, gõ `java -version` để xác nhận cài đặt thành công.

#### BƯỚC 2: Cài Python 3.10.11 (Tương thích với Spark 3.5.6)
- **Tải Python 3.10.11**: Tải bản cài đặt từ trang chính thức (https://www.python.org/downloads/release/python-31011/) hoặc dùng file `.exe`.
- **Cài đặt**:
  - Chạy file cài đặt, chọn "Add Python to PATH" (quan trọng để sử dụng lệnh `python` trong CMD).
  - Ghi nhớ đường dẫn cài đặt (VD: `C:\Python310`).
  - Chọn "Install Now" và hoàn tất cài đặt.
- **Cấu hình biến môi trường**:
  - Mở "Environment Variables", thêm `C:\Python310` và `C:\Python310\Scripts` vào biến `Path`.
- **Kiểm tra**:
  - Mở CMD, gõ `python --version` để kiểm tra (nên hiển thị Python 3.10.11).
  - Cập nhật pip: Chạy `python -m pip install --upgrade pip` để đảm bảo pip mới nhất.
- **Lưu ý**: Spark 3.5.6 yêu cầu Python 3.6 trở lên, và Python 3.10.11 là phiên bản ổn định, tương thích tốt với PySpark.

#### BƯỚC 3: Cài Apache Spark
- **Tải Spark**: Tải phiên bản Spark 3.5.6 từ trang chính thức (https://spark.apache.org/downloads.html), chọn "Pre-built for Apache Hadoop 3.x".
- **Giải nén**: Giải nén file tải về vào thư mục (VD: `C:\spark`).
- **Cấu hình biến môi trường**:
  - Thêm `C:\spark\bin` vào biến `Path`.

#### BƯỚC 4: Cài Winutils.exe (Bắt buộc cho Windows)
- **Tải winutils**: Tải từ https://github.com/steveloughran/winutils, chọn thư mục tương ứng với Hadoop 3.x (VD: `hadoop-3.2.0`).
- **Giải nén**: Tạo thư mục `C:\hadoop`, sao chép file `winutils.exe` vào `C:\hadoop\bin`.
- **Cấu hình biến môi trường**:
  - Tạo biến mới: `HADOOP_HOME` = `C:\hadoop`.
  - Thêm `C:\hadoop\bin` vào biến `Path`.

#### BƯỚC 5: Cài PySpark tương thích với Spark 3.5.6
- **Cài đặt**: Mở terminal (CMD hoặc Powershell), chạy lệnh:
  ```
  pip install pyspark==3.5.6
  ```
- **Kiểm tra**: Chạy `python -c "import pyspark; print(pyspark.__version__)"` để xác nhận phiên bản 3.5.6.

#### BƯỚC 6: Chạy file Python với Spark
- **File**: Tạo file `personalized_pagerank.py` chứa mã PySpark.
- **Chạy**:
  - Mở CMD, điều hướng đến thư mục chứa file (VD: `cd C:\path\to\your\file`).
  - Chạy lệnh: `spark-submit personalized_pagerank.py`.
- **Lưu ý**: Đảm bảo file `.txt` chứa đồ thị (VD: `graph.txt`) được trỏ đúng trong mã (VD: `input_path = "file:///C:/path/to/graph.txt"`). Đường dẫn phải dùng định dạng URI với `/` thay vì `\`.

---

### Lưu ý quan trọng
- Đảm bảo tất cả biến môi trường (`JAVA_HOME`, `HADOOP_HOME`, `Path`) được cập nhật sau mỗi bước.
- Nếu gặp lỗi, kiểm tra lại đường dẫn hoặc chạy CMD với quyền quản trị.
- Cấu hình `spark.executor.memory` và `spark.driver.memory` là 2GB trong mã là hợp lý, nhưng có thể tăng lên 4GB nếu cần xử lý dữ liệu lớn hơn.
