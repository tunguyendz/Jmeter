Báo Cáo Thực Hành Kiểm Thử Hiệu Năng Với Apache JMeter

1. Thông tin sinh viên

Họ và tên: Nguyễn Trung Tú

Mã sinh viên: 23010514

Lớp / Học phần: Đánh giá và kiểm định chất phần mềm 

2. Giới thiệu về công cụ Apache JMeter

Apache JMeter là phần mềm mã nguồn mở viết bằng ngôn ngữ Java, được sử dụng phổ biến để kiểm thử tải (Load Testing) và đo lường hiệu năng (Performance Testing) cho các hệ thống Web, RESTful API và cơ sở dữ liệu.

Các thành phần sử dụng trong bài thực hành:

Test Plan: Kịch bản tổng thể chứa toàn bộ cấu hình của đợt kiểm thử.

Thread Group: Giả lập số lượng người dùng ảo (Virtual Users) truy cập đồng thời vào hệ thống.

HTTP Request (Sampler): Tạo và gửi các yêu cầu HTTP/HTTPS đến máy chủ đích.

Listeners (View Results Tree & Summary Report): Thu thập, hiển thị chi tiết từng phản hồi và tổng hợp bảng số liệu thống kê hiệu năng.

3. Môi trường và Thiết kế kịch bản kiểm thử

3.1. Môi trường thực hiện

Hệ điều hành: Windows 10/11 (64-bit)

Phiên bản Java: Java Runtime Environment (JRE 1.8.0_503)

Phiên bản công cụ: Apache JMeter 5.6.3

3.2. Thông số kịch bản (Test Scenario)

Mục tiêu kiểm thử: REST API Demo (https://jsonplaceholder.typicode.com/posts)

Phương thức (Method): GET

Cấu hình tải (Thread Group):

Number of Threads (Users): 50 người dùng ảo truy cập

Ramp-up Period: 10 giây (trung bình mỗi giây tăng thêm 5 người dùng)

Loop Count: 2 lần lặp (Tổng cộng gửi đi 100 requests)

3.3. Hình ảnh cấu hình kịch bản

📌 Cấu hình Thread Group:

<img width="975" height="549" alt="image" src="https://github.com/user-attachments/assets/1366db26-202a-41a2-850b-99782f9736a7" />

📌 Cấu hình HTTP Request:

<img width="975" height="543" alt="image" src="https://github.com/user-attachments/assets/fd7517dc-21ef-428c-abfc-b2dfe57dffb8" />


4. Kết quả thực hiện và Đánh giá

4.1. Kết quả chi tiết trên View Results Tree

Toàn bộ các yêu cầu gửi tới máy chủ đều nhận được phản hồi thành công với mã trạng thái 200 OK (hiển thị biểu tượng khiên màu xanh lá).

<img width="975" height="541" alt="image" src="https://github.com/user-attachments/assets/a3533d53-8824-407a-9e22-dc71228ec783" />


4.2. Bảng thống kê hiệu năng trên Summary Report

Dưới đây là bảng tổng hợp các chỉ số đo lường sau khi hoàn tất 100 requests:

<img width="1493" height="822" alt="image" src="https://github.com/user-attachments/assets/b1942ef4-0cff-493c-a599-a1589ec1e794" />


4.3. Nhận xét và Đánh giá kết quả

Tổng số mẫu thử (# Samples): Đạt đủ 100 requests theo đúng kịch bản thiết kế (50 threads x 2 loops).

Tỷ lệ lỗi (Error %): 0.00% — Hệ thống xử lý thành công 100% yêu cầu, không xảy ra hiện tượng nghẽn mạng hay từ chối kết nối (Timeout/5xx).

Thời gian phản hồi (Average / Min / Max): Thời gian phản hồi trung bình ở mức thấp và ổn định, đáp ứng tốt trải nghiệm người dùng.

Thông lượng (Throughput): Duy trì tốc độ xử lý yêu cầu trên mỗi giây tốt trong suốt quá trình tăng tải (Ramp-up).
