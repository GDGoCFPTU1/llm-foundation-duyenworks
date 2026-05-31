# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature tăng từ 0.0 lên 1.5, phản hồi trở nên đa dạng và sáng tạo hơn. Ở mức 0.0, câu trả lời thường ngắn gọn, nhất quán và dễ lặp lại giữa các lần gọi. Ở mức 1.0–1.5, mô hình có xu hướng đưa ra nhiều chi tiết hoặc cách diễn đạt độc đáo hơn, nhưng cũng có thể kém ổn định và đôi khi ít chính xác hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature khoảng 0.2–0.4. Mức này giúp chatbot trả lời nhất quán, chính xác và giảm nguy cơ tạo ra thông tin không mong muốn, trong khi vẫn giữ được sự tự nhiên trong giao tiếp.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Theo bảng giá API phổ biến của OpenAI, GPT-4o thường đắt hơn GPT-4o-mini khoảng 10–20 lần tùy tỷ lệ input/output token. Với 10.000 người dùng × 3 lần gọi × 350 token ≈ 10,5 triệu token mỗi ngày, chênh lệch chi phí hàng tháng có thể lên tới hàng nghìn đô la Mỹ.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o phù hợp cho các tác vụ yêu cầu độ chính xác và khả năng suy luận cao như trợ lý pháp lý, phân tích tài liệu phức tạp hoặc hỗ trợ ra quyết định kinh doanh. GPT-4o-mini phù hợp cho chatbot FAQ, phân loại văn bản, tóm tắt nội dung ngắn hoặc các ứng dụng có lưu lượng lớn và yêu cầu tối ưu chi phí.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming đặc biệt quan trọng đối với chatbot tương tác thời gian thực, trợ lý AI hoặc các ứng dụng tạo nội dung dài vì người dùng có thể thấy phản hồi xuất hiện ngay lập tức thay vì phải chờ toàn bộ kết quả. Điều này giúp giảm cảm giác chờ đợi và cải thiện trải nghiệm sử dụng. Ngược lại, non-streaming phù hợp khi hệ thống cần nhận toàn bộ kết quả trước khi xử lý tiếp, chẳng hạn như lưu dữ liệu vào cơ sở dữ liệu, thực hiện kiểm duyệt nội dung hoặc trả về các phản hồi ngắn mà thời gian chờ không đáng kể.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
