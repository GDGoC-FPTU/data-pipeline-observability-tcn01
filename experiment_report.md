# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600142
**Name:** Nguyễn Công Thành
**Date:** 15/04/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | "Based on my data, the best choice is Laptop at $1200." |10  | Giá hợp lý, category phù hợp. |
| Garbage Data (`garbage_data.csv`) |  "Based on my data, the best choice is Nuclear Reactor at $999999."  | 1 | Giá cực lớn, sản phẩm không thực tế. |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi dùng garbage data, agent bị nhiễu do:

 - Outlier giá: $999999 quá lớn, làm lệch quyết định.

 - Category không hợp lệ: "Nuclear Reactor" không phải sản phẩm thực tế.

 - Thiếu validation: Dữ liệu chưa qua pipeline ETL (không lọc, không chuẩn hóa).

 - Trùng ID: Gây nhầm lẫn khi tổng hợp.

→ Dữ liệu chưa được làm sạch có thể dẫn đến quyết định sai lệch nghiêm trọng.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

**Đồng ý.** Một prompt được viết rất tốt cũng không thể cứu vãn nếu dữ liệu đầu vào chứa outlier, giá trị sai, hoặc danh mục không hợp lệ. Dữ liệu chất lượng cao (đã qua validation, cleansing, transformation) là nền tảng cho bất kỳ AI agent nào. Prompt chỉ có thể phát huy tối đa khi dữ liệu đã đáng tin cậy. Vì vậy, đầu tư vào 
**data observability và pipeline ETL/ELT** quan trọng hơn là chỉ tinh chỉnh prompt.
