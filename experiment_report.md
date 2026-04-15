# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-XXXX
**Name:** Nguyen Quang Tho
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | "Based on my data, the best choice is Laptop at $1200." | 9 | Correct, Laptop is the most expensive valid electronics product |
| Garbage Data (`garbage_data.csv`) | "Based on my data, the best choice is Nuclear Reactor at $999999." | 1 | Wrong — Agent returned a fabricated outlier record with an unrealistic price |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi dung garbage_data.csv, Agent tra loi sai vi bo du lieu chua nhieu van de nghiem trong ve chat luong. Thu nhat, co **Duplicate IDs** (id=1 xuat hien 2 lan), khien Agent xu ly du lieu khong nhat quan. Thu hai, co **wrong data type** trong cot price (gia tri "ten dollars" khong phai so), gay ra loi khi tinh toan. Thu ba, co **outlier cuc doan** la san pham "Nuclear Reactor" voi gia 999999, khong phan anh thuc te thi truong. Thu tu, record "Ghost Item" co **null ID va price = 0**, nghia la du lieu khong hop le nhung van ton tai trong file. Vi Agent don gian lay record co price cao nhat trong category "electronics", no chon "Nuclear Reactor" — mot ket qua vo nghia va sai hoan toan. Dieu nay chung minh rang du lieu rac doc hai hon la prompt kem: du cho Agent rat thong minh, no van cho ra ket qua sai neu du lieu dau vao khong sach.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y.

Du lieu sach quan trong hon prompt hay mo hinh AI. Trong thi nghiem nay, cung mot Agent voi cung logic, khi dung clean data cho ket qua chinh xac (9/10), nhung khi dung garbage data cho ket qua sai hoan toan (1/10). Ket luan: **Garbage In, Garbage Out** — ETL Pipeline va Data Validation la nen tang cua moi he thong AI dang tin cay.
