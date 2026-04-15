# Báo Cáo Thí Nghiệm: Tác Động Của Chất Lượng Dữ Liệu Lên AI Agent

**Mã học viên:** AI20K-XXXX
**Họ và tên:** Nguyễn Quang Thọ
**Ngày thực hiện:** 2026-04-15

---

## 1. Kết Quả Thí Nghiệm

Chạy `agent_simulation.py` với 2 bộ dữ liệu và ghi lại kết quả:

| Kịch bản | Phản hồi của Agent | Độ chính xác (1-10) | Ghi chú |
|----------|-------------------|---------------------|---------|
| Clean Data (`processed_data.csv`) | "Based on my data, the best choice is Laptop at $1200." | 9 | Đúng — Laptop là sản phẩm điện tử có giá cao nhất và hợp lệ |
| Garbage Data (`garbage_data.csv`) | "Based on my data, the best choice is Nuclear Reactor at $999999." | 1 | Sai — Agent trả về bản ghi ngoại lệ với giá trị phi thực tế |

---

## 2. Phân Tích & Nhận Xét (Phan tich & nhan xet)

### Tại sao Agent trả lời sai khi dùng Garbage Data? (Tai sao Agent tra loi sai?)

Khi dùng `garbage_data.csv`, Agent trả lời sai vì bộ dữ liệu chứa nhiều vấn đề nghiêm trọng về chất lượng. Thứ nhất, có **ID trùng lặp** (id=1 xuất hiện 2 lần), khiến Agent xử lý dữ liệu không nhất quán. Thứ hai, có **kiểu dữ liệu sai** trong cột `price` (giá trị "ten dollars" không phải số), gây lỗi khi tính toán. Thứ ba, có **giá trị ngoại lệ cực đoan** là sản phẩm "Nuclear Reactor" với giá 999.999, không phản ánh thực tế thị trường. Thứ tư, bản ghi "Ghost Item" có **ID null và price = 0**, nghĩa là dữ liệu không hợp lệ nhưng vẫn tồn tại trong file. Vì Agent đơn giản lấy bản ghi có giá cao nhất trong danh mục "electronics", nó chọn "Nuclear Reactor" — một kết quả vô nghĩa và sai hoàn toàn. Điều này chứng minh rằng dữ liệu rác gây hại hơn là prompt kém: dù Agent rất thông minh, nó vẫn cho ra kết quả sai nếu dữ liệu đầu vào không sạch.

---

## 3. Kết Luận

**Dữ liệu chất lượng cao > Prompt chất lượng cao?** Đồng ý.

Dữ liệu sạch quan trọng hơn prompt hay mô hình AI. Trong thí nghiệm này, cùng một Agent với cùng logic, khi dùng dữ liệu sạch cho kết quả chính xác (9/10), nhưng khi dùng dữ liệu rác cho kết quả sai hoàn toàn (1/10). Kết luận: **Garbage In, Garbage Out** — ETL Pipeline và Data Validation là nền tảng của mọi hệ thống AI đáng tin cậy.
