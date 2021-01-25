# Tìm hiểu Spark
Spark cho phép xây dựng các mô hình dự đoán nhanh chóng với việc tính toán được thực hiện trên một nhóm các máy tính, có có thể tính toán cùng lúc trên toàn bộ tập dữ liệu mà không cần phải trích xuất mẫu tính toán thử nghiệm. Tốc độ xử lý của Spark có được do việc tính toán được thực hiện cùng lúc trên nhiều máy khác nhau. Đồng thời việc tính toán được thực hiện ở bộ nhớ trong (in-memories) hay thực hiện hoàn toàn trên RAM.
Thành phần trung của Spark là Spark Core: cung cấp những chức năng cơ bản nhất của Spark như lập lịch cho các tác vụ, quản lý bộ nhớ, fault recovery, tương tác với các hệ thống lưu trữ… Đặc biệt, Spark Core cung cấp API để định nghĩa RDD (Resilient Distributed DataSet) là tập hợp của các item được phân tán trên các node của cluster và có thể được xử lý song song.

<https://images.viblo.asia/full/2ba27584-446d-49d8-b9bb-fe876ecb60d5.png/>

Spark có thể chạy trên nhiều loại Cluster Managers như Hadoop YARN, Apache Mesos hoặc trên chính cluster manager được cung cấp bởi Spark được gọi là Standalone Scheduler.
 - Spark SQL cho phép truy vấn dữ liệu cấu trúc qua các câu lệnh SQL. Spark SQL có thể thao tác với nhiều nguồn dữ liệu như Hive tables, Parquet, và JSON.
 - Spark Streaming cung cấp API để dễ dàng xử lý dữ liệu stream.
 - MLlib Cung cấp rất nhiều thuật toán của học máy như: classification, regression, clustering, collaborative filtering …
 - GraphX là thư viện để xử lý đồ thị.

Những tính năng nổi bật:
 - “Spark as a Service”: Giao diện REST để quản lí (submit, start, stop, xem trạng thái) spark job, spark context.
 - Tăng tốc, giảm độ trễ thực thi job xuống mức chỉ tính bằng giây bằng cách tạo sẵn spark context cho các job dùng chung.
 - Stop job đang chạy bằng cách stop spark context.
 - Bỏ bước upload gói jar lúc start job làm cho job được start nhanh hơn.
 - Cung cấp hai cơ chế chạy job đồng bộ và bất đồng bộ.
 - Cho phép cache RDD theo tên , tăng tính chia sẻ và sử dụng lại RDD giữa các job.
 - Hỗ trợ viết spark job bằng cú pháp SQL.
 - Dễ dàng tích hợp với các công cụ báo cáo như: Business Intelligence, Analytics, Data Integration Tools.

# Tìm hiểu về mapreduce
Mapreduce là một mô hình lập trình, thực hiện quá trình xử lý tập dữ liệu lớn. Mapreduce gồm 2 pha : map và reduce.
 - Hàm Map : Các xử lý một cặp (key, value) để sinh ra một cặp (keyI, valueI) - key và value trung gian. Dữ liệu này input vào hàm Reduce.
 - Hàm Reduce : Tiếp nhận các (keyI, valueI) và trộn các cặp (keyI, valueI) trung gian , lấy ra các valueI có cùng keyI.

Hoạt động :
 - Ý tưởng:
   Chia vấn đề cần xử lý thành các phần nhỏ để xử lý.
   Xử lý các phần nhỏ đó một cách song song và độc lập trên các máy tính phân tán.
   Tổng hợp các kết quả thu được để dưa ra kết quả cuối cùng.
 - Hoạt động của MapReduce có thể được tóm tắt như sau:
   Đọc dữ liệu đầu vào.
   Xử lý dữ liệu đầu vào (thực hiện hàm map).
   Sắp xếp và trộn các kết quả thu được từ các máy tính phân tán thích hợp nhất.
   Tổng hợp các kết quả trung gian thu được ( thực hiện hàm reduce).
   Đưa ra kết quả cuối cùng.
