# Báo cáo cá nhân — Day 01: Lọc tin nhắn rác bằng ML, DL, Embedding và LLM

> Đổi tên file này thành `MSSV_HoTen.md` của bạn, ví dụ `2A20260000_NguyenVanAn.md`, rồi điền từng mục. Xoá các dòng hướng dẫn in nghiêng khi xong.

- **MSSV:** 2A202603772
- **Họ và tên:** Nguyễn Đức Hiếu
- **SEED** (in ở ô đầu notebook): 4316

## 1. Bằng chứng

| Tệp | Có? |
| --- | --- |
| [`day01_lab.ipynb`](day01_lab.ipynb) — notebook đã chạy, còn output | có |
| [`lab1_report.json`](lab1_report.json) — do ô "Báo cáo cuối" sinh ra | có |
| [`hand_calc.jpg`](hand_calc.jpg) — ảnh tính tay có các bước | có |

## 2. Kết quả chính
BoW + LogReg: F1 0.919, p95 0.12ms; BoW + MLP: 0.947, 0.31ms; MiniLM + kNN: 0.947, 60.95ms; MiniLM + LogReg: 0.974, 34.74ms; MiniLM + MLP: 0.974, 49.31ms. LLM nhỏ: 0.864, 2723.70ms; LLM lớn: 0.905, 2407.91ms; few-shot: 0.850, 3067.90ms. Đây là F1 SUB 40; F1 test đầy đủ.

## 3. Dự đoán và thực tế

Đề #3: Thử MLP với 4 và 512 nơ-ron. Mạng 4 nơ-ron có 8.009 tham số, F1 0.914, train 2.68 giây. Mạng 512 nơ-ron có 1.025.025 tham số, F1 0.942, train 18.44 giây. Mạng nhỏ phù hợp khi cần tiết kiệm tài nguyên.
## 4. Phân tích 50 case khó

BoW + LogReg giảm mạnh nhất (0.919 xuống 0.333). Hai dạng gây lỗi là spam viết như hội thoại tự nhiên (chỉ đúng 10%) và tin nhắn lừa đảo thao túng (đúng 12%). Nguyên nhân chủ yếu do phụ thuộc từ khóa.

## 5. Thử thách cá nhân

Đề #3: Thử MLP với 4 và 512 nơ-ron. Mạng 4 nơ-ron có 8.009 tham số, F1 0.914, train 2.68 giây. Mạng 512 nơ-ron có 1.025.025 tham số, F1 0.942, train 18.44 giây. Mạng nhỏ phù hợp khi cần tiết kiệm tài nguyên.

## 6. Phương án cho sản phẩm thật

Chọn MiniLM + LogReg vì F1 0.974, p95 34.74ms, đạt SLA dưới 50ms. Với 10 triệu SMS/ngày cần nhiều worker để đáp ứng lưu lượng. Đánh đổi là chi phí tính toán embedding và khả năng sai trên các case khó.

## 7. AI log và điều đã học

gợi ý code Đề #3 So sánh MLP, Code thử nghiệm, Chạy và đo F1, thời gian
