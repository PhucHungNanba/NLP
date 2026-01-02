# Đồ án cuối kỳ: Xử lý ngôn ngữ tự nhiên NLP

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
## Mục đích repo

Dưới đây là đường dẫn Google Drive của em, nơi lưu trữ đầy đủ và minh bạch các tài liệu phân công công việc, kế hoạch, cũng như toàn bộ minh chứng trong suốt quá trình thực hiện đồ án cuối kỳ môn Xử lý ngôn ngữ tự nhiên. https://drive.google.com/drive/folders/1GWSegV0w2Y3-_QxLA-1gEkR1hpAT9rih


## Cấu trúc repo

| Tên file | Mô tả |
|---------|------|
| `NLP_Project.ipynb` | Notebook chính: xử lý dữ liệu, xây dựng mô hình, huấn luyện, kiểm thử |
| `3122411073-Huynh_Phuc_Hung-NLP.docx` | Bản tiểu luận đầy đủ (.docx) |
| `3122411073-Huynh_Phuc_Hung-NLP.pdf` | Bản tiểu luận xuất ra PDF |
| `README.md` | File giới thiệu repo |
| `best_model.pth` | Checkpoint mô hình tốt nhất |

Tải checkpoint mô hình tại đây: [best_model.pth trên Google Drive](https://drive.google.com/drive/folders/1GWSegV0w2Y3-_QxLA-1gEkR1hpAT9rih))
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

## Hạn chế của đề tài
Với tinh thần cầu thị khoa học, em xin thẳng thắn nhìn nhận những hạn chế còn tồn tại của đồ án:
- Vấn đề từ vựng chưa biết: Do giới hạn từ điển ở mức 10.000 từ, mô hình thường xuyên trả về token <unk> khi gặp các từ chuyên ngành hoặc tên riêng.
- Khả năng xử lý câu dài kém: Như đã phân tích ở Chương 4, điểm BLEU giảm mạnh khi câu đầu vào vượt quá 20 từ. Đây là giới hạn vật lý của kiến trúc vector cố định.
- Thiếu tính ứng dụng thực tiễn: Hiện tại mô hình chỉ chạy trên môi trường Google Colab. Người dùng phổ thông chưa thể tiếp cận thông qua một giao diện web hay mobile thân thiện.

## Lộ trình phát triển công nghệ
Để khắc phục các hạn chế trên và nâng cấp hệ thống tiệm cận với các tiêu chuẩn công nghiệp, em xin đề xuất một lộ trình phát triển chi tiết cho giai đoạn tiếp theo (Phase 2), dự kiến kéo dài 12 tuần.
Lộ trình này tập trung vào 3 mũi nhọn chính: Nâng cấp thuật toán, Tối ưu dữ liệu và Triển khai sản phẩm.

![Lộ trình phát triển dự án](https://private-user-images.githubusercontent.com/230809903/531507373-f5f8c88b-d7c0-4db6-9808-eb261e27417d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjczNjk0NjAsIm5iZiI6MTc2NzM2OTE2MCwicGF0aCI6Ii8yMzA4MDk5MDMvNTMxNTA3MzczLWY1ZjhjODhiLWQ3YzAtNGRiNi05ODA4LWViMjYxZTI3NDE3ZC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwMTAyJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDEwMlQxNTUyNDBaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT02ZjZkY2Y1NWFlMzVkZjhjOGNiNTY3MDEyMTFiNTczYjhkMDhiYTNhZjkxNDNlNDVhY2Q3ODg4Y2I0ZDk1YmVjJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.7P5byO-Kwb9oiozTuwnqE09o70vsEc5L9CO7pX_2JXA)

 Chi tiết các hạng mục nâng cấp:
Tuần 1-4: Tích hợp Cơ chế Attention
- Mục tiêu: Giải quyết triệt để vấn đề quên thông tin ở câu dài.
- Kỳ vọng: Điểm BLEU tăng từ 14.6 lên mức 20-22.
Tuần 5-8: Chuyển đổi sang kiến trúc Transformer & BPE
- Thay thế LSTM bằng Transformer để tận dụng khả năng huấn luyện song song.
- Sử dụng Byte Pair Encoding để xử lý từ vựng ở cấp độ ký tự con, giúp loại bỏ hoàn toàn lỗi <unk>.
Tuần 9-12: Triển khai Web App
- Đóng gói mô hình bằng Docker container.
- Xây dựng giao diện người dùng đơn giản bằng Streamlit hoặc Flask.
- Tích hợp API để cho phép các ứng dụng khác gọi vào dịch vụ dịch thuật.
