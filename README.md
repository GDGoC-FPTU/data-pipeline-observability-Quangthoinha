[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574075&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** email@example.com
**Name:** Nguyen Quang Tho

---

## Mo ta

Bai lab xay dung mot ETL Pipeline hoan chinh gom 4 buoc: Extract du lieu tu file JSON, Validate loai bo record khong hop le (gia <= 0 hoac category rong), Transform chuan hoa du lieu va tinh gia giam 10%, sau do Load ket qua ra file CSV. Ngoai ra, bai lab thu nghiem tac dong cua du lieu rac (garbage data) len ket qua cua AI Agent.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python solution.py
```
Ket qua: file `processed_data.csv` duoc tao ra.

### Chay Agent Simulation (Stress Test)
```bash
python agent_simulation.py
```
Chay Agent voi ca 2 bo du lieu: `processed_data.csv` (clean) va `garbage_data.csv` (rac) de so sanh ket qua.

### Chay Tests
```bash
pytest tests/
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline (duoc tao sau khi chay)
├── garbage_data.csv         # Du lieu rac dung cho Stress Test
├── raw_data.json            # Du lieu dau vao
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- **Tong records dau vao:** 5
- **Records hop le (processed):** 3 (Laptop, Chair, Monitor)
- **Records bi loai (dropped):** 2 (Mystery Box gia am, Phone category rong)
- **Output:** `processed_data.csv` voi cac cot: id, product, price, category, discounted_price, processed_at

