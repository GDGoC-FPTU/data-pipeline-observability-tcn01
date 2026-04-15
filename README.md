[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574034&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 26ai.thanhnc@vinuni.edu.vn
**Name:** Nguyễn Công Thành

---

## Mo ta

(Mo ta ngan gon bai lab va nhung gi ban da lam)
Bài lab này xây dựng một **ETL pipeline tự động** xử lý dữ liệu sản phẩm từ file JSON, áp dụng các bước:
- **Extract**: Đọc dữ liệu thô từ `raw_data.json`.
- **Validate**: Loại bỏ các record có giá `price <= 0` hoặc `category` rỗng (thiếu).
- **Transform**: Tính giá sau giảm 10% (`discounted_price`), chuẩn hóa category sang dạng Title Case, thêm timestamp `processed_at`.
- **Load**: Lưu kết quả ra file `processed_data.csv`.

Ngoài ra, có mô phỏng **stress test** với `generate_garbage.py` để so sánh phản ứng của agent khi dùng dữ liệu sạch (clean) và dữ liệu rác (garbage). Qua đó minh họa tầm quan trọng của **data observability** – nếu không có validation, garbage data sẽ làm sai lệch quyết định của agent.
---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# Mo ta cach ban chay thi nghiem Clean vs Garbage data
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

Số record xử lý thành công: 3
Số record bị loại: 2 (ID 3 và ID 4)
