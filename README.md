# \# Báo cáo kiểm thử hiệu năng website bằng Apache JMeter

# 

# \## 1. Tổng quan

# 

# Kiểm thử hiệu năng là một hoạt động quan trọng nhằm đánh giá khả năng xử lý của hệ thống khi có nhiều người dùng truy cập cùng lúc. Thông qua kiểm thử hiệu năng, chúng ta có thể đo lường thời gian phản hồi của hệ thống, số lượng yêu cầu mà hệ thống có thể xử lý trong một khoảng thời gian nhất định và phát hiện các lỗi khi hệ thống chịu tải cao.

# 

# Trong bài thực hành này, công cụ \*Apache JMeter\* được sử dụng để thực hiện kiểm thử hiệu năng cho một website công khai trên Internet. JMeter cho phép mô phỏng nhiều người dùng truy cập đồng thời vào hệ thống và thu thập các thông tin quan trọng về hiệu năng.

# 

# Website được lựa chọn để kiểm thử:

# 

# https://www.wikipedia.org

# 

# ---

# 

# \# 2. Công cụ và môi trường sử dụng

# 

# Các công cụ và môi trường được sử dụng trong bài kiểm thử:

# 

# \* Công cụ kiểm thử: \*Apache JMeter\*

# \* Phiên bản: \*JMeter 5.x\*

# \* Hệ điều hành: \*Windows\*

# \* Giao thức sử dụng: \*HTTP/HTTPS\*

# \* Loại kiểm thử: \*Load Testing\*

# 

# ---

# 

# \# 3. Thiết kế kịch bản kiểm thử

# 

# Trong bài thực hành này, ba kịch bản kiểm thử được xây dựng nhằm mô phỏng các mức tải khác nhau của người dùng.

# 

# \## 3.1 Kịch bản 1 – Truy cập cơ bản

# 

# Kịch bản này mô phỏng một số lượng nhỏ người dùng truy cập vào trang chủ của website.

# 

# Thông số cấu hình:

# 

# \* Số lượng người dùng (Threads): 10

# \* Ramp-up period: 5 giây

# \* Loop Count: 5 lần

# 

# Request thực hiện:

# 

# \* HTTP Method: GET

# \* URL Path: /

# 

# Mục tiêu của kịch bản này là kiểm tra tốc độ phản hồi của hệ thống khi có tải nhẹ.

# 

# ---

# 

# \## 3.2 Kịch bản 2 – Tải cao

# 

# Kịch bản này mô phỏng số lượng người dùng lớn hơn truy cập vào website trong một khoảng thời gian ngắn.

# 

# Thông số cấu hình:

# 

# \* Số lượng người dùng: 50

# \* Ramp-up period: 30 giây

# \* Loop Count: 5

# 

# Các request gửi tới server:

# 

# \* GET /

# \* GET /wiki/Main\_Page

# 

# Mục tiêu của kịch bản này là đánh giá khả năng xử lý của website khi có nhiều người dùng truy cập đồng thời.

# 

# ---

# 

# \## 3.3 Kịch bản 3 – Hành vi người dùng thực tế

# 

# Kịch bản này mô phỏng hành vi duyệt web của người dùng khi truy cập nhiều trang khác nhau trên website.

# 

# Thông số cấu hình:

# 

# \* Số lượng người dùng: 20

# \* Thời gian chạy: 60 giây

# 

# Các request được gửi:

# 

# \* GET /wiki/Technology

# \* GET /wiki/Computer

# 

# Kịch bản này giúp đánh giá hiệu năng hệ thống trong trường hợp người dùng truy cập nhiều nội dung khác nhau.

# 

# ---

# 

# \# 4. Thu thập kết quả kiểm thử

# 

# Trong quá trình thực hiện kiểm thử, JMeter sử dụng các Listener để ghi nhận kết quả. Các Listener được sử dụng bao gồm:

# 

# \* \*View Results Tree\*: hiển thị chi tiết từng request và response.

# \* \*Summary Report\*: tổng hợp các chỉ số hiệu năng.

# \* \*Graph Results\*: biểu diễn kết quả dưới dạng đồ thị.

# 

# Các chỉ số quan trọng được quan sát bao gồm:

# 

# \* Response Time (thời gian phản hồi)

# \* Throughput (số request xử lý trong một giây)

# \* Error Rate (tỷ lệ lỗi)

# 

# ---

# 

# \# 5. Kết quả thu được

# 

# | Kịch bản           | Response Time trung bình | Throughput           | Error Rate |

# | ------------------ | ------------------------ | -------------------- | ---------- |

# | Truy cập cơ bản    | khoảng 210 ms            | khoảng 38 request/s  | 0%         |

# | Tải cao            | khoảng 360 ms            | khoảng 105 request/s | 0%         |

# | Hành vi người dùng | khoảng 295 ms            | khoảng 70 request/s  | 0%         |

# 

# ---

# 

# \# 6. Đánh giá kết quả

# 

# Dựa trên kết quả kiểm thử, có thể đưa ra một số nhận xét sau:

# 

# \* Khi số lượng người dùng thấp, hệ thống phản hồi rất nhanh.

# \* Khi số lượng người dùng tăng lên, thời gian phản hồi của hệ thống cũng tăng theo.

# \* Throughput tăng khi số lượng request được gửi nhiều hơn.

# \* Không xuất hiện lỗi trong quá trình kiểm thử, cho thấy hệ thống hoạt động ổn định.

# 

# Nhìn chung, website có thể xử lý tốt các mức tải trung bình mà không xảy ra lỗi.

# 

# ---

# 

# \# 7. Kết luận

# 

# Bài thực hành đã giúp hiểu rõ hơn về cách sử dụng \*Apache JMeter\* để thực hiện kiểm thử hiệu năng cho một website.

# 

# Thông qua ba kịch bản kiểm thử khác nhau, chúng ta có thể quan sát được sự thay đổi của thời gian phản hồi và thông lượng khi số lượng người dùng thay đổi.

# 

# Kết quả kiểm thử cho thấy website hoạt động ổn định và có khả năng xử lý nhiều yêu cầu cùng lúc.

# 

# ---

# 

# \# 8. Cấu trúc thư mục dự án

# 

# jmeter

# │

# ├── testplan.jmx

# ├── ketqua.csv

# ├── screenshots

# │   ├── testplan.png

# │   ├── threadgroup1.png

# │   ├── threadgroup2.png

# │   ├── threadgroup3.png

# │   └── summary.png

# │

# └── README.md

# 

# ---

# 

# \# 9. Tài liệu đính kèm

# 

# Repository bao gồm các thành phần sau:

# 

# \* File cấu hình kiểm thử \*JMeter (.jmx)\*

# \* File kết quả kiểm thử \*CSV\*

# \* Ảnh chụp màn hình quá trình kiểm thử

# \* Báo cáo README.md

