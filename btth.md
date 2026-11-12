


# BTTH: CẨM NANG SỬ DỤNG AI HIỆU QUẢ CHO TÂN SINH VIÊN

## 1. Sơ đồ xâu chuỗi prompt

```
Prompt 0: Dàn ý ──► Prompt 1: Phần 1 ──► Prompt 2: Phần 2 ──► Prompt 3: Phần 3 ──► Prompt 4: Ghép & rà soát
                    (người duyệt)        (người duyệt)        (người duyệt)           (người kiểm tra cuối)
```

Đầu ra của bước trước làm ngữ cảnh cho bước sau. Cách này tiết kiệm token, dễ sửa từng phần và hạn chế ảo giác lan rộng.

## 2. Các prompt thành phần (khung CREATE)

**Prompt 0 (Dàn ý)**
- C: Bạn là giảng viên Khoa học máy tính.
- R: Lập dàn ý cẩm nang "Học lập trình cùng AI" gồm 3 phần: LLM đoán từ, 3 cách nhận diện ảo giác, prompt mẫu CREATE.
- E: Mỗi phần có tiêu đề + 3 ý chính.
- A: Chỉ dàn ý, tối đa 150 từ, giọng thân thiện.
- T: Gạch đầu dòng.
- E: Đề xuất quy ước chung (xưng hô, độ dài).

**Prompt 1 (Phần 1: AI đoán từ)**
- C: Giảng viên giỏi giải thích bằng ví dụ đời thường.
- R: Viết Phần 1 giải thích LLM, Token, Context Window.
- E: So sánh với gợi ý từ trên bàn phím điện thoại.
- A: ~250 từ, không công thức, không bịa số liệu.
- T: 3 đoạn ngắn + 1 mẹo tiết kiệm token.
- E: Câu chuyển sang chủ đề ảo giác.

**Prompt 2 (Phần 2: Ảo giác)**
- C: Kỹ sư phần mềm có kinh nghiệm kiểm thử.
- R: Nêu 3 cách nhận diện ảo giác khi học lập trình.
- E: Ví dụ AI gọi hàm không tồn tại.
- A: ~300 từ, mỗi cách có hành động cụ thể.
- T: Danh sách đánh số: Dấu hiệu / Ví dụ / Cách kiểm tra.
- E: Nhắc nguyên tắc Human-in-the-loop.

**Prompt 3 (Phần 3: CREATE)**
- C: Chuyên gia prompt engineering.
- R: Giải thích 6 thành phần CREATE và đưa 1 prompt mẫu nhờ sửa lỗi Python.
- E: Mỗi chữ cái có 1 ví dụ ngắn.
- A: ~300 từ, nhắc không đưa dữ liệu cá nhân vào prompt.
- T: Bảng 3 cột + khối prompt mẫu.
- E: Checklist 3 ý tự kiểm tra.

**Prompt 4 (Ghép)**
- C: Biên tập viên sách giáo dục.
- R: Ghép 3 phần thành cẩm nang, thêm tiêu đề và lời mở.
- E: Giữ nguyên cấu trúc từng phần.
- A: Không thêm thông tin mới; chỗ đáng ngờ đánh dấu [CẦN KIỂM CHỨNG].
- T: Markdown, ~600 từ.
- E: Liệt kê các điểm cần kiểm chứng.

## 3. Cẩm nang hoàn chỉnh

# Học lập trình AI an toàn và hiệu quả

## Phần 1. AI "đoán từ" thế nào?
LLM không thực sự "hiểu", it ** dự đoán vị trí chữ tiếp theo theo hiệu suất ** , Tương tự Mẹo từ trên bàn phím điện thoại. AI đọc theo ** mã thông báo ** (một chuỗi ký tự hoặc từ phụ, thường là 3-4 ký tự). Tiếng Việt có nhiều dấu tích hơn: 1.000 từ Khoảng cách 2.000-3.000 token. AI ghi nhớ chỉ trong ** Cảnh báo cửa sổ ** , RAM tạm thời tương thích; hội thoại càng dài càng nhanh và dễ quên thông tin cũ. Vì lời lựa chọn có thể hiện, đôi khi AI nói sai rất tự tin, được gọi là Ảo Giác.

> ** Mẹo tiết kiệm token: ** chỉ gửi đoạn mã cần hỏi; hội thoại dài thì tóm tắt rồi mở cuộc trò chuyện mới. 

## Phần 2. 3 cách nhận dạng giác ảo
1. ** Kiểm tra tên có thật không ** : thư viện, hàm, lạ dữ liệu thì tài liệu chính thức (VD: AI đề xuất hàm ` list.sort_reverse() ` không tồn tại). 2. ** Chạy thử và đối chiếu ** : code không chắc chắn; Hãy thử và kiểm tra các trường biên dịch. 3. ** Hỏi lại cách khác ** : hai lần hỏi ra hai phản ứng Chắc chắn là dấu hiệu ngạc nhiên nhiên; yêu cầu nguồn nêu và do đó có nguồn độc lập.



** Human-in-the-loop: ** người dùng cam kết trách nhiệm cuối cùng về sản phẩm.

## Phần 3. nhắc nhở TẠO mẫu
| Thành phần | Ý nghĩa | Ví dụ | |---|---|---| | Nhân vật | Giao vai | "Bạn là học viên Python" | | Yêu cầu | Việc cần làm | "Giải thích lỗi IndexError" | | Ví dụ | Mẫu đầu ra | "Nguyên nhân → Cách sửa" | | Điều chỉnh | Chiến đấu lượng | "Tối đa 150 từ" | | Output type | Định dạng | "Gạch đầu dòng + code" | | Tiện ích bổ sung | Bổ sung | "Gợi ý 1 bài tập tương tự" |








** Gợi ý mẫu: **
> Bạn là thành viên chiến đấu Python. Giải thích sao đoạn mã bên dưới cảnh báo ` IndexError ` và cách sửa theo mẫu: Nguyên nhân → Cách sửa. Chỉ sửa lỗi, tối đa 150 từ, sử dụng mã hóa đính kèm đầu dòng. Cuối cùng gợi ý 1 bài tập tương tự. Code: ` [dán code] `

** Danh sách kiểm tra: ** ☐ Đủ vai trò, việc làm, định dạng? ☐ Đã xóa dữ liệu cá nhân, mật khẩu, API key? ☐ Chỉ gửi đoạn cần thiết?

** Lời nhắn: ** Hỏi rõ (TẠO), kiểm tra kỹ thuật (chống ảo giác), bảo vệ dữ liệu, tự chịu trách nhiệm với bài của mình.
