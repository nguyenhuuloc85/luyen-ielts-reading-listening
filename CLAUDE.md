# CLAUDE.md – Luyện đọc và nghe IELTS (~band 5.5)

- **Dự án:** ứng dụng một tệp `index.html` (HTML + CSS + JS thuần, không build), luyện đọc và nghe IELTS cho thầy Nguyễn Hữu Lộc. Độc lập với dự án chấm bài vẽ kỹ thuật.
- **Cách trả lời:** tiếng Việt, đi thẳng vào vấn đề; chưa chắc thì nói rõ, không đoán.
- **Chỉ thêm bài khi được yêu cầu.** Sửa xong thì báo cáo ngắn rồi dừng; commit khi người dùng cho phép hoặc phiên có chỉ định nhánh.

## Thêm bài mới

Mọi bài nằm trong mảng `DATA` ở đầu thẻ `<script>` của `index.html`. Thêm một mục vào cuối mảng, giữ dấu phẩy giữa các mục.

### Bài đọc

```js
{
  id: "ma-ngan",                 // duy nhất, chữ thường, không dấu, dùng để lưu điểm
  title: "Tiêu đề tiếng Anh",
  topic: "Chủ đề tiếng Việt",
  paras: ["Đoạn A...", "Đoạn B..."],        // mỗi phần tử là một đoạn, nhãn A, B, C... tự sinh
  gloss: [["word", "nghĩa tiếng Việt"]],    // 5 từ khó
  qs: [ { q: "Câu hỏi?", p: "B", a: 2,      // p = đoạn chứa bằng chứng, a = chỉ số đáp án đúng (0–3)
          o: ["A", "B", "C", "D"], ex: "Đoạn B: “trích câu bằng chứng”. Giải thích vì sao các đáp án khác sai." } ]
}
```

### Bài nghe

Thêm `kind: "listening"`, bỏ `paras` và `gloss`, thêm:

```js
kind: "listening",
topic: "Nghe · ...",
setting: "Một câu tiếng Việt mô tả bối cảnh.",
speakers: ["Karen", "Mark"],     // một người = bài nói; hai người = hội thoại (giọng cao / thấp)
script: [ { who: "Karen", text: "..." } ],
qs: [ { q: "...", line: 4, a: 3, o: [...], ex: "..." } ]   // line = chỉ số lượt nói (từ 0) chứa bằng chứng
```

Bài nghe dùng giọng tổng hợp của trình duyệt (Web Speech API); không có tệp âm thanh.

## Chuẩn nội dung

- **Độ khó band 5.5:** câu ngắn đến vừa, từ vựng thông dụng và học thuật cơ bản (B1–B2), mỗi bài đọc khoảng 330–370 từ, 5 đoạn A–E; bài nghe 7–17 lượt nói. Mỗi bài 6 câu trắc nghiệm A–D, một đáp án đúng.
- **Soạn mới hoàn toàn**, không chép đề IELTS hay văn bản có bản quyền.
- **Đáp án nhiễu** phải hợp lý: dùng thông tin có trong bài nhưng không trả lời đúng câu hỏi (con số khác, chi tiết ở đoạn khác). Rải đáp án đúng đều ở A, B, C, D.
- **Số trong bài nghe** (giờ, tiền, năm) đọc rõ, tránh số điện thoại và địa chỉ email dài vì giọng tổng hợp đọc dễ nhầm.
- **Ngôn ngữ:** bài đọc, bài nghe, câu hỏi và đáp án bằng tiếng Anh; giao diện, `topic`, `setting`, `gloss` (nghĩa), `ex` (giải thích) bằng tiếng Việt. `ex` nêu câu bằng chứng trong ngoặc kép “ ” và vì sao đáp án đúng; câu có bẫy thì giải thích luôn bẫy.
- **Trong chuỗi JS** dùng dấu nháy kép ngoài; dấu nháy trong tiếng Anh viết `'` hoặc `’`, tránh `"` bên trong.

## Cập nhật kèm theo

Thêm bài xong cập nhật số bài ở dòng mô tả trong `index.html` (phần `.sub`: “3 bài đọc và 2 bài nghe”) và trong `README.md`. Tiêu đề trang `<title>` giữ nguyên.
