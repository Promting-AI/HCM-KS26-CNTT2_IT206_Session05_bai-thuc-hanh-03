# Yêu cầu đầu ra:
## Promt 
```markdown
# CONTEXT
Bạn là nhân viên phân tích khiếu nại của bộ phận chăm sóc khách hàng ở một cửa hàng bán laptop.
Bạn chỉ giúp nhân viên phân tích, bạn không được thay cửa hàng quyết định.
Dưới đây là khiếu nại của khách. Đây chỉ là lời khách kể, cửa hàng chưa kiểm tra lại:
"""
{{NOI_DUNG_KHIEU_NAI}}
"""
Cửa hàng chưa cho biết chính sách đổi trả, hoàn tiền hay bảo hành.

# REQUEST
Bạn hãy làm 5 việc sau:
1. Tìm ra các vấn đề khách đang gặp.
2. Đánh giá mức độ nghiêm trọng của từng vấn đề.
3. Nêu những thông tin còn thiếu cần kiểm tra lại.
4. Đề xuất đúng 2 cách giải quyết phù hợp.
5. Viết một tin nhắn trả lời khách thật lịch sự.

# EXPLANATION
Lý do làm từng bước:
- Nếu trả lời ngay, bạn dễ bỏ sót vấn đề hoặc kết luận khi chưa có căn cứ.
  Vì vậy hãy dùng kỹ thuật Chain-of-Thought: mỗi bước viết lý do trước, kết quả sau.
- Bước sau chỉ được dùng kết quả của bước trước.

Quy tắc về nhãn thông tin, mỗi thông tin phải gắn 1 nhãn:
- [DỮ KIỆN] = khách đã nói rõ trong khiếu nại, ghi chú đây là lời khách.
- [GIẢ THUYẾT] = bạn đoán, phải ghi lý do và cách kiểm tra.
- [CHƯA XÁC ĐỊNH] = chưa đủ thông tin để kết luận.

Quy tắc về mức độ nghiêm trọng:
- Có 3 mức: Cao, Trung bình, Thấp.
- Đánh giá dựa trên 4 điều: ảnh hưởng đến việc dùng máy, có nguy hiểm không,
  có bị lặp lại không, có sửa được không.
- Nếu thiếu thông tin thì ghi rõ mức đó chỉ là tạm thời.

Quy tắc không được làm:
- Không tự nghĩ ra chính sách đổi trả, hoàn tiền, bảo hành. Vì cửa hàng chưa cung cấp,
  nếu đoán sai thì nhân viên có thể hứa sai với khách.
- Không kết luận nguyên nhân hỏng, lỗi của ai, hay khách đúng hay sai khi chưa có bằng chứng.
- Không tự thêm thông tin ngoài khiếu nại, ví dụ tên máy, cấu hình, hóa đơn.
- Không đổ lỗi cho khách hay cho nhân viên đã kiểm tra máy lần trước.

Quy tắc cho tin nhắn gửi khách:
- Không hứa đổi máy, hoàn tiền hay hẹn ngày cụ thể.
- Nói bước tiếp theo và xin khách thêm thông tin.
- Chỗ nào cần cửa hàng điền, ví dụ thời gian liên hệ lại, thì ghi: [cửa hàng tự điền].

Quy tắc tự kiểm tra trước khi trả lời:
- Mọi thông tin đã có nhãn chưa? Có tự nghĩ ra chính sách không? Có kết luận khi chưa có bằng chứng không?
- Nếu có thì sửa lại.

# ACTION
Hãy làm lần lượt 6 bước.
Bước 1: Liệt kê từng ý khách đã nói.
Bước 2: Tách từng vấn đề ra riêng, ghi lại câu gốc của khách.
Bước 3: Đánh giá mức độ nghiêm trọng của từng vấn đề, ghi lý do.
Bước 4: Nêu thông tin còn thiếu. Mỗi mục ghi: thiếu gì, vì sao cần, kiểm tra bằng cách nào.
Bước 5: Đưa ra đúng 2 phương án. Mỗi phương án ghi: làm gì, ưu điểm, hạn chế,
        cần kiểm tra gì trước khi làm.
Bước 6: Viết tin nhắn trả lời khách.

# TONE
- Phần phân tích: rõ ràng, ngắn gọn, mỗi ý một câu.
- Tin nhắn gửi khách: lịch sự, thông cảm, tiếng Việt, xưng "chúng tôi", gọi khách là "Anh/Chị".

# EXTRAS
Kết quả trả về gồm:
1. Báo cáo phân tích theo từng bước, từ Bước 1 đến Bước 6.
2. Bảng "Danh sách thông tin cần xác minh": Thông tin | Vì sao cần | Cách kiểm tra.
3. Bảng "Hai phương án xử lý": Phương án | Ưu điểm | Hạn chế.
4. Định dạng tất cả thành file .md

```
--- 

- Báo cáo phân tích theo từng bước. Danh sách thông tin cần xác minh. Hai phương án xử lý, kèm ưu điểm và hạn chế.
```markdown
# Kết quả phân tích khiếu nại laptop

> Mức độ và tiêu chí là **(đề xuất)**. Không dùng chính sách đổi trả nào vì đề không cho.

---

## 1/ Báo cáo phân tích theo từng bước

### Bước 1: Dữ kiện (toàn bộ là lời khách, chưa xác minh)

- Mua 10 ngày trước; máy nóng thường xuyên; quạt kêu to; pin ~2 tiếng.
- Đã mang đến cửa hàng, chỉ được vệ sinh; 2 ngày sau lỗi vẫn còn.
- Khách muốn đổi máy hoặc hoàn tiền.

### Bước 2: Vấn đề

| Vấn đề | Nhãn |
|---|---|
| V1. Máy nóng | [DỮ KIỆN] |
| V2. Quạt ồn | [DỮ KIỆN] |
| V3. Pin ~2 tiếng | [DỮ KIỆN] |
| V4. Lần xử lý đầu không hiệu quả | [DỮ KIỆN] |
| Quạt ồn do máy nóng | [GIẢ THUYẾT]: kiểm tra bằng đo nhiệt độ, tốc độ quạt |
| Nguyên nhân gốc | [CHƯA XÁC ĐỊNH] |

### Bước 3: Mức độ nghiêm trọng (tạm thời vì thiếu thông tin)

| Vấn đề | Mức | Lý do |
|---|---|---|
| V1 | Cao | Thường xuyên, ảnh hưởng hiệu năng và độ bền |
| V2 | Trung bình | Ảnh hưởng trải nghiệm, có thể là hệ quả của V1 |
| V3 | Trung bình | Chưa biết thông số pin nên chưa rõ có bất thường |
| V4 | Cao | Lỗi lặp lại sau can thiệp, khách mất niềm tin |

**Ưu tiên:** V1, V4 trước.

### Bước 4 và 5

Xem mục 2/ và 3/.

### Bước 6: Tin nhắn gửi khách

> Kính gửi Anh/Chị [Tên],
>
> Chúng tôi xin lỗi vì máy vẫn chưa được cải thiện sau lần kiểm tra trước. Chúng tôi đã ghi nhận tình trạng nóng, quạt ồn, pin ~2 tiếng và đề nghị đổi hoặc hoàn tiền của Anh/Chị, và sẽ xem xét theo quy định của cửa hàng.
>
> Để xử lý chính xác, Anh/Chị vui lòng cho biết: (1) mã đơn hoặc hóa đơn; (2) máy nóng, quạt ồn khi làm việc gì; (3) ảnh hoặc video nếu có.
>
> Chúng tôi sẽ liên hệ lại trong [cửa hàng tự điền].
>
> Trân trọng,
> [Tên nhân viên] – CSKH

---

## 2/ Danh sách thông tin cần xác minh

| # | Thông tin | Cách kiểm tra |
|---|---|---|
| 1 | Ngày mua, hóa đơn | Tra hệ thống bán hàng |
| 2 | Chính sách đổi, trả, hoàn, bảo hành | Văn bản chính sách; hỏi quản lý |
| 3 | Model, thông số pin | Hồ sơ sản phẩm |
| 4 | Nhiệt độ, độ ồn, tác vụ khi xảy ra | Kiểm tra kỹ thuật; hỏi khách |
| 5 | Lần tiếp nhận trước đã kiểm tra gì | Phiếu tiếp nhận |
| 6 | Tình trạng ngoại quan (va đập, vào nước) | Kiểm tra trực tiếp |
| 7 | Cách khách dùng máy | Hỏi khách |
| 8 | Ai duyệt đổi hoặc hoàn | Hỏi quản lý |

---

## 3/ Hai phương án xử lý

| Phương án | Ưu điểm | Hạn chế |
|---|---|---|
| **PA1. Kiểm tra kỹ thuật có biên bản, rồi quyết định** | Có bằng chứng khách quan; tránh kết luận sai | Khách thấy chậm; chưa đáp ứng ngay đề nghị đổi hoặc hoàn |
| **PA2. Trình cấp có thẩm quyền xét đổi hoặc hoàn theo chính sách** | Đúng nguyện vọng khách; có thể nhanh | Phụ thuộc chính sách chưa biết; thiếu bằng chứng kỹ thuật |

Hai phương án có thể kết hợp: làm PA1 lấy bằng chứng cho PA2.
```



