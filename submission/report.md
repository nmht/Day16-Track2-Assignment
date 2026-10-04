1. Tôi dùng AWS, us-east-1, instance type t3.medium (Compute) & t3.micro (Bastion), source commit mới nhất.
2. Dataset có 284,807 dòng, chia train/validation/test theo tỷ lệ 60/20/20 (tương ứng 170883/56962/56962 dòng, có stratify), seed 16.
3. Load dữ liệu mất \~2.39 giây; training mất \~3.58 giây; best iteration là 68.
4. AUC 0.9768, Accuracy 0.9995, F1 0.8478, Precision 0.9070, Recall 0.7959 trên tập test.
5. Latency 1 dòng \~1.18 ms; throughput batch 1.000 dòng \~333,056.7 dòng/giây; cách đo: lấy median qua nhiều lần lặp, có warm-up trước khi đo, sử dụng hàm predict\_proba trên pandas DataFrame.
6. CPU/RAM/Network tôi quan sát sau khi chạy benchmark, RAM sử dụng ổn định ở mức thấp, Network spike nhẹ lúc tải file dataset; ảnh đính kèm trong tệp bài nộp.
7. Billing chưa cập nhật tại thời điểm 09:05 ngày 04/10/2026. Danh sách tài nguyên đã chạy trong khoảng \~45 phút bao gồm: 1 EC2 t3.medium, 1 EC2 t3.micro, 1 NAT Gateway, và 1 ALB.
8. Tôi đã tải kết quả và xóa tài nguyên ngay sau đó bằng lệnh `terraform destroy`; terminal báo Destroy Complete.
