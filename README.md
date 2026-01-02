# Đồ án cuối kỳ: Xử lý ngôn ngữ tự nhiên (NLP)

## Đề tài
Dịch máy Anh–Pháp với mô hình Encoder–Decoder sử dụng LSTM

---

## Giảng viên hướng dẫn
PGS. TS. Nguyễn Tuấn Đăng  
Khoa Công nghệ Thông tin — Trường Đại học Sài Gòn

## Sinh viên thực hiện
- Huỳnh Phúc Hưng — 3122411073  
- Lớp: DCT122C3  
- Học kỳ: HK1 / 2025–2026

---

## Cấu trúc repo

| Tên file | Mô tả |
|---------|------|
| `NLP_Project.ipynb` | Notebook chính: xử lý dữ liệu, xây dựng mô hình, huấn luyện, kiểm thử |
| `3122411073-Huynh_Phuc_Hung-NLP.docx` | Bản tiểu luận đầy đủ (.docx) |
| `3122411073-Huynh_Phuc_Hung-NLP.pdf` | Bản tiểu luận xuất ra PDF |
| `README.md` | File giới thiệu repo |
| `best_model.pth` *(nếu có)* | Checkpoint mô hình tốt nhất |

---

## Mô hình sử dụng

- Kiến trúc: Encoder–Decoder với LSTM  
- Ngôn ngữ nguồn: Tiếng Anh  
- Ngôn ngữ đích: Tiếng Pháp  
- Bộ dữ liệu: Multi30K (en-fr)  
- Kỹ thuật: Tokenization, Padding, Teacher Forcing  
- Đánh giá: BLEU Score, phân tích lỗi  

---

## Cách chạy mô hình

1. Tải dữ liệu từ Multi30K  
2. Chạy từng cell theo thứ tự: tiền xử lý → huấn luyện → kiểm thử  
3. Sử dụng hàm `translate(sentence)` để dịch câu mới  

---

## Kết quả

- BLEU Score trên tập test: ~0.15  
- Mô hình dịch tốt các câu ngắn, đơn giản  
- Một số lỗi phổ biến: từ vựng hiếm, lặp từ, mất ngữ cảnh  

---

## Lỗi đã gặp

Trong quá trình đọc dữ liệu, em từng gặp lỗi `UnicodeDecodeError` khi dùng `pd.read_csv('fra.txt')`.  
Nguyên nhân là do file không được mã hóa theo chuẩn UTF-8.  
Em đã khắc phục bằng cách thêm tham số `encoding='latin1'`.  
Sau đó, dữ liệu được đọc thành công và xử lý bình thường.  

---

## Ghi chú

- Mô hình chưa tích hợp Attention hoặc Beam Search  
- Nếu muốn cải tiến, có thể thử thêm các kỹ thuật như BPE, Transformer  
- Tiểu luận có phân tích chi tiết lỗi và đề xuất hướng phát triển  

---

## Tài liệu tham khảo

- Sutskever et al. (2014). Sequence to Sequence Learning with Neural Networks  
- PyTorch Documentation: torch.nn.LSTM  
- Multi30K Dataset: https://github.com/multi30k/dataset  
- Slide bài giảng học phần NLP — Nguyễn Tuấn Đăng  

---

## Mã & Hướng phát triển

Nếu sau này em thêm Attention hoặc Beam Search thì có thể cập nhật lại phần mô hình và kết quả.  
Có thể bổ sung thêm phần demo ảnh mô hình hoặc hướng dẫn cài đặt chi tiết hơn nếu cần.  
