# 💻 Tiếng Anh IT (Technical English)

> ← [Quay lại mục lục](README.md)

---

## 1. Giải Thích Code Bằng Tiếng Anh

### Mô tả function
```
Template:
"This function takes [input] as a parameter and returns [output].
It first checks if [condition], then [does action].
If the condition is not met, it [alternative action]."

Ví dụ thực tế:
"This function takes a user ID as a parameter and returns 
a promise that resolves to the user object.
It first checks if the ID is valid, then fetches the data from the API.
If the ID is invalid, it throws an error."
```

### Giải thích bug
```
Template:
"I found a bug in the [component/function].
When [condition], the app [unexpected behavior].
The root cause is [explanation].
My fix is to [solution]."

Ví dụ:
"I found a bug in the LoginForm component.
When the user submits with an empty email field,
the app crashes instead of showing a validation error.
The root cause is a missing null check.
My fix is to add form validation before the API call."
```

### Mô tả pull request
```
"This PR [adds/fixes/refactors] [what].

Changes made:
- [change 1]
- [change 2]

How to test:
1. [step 1]
2. [step 2]

Related ticket: #[number]"
```

---

## 2. Phỏng Vấn Technical

### Khi Bắt Đầu Giải Bài
```
"Let me think about this for a moment..."
"I'll start by clarifying the requirements..."
"My initial approach would be..."
"Before I start coding, let me ask a few questions..."

Câu hỏi làm rõ:
"Can I assume the input is always valid?"
"What should I return if the input is empty?"
"Is there a time or space complexity requirement?"
```

### Trong Quá Trình Giải
```
"I'm thinking of using X because..."
"This has a time complexity of O(n)..."
"An edge case I need to handle is..."
"I could optimize this by..."
"Let me trace through this example..."
"This approach trades [X] for [Y]..."
```

### Kết Thúc
```
"To summarize my approach..."
"The trade-off of this solution is..."
"Given more time, I would also..."
"I could improve this by..."
```

---

## 3. Behavioral Questions — Phương Pháp STAR

Dùng cho các câu hỏi về kinh nghiệm và hành vi.

```
S — Situation (Bối cảnh):
"In my previous project, we had..."

T — Task (Nhiệm vụ):
"My responsibility was to..."

A — Action (Hành động):
"I decided to... / I took the approach of..."

R — Result (Kết quả):
"As a result, we achieved... / The outcome was..."
```

### Câu Hỏi Thường Gặp + Cách Trả Lời

| Câu Hỏi | Điểm Cần Nêu |
|---|---|
| "Tell me about yourself." | Background → Skills → Goals (1–2 phút) |
| "Why do you want this job?" | Research về company + Fit cá nhân |
| "What's your greatest strength?" | 1 kỹ năng cụ thể + ví dụ thực tế |
| "What's your weakness?" | Điểm yếu thật + Cách đang cải thiện |
| "Describe a challenging project." | STAR method đầy đủ |
| "Tell me about a conflict at work." | STAR + nhấn mạnh giải quyết được |
| "Where do you see yourself in 5 years?" | Growth + Commitment với công ty |
| "Why are you leaving your current job?" | Positive framing, không nói xấu |

### Ví Dụ STAR Hoàn Chỉnh

**Câu hỏi:** "Tell me about a time you solved a difficult technical problem."

```
S: "In my last project, we had a performance issue where the 
    homepage took 8 seconds to load, which was causing a 40% 
    bounce rate."

T: "I was responsible for identifying the bottleneck and 
    improving the load time to under 2 seconds."

A: "I started by running a Lighthouse audit and found that 
    the main issue was unoptimized images and blocking JavaScript.
    I implemented lazy loading for images, used code splitting 
    to defer non-critical JS, and added a CDN for static assets."

R: "As a result, the load time dropped from 8 seconds to 1.4 seconds.
    The bounce rate decreased by 25%, and the client reported 
    a 15% increase in conversions over the next month."
```

---

## 4. Tiếng Anh Trong Môi Trường Làm Việc

### Daily Standup
```
"Yesterday I worked on [task]."
"Today I'm planning to [task]."
"I'm blocked by [issue] — I need help with [specific thing]."
```

### Code Review Comments
```
Khen ngợi:    "Nice approach! / Clean implementation."
Gợi ý nhẹ:   "Consider using X here — it might be cleaner."
Yêu cầu đổi: "This needs to be changed because..."
Hỏi:          "Can you explain why you chose this over Y?"
Chặn merge:   "This is a blocker — we need to fix [issue] first."
```

### Họp Team
```
Đề xuất:    "I'd like to suggest..."
Đồng ý:     "That makes sense. / I'm on board with that."
Không đồng ý: "I have a concern about... / I'd push back on that."
Tóm tắt:    "So to summarize what we've agreed on..."
Kết thúc:   "Let's take this offline." / "Let's sync up later."
```

---

> **Tiếp theo:** [⚒️ Tools & Lịch Học →](08_tools_lich_hoc.md)  
> **Quay lại:** [← Đọc & Viết](06_doc_va_viet.md)
