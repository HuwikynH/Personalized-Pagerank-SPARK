# Personalized-Pagerank-SPARK
Hướng dẫn cài đặt Apache Spark và PySpark trên Windows (ngắn gọn)

BƯỚC 1: Cài Java JDK
- Tải JDK 11
- Cài xong, đặt biến môi trường:
    JAVA_HOME = đường dẫn đến thư mục JDK
    Thêm %JAVA_HOME%\bin vào biến Path

BƯỚC 2: Cài Apache Spark
- Tải Spark
    Chọn phiên bản: Spark (Khuyên dùng bản 3.5.6) → Pre-built for Apache Hadoop 3
- Giải nén ra thư mục (VD: C:\spark)

BƯỚC 3: Cài Winutils.exe (bắt buộc cho Windows)
- Tải winutils tại: https://github.com/steveloughran/winutils
- Giải nén vào C:\hadoop\bin
- Đặt biến môi trường:
    HADOOP_HOME = C:\hadoop
    Thêm C:\hadoop\bin vào Path

BƯỚC 4: Cài PySpark tương thích cho bản spark 3.5.
- Mở terminal (CMD/Powershell), chạy:
    pip install pyspark==3.5.6

BƯỚC 5: Chạy file Python với Spark
- file: personalized_pagerank.py
- Chạy bằng lệnh:
    spark-submit personalized_pagerank.py

***Lưu ý: phải trỏ đến file .txt chứa đồ thị 
