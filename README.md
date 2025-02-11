# Tài liệu tham khảo:https://chatgpt.com/c/67ab49d0-915c-8000-96c8-56784b5ff309
# Nguyễn Tùng Dương-BIT220038
# README: Kiểm Thử Hiệu Suất Hệ Thống Bằng Apache JMeter

## 1. Giới Thiệu
Kiểm thử hiệu suất là một phần quan trọng trong việc đánh giá khả năng đáp ứng của hệ thống trước các mức tải khác nhau. Mục tiêu chính của kiểm thử này là:
- Đánh giá thời gian phản hồi của hệ thống.
- Xác định điểm nghẽn (bottleneck) nếu có.
- Kiểm tra khả năng chịu tải của hệ thống.

## 2. Cài Đặt Công Cụ

1. Tải và cài đặt **Apache JMeter** từ trang chủ: [https://jmeter.apache.org/](https://jmeter.apache.org/).
2. Cấu hình Java nếu cần thiết (JMeter yêu cầu Java để chạy).
3. Chạy JMeter bằng lệnh `jmeter.bat` (Windows) hoặc `./jmeter` (Linux/macOS).

## 3. Thiết Lập Kịch Bản Kiểm Thử Hiệu Suất

- **Mô phỏng 50 người dùng đồng thời** truy cập trang web trong vòng **5 phút**.
- Sử dụng **Thread Group** trong JMeter để thiết lập số lượng người dùng và thời gian chạy.
- Tạo một **HTTP Request** để gửi yêu cầu đến trang chủ của website.
- Cấu hình **Listeners** để đo thời gian phản hồi, throughput và tỷ lệ lỗi.

## 4. Thực Hiện Kiểm Thử

### 4.1. Kiểm Thử Tải (Load Testing)
- Chạy kiểm thử với số lượng người dùng tăng dần từ **10 → 50**.
- Ghi nhận thời gian phản hồi trung bình và tỷ lệ lỗi.
- Phân tích kết quả để đánh giá xu hướng hiệu suất hệ thống.

### 4.2. Kiểm Thử Khả Năng Chịu Tải (Stress Testing)
- Tiếp tục tăng số lượng người dùng lên **100**.
- Quan sát thời điểm hệ thống bắt đầu giảm hiệu suất đáng kể.
- Xác định **giới hạn chịu tải** của hệ thống.

## 5. Phân Tích Kết Quả

### 5.1. Kết Quả Theo Từng File Kiểm Thử

#### **File: kiemthutai10.csv**
- Thời gian phản hồi trung bình: **299ms**
- Throughput: **1.87 requests/sec**
- Tỷ lệ lỗi: **24.05%**

#### **File: kiemthutai30.csv**
- Thời gian phản hồi trung bình: **331ms**
- Throughput: **1.79 requests/sec**
- Tỷ lệ lỗi: **17.43%**

#### **File: kiemthutai50.csv**
- Thời gian phản hồi trung bình: **365ms**
- Throughput: **1.95 requests/sec**
- Tỷ lệ lỗi: **11.95%**

### 5.2. Nhận Xét Chung
- Khi tải tăng từ **10 → 50 users**, thời gian phản hồi tăng từ **299ms → 365ms**.
- Khi đạt **50 users**, hệ thống vẫn duy trì mức phản hồi hợp lý nhưng có dấu hiệu chậm lại.
- Throughput dao động từ **1.87 đến 1.95 requests/sec**, có xu hướng giảm nhẹ khi tải tăng.
- Ở mức **10 users**, tỷ lệ lỗi cao (**24.05%**), nhưng khi tăng lên **50 users**, tỷ lệ lỗi giảm xuống **11.95%**, có thể do hệ thống tự điều chỉnh tài nguyên.

## 6. Kết Luận
- Hệ thống có thể xử lý tốt tải lên đến **50 users** nhưng bắt đầu có dấu hiệu giảm hiệu suất.
- Tỷ lệ lỗi cao ở mức tải thấp có thể do vấn đề cấu hình hoặc tối ưu hóa backend chưa tốt.
- Cần tiếp tục kiểm tra với **100 users** để xác định giới hạn thực sự của hệ thống.

## 7. Câu Hỏi Thảo Luận

### 7.1. Tại sao kiểm thử phi chức năng lại quan trọng trong phần mềm?
- Đảm bảo hệ thống hoạt động ổn định dưới tải cao.
- Xác định giới hạn chịu tải trước khi triển khai thực tế.
- Giúp phát hiện bottleneck và tối ưu hiệu suất.

### 7.2. Các thông số quan trọng cần theo dõi trong kiểm thử hiệu suất là gì?
- **Thời gian phản hồi (Response Time).**
- **Throughput (số request xử lý/giây).**
- **Tỷ lệ lỗi (Error Rate).**
- **Sử dụng tài nguyên (CPU, RAM, Network).**

### 7.3. Nếu hệ thống không đáp ứng yêu cầu hiệu suất, bạn sẽ đề xuất giải pháp gì?
- **Tối ưu hóa mã nguồn backend.**
- **Cải thiện caching và load balancing.**
- **Tăng cường tài nguyên phần cứng hoặc sử dụng kiến trúc microservices.**
- **Giảm tải bằng cách sử dụng CDN hoặc tối ưu database.**

---
**Tài liệu này cung cấp hướng dẫn chi tiết về cách kiểm thử hiệu suất hệ thống bằng JMeter. Hãy kiểm tra lại các thông số cụ thể và điều chỉnh theo yêu cầu thực tế.**

