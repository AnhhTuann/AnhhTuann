# 🗺️ Lộ Trình Học Front-End Từ Đầu

> **Dành cho**: Người mới bắt đầu, chưa biết gì về lập trình web.
> **Mục tiêu**: Có thể làm việc như một Junior Front-End Developer.
> **Thời gian ước tính**: 3–5 tháng (nếu học đều đặn mỗi ngày 2–3 tiếng).

---

## 📌 Nguyên tắc học hiệu quả

Trước khi bắt đầu, hãy ghi nhớ 3 nguyên tắc này:

> **1. Đọc 20% – Code 80%**: Đọc lý thuyết xong phải code ngay. Không code = không nhớ.
>
> **2. Hiểu sâu 1 thứ hơn biết nông 10 thứ**: Đừng vội chạy sang chủ đề mới khi chưa hiểu rõ cái đang học.
>
> **3. Build something every day**: Mỗi ngày tạo ra ít nhất 1 thứ nhỏ, dù chỉ là 1 button đẹp.

---

## 🧭 Bản đồ tổng quan

```
Giai đoạn 1       Giai đoạn 2        Giai đoạn 3         Giai đoạn 4
(4 tuần)          (4 tuần)           (4 tuần)            (4 tuần)
   │                  │                  │                   │
HTML & CSS  →   JavaScript  →   Tools & Framework  →  Project & Job
Nền tảng         Lập trình         React + Git            Thực chiến
```

---

## 📅 GIAI ĐOẠN 1 – HTML & CSS (Tuần 1–4)

### 🎯 Mục tiêu giai đoạn
Kết thúc giai đoạn này bạn phải tự làm được một trang web tĩnh **đẹp và responsive** hoàn toàn bằng HTML + CSS.

---

### Tuần 1 – HTML Cơ bản

**Lý thuyết cần học:**
- [ ] HTML là gì? Cấu trúc file HTML cơ bản
- [ ] Các thẻ thông dụng: `div`, `p`, `h1-h6`, `a`, `img`, `ul/ol/li`
- [ ] Semantic HTML: `header`, `nav`, `main`, `section`, `article`, `footer`
- [ ] Form cơ bản: `input`, `button`, `label`, `select`
- [ ] Attribute: `class`, `id`, `href`, `src`, `alt`

**Tài nguyên học:**
- 📖 [MDN HTML Basics](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML)
- 📺 [freeCodeCamp HTML Course (YouTube)](https://www.youtube.com/watch?v=kUMe1FH4CHE)
- 🎮 [HTML Quiz – W3Schools](https://www.w3schools.com/html/html_quiz.asp)

**Bài tập thực hành:**
```
✅ Bài 1: Tạo trang "Giới thiệu bản thân" – có ảnh, tên, bio, danh sách sở thích
✅ Bài 2: Tạo trang "Menu nhà hàng" – dùng bảng hoặc danh sách có hình ảnh
✅ Bài 3: Tạo form đăng ký tài khoản đơn giản
```

**Kiểm tra hiểu bài (tự hỏi):**
> - Sự khác biệt giữa `<div>` và `<section>` là gì?
> - Tại sao phải dùng `alt` cho thẻ `<img>`?
> - `id` khác `class` như thế nào?

---

### Tuần 2 – CSS Cơ bản

**Lý thuyết cần học:**
- [ ] CSS là gì? 3 cách viết CSS (inline, internal, external)
- [ ] Selector: element, class, id, pseudo-class (`:hover`, `:focus`)
- [ ] Colors, fonts, text properties
- [ ] Box Model: content, padding, border, margin
- [ ] `display`: block, inline, inline-block, none
- [ ] `position`: static, relative, absolute, fixed, sticky
- [ ] Đơn vị: `px`, `%`, `em`, `rem`, `vw`, `vh`

**Tài nguyên học:**
- 📖 [MDN CSS First Steps](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps)
- 🎮 [CSS Diner – Luyện Selector](https://flukeout.github.io/)
- 🎮 [CSS Battle – Thách đố CSS](https://cssbattle.dev/)

**Bài tập thực hành:**
```
✅ Bài 1: Style lại trang "Giới thiệu bản thân" từ tuần 1 cho đẹp
✅ Bài 2: Tạo card sản phẩm (ảnh + tên + giá + nút "Mua")
✅ Bài 3: Tạo navigation bar ngang với hiệu ứng hover
```

**Kiểm tra hiểu bài:**
> - `box-sizing: border-box` có nghĩa là gì? Tại sao nên dùng?
> - `position: absolute` định vị theo cái gì?
> - Khi nào dùng `em` thay vì `rem`?

---

### Tuần 3 – CSS Layout (Flexbox + Grid)

**Lý thuyết cần học:**
- [ ] Flexbox: `display: flex`, `justify-content`, `align-items`, `flex-wrap`, `gap`
- [ ] Flexbox items: `flex-grow`, `flex-shrink`, `align-self`, `order`
- [ ] CSS Grid: `display: grid`, `grid-template-columns`, `grid-template-rows`, `gap`
- [ ] Grid items: `grid-column`, `grid-row`, `grid-area`
- [ ] Khi nào dùng Flexbox, khi nào dùng Grid?

**Tài nguyên học:**
- 🎮 [Flexbox Froggy – Học Flexbox bằng game](https://flexboxfroggy.com/)
- 🎮 [Grid Garden – Học Grid bằng game](https://cssgridgarden.com/)
- 📖 [CSS Tricks – Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

**Bài tập thực hành:**
```
✅ Bài 1: Làm layout 3 cột với Flexbox (sidebar + main + sidebar)
✅ Bài 2: Làm grid ảnh giống Pinterest (3–4 cột)
✅ Bài 3: Tạo pricing cards – 3 card nằm ngang, canh giữa trang
```

---

### Tuần 4 – Responsive Design

**Lý thuyết cần học:**
- [ ] Mobile First là gì? Tại sao nên dùng?
- [ ] Viewport meta tag – bắt buộc phải có
- [ ] Media Queries: `@media (min-width: ...)` và `@media (max-width: ...)`
- [ ] Responsive images: `max-width: 100%`, `srcset`
- [ ] Breakpoints phổ biến (sm: 576px, md: 768px, lg: 1024px, xl: 1280px)

**Tài nguyên học:**
- 📖 [MDN Responsive Design](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design)
- 🛠️ [Responsive Checker](https://responsivechecker.net/)

**Bài tập thực hành:**
```
✅ Bài 1: Làm landing page có:
   - Mobile: 1 cột, menu ẩn
   - Tablet: 2 cột
   - Desktop: 3 cột, full navigation
✅ Bài 2: Clone trang web đơn giản bất kỳ (trang giới thiệu công ty, portfolio...)
```

**🏁 Project cuối giai đoạn 1:**
> Clone lại giao diện một trang web thật (VD: trang landing của Notion, Spotify, hoặc bất kỳ trang nào bạn thích). Phải responsive trên cả mobile và desktop.

---

## 📅 GIAI ĐOẠN 2 – JAVASCRIPT (Tuần 5–8)

### 🎯 Mục tiêu giai đoạn
Kết thúc giai đoạn này bạn phải hiểu được JavaScript đủ để làm trang web có **tương tác thật sự** (không chỉ hiển thị tĩnh).

---

### Tuần 5 – JS Cơ bản

**Lý thuyết cần học:**
- [ ] JS là gì? Cách chạy JS trong trình duyệt (Console, `<script>`)
- [ ] Variables: `var`, `let`, `const` – nên dùng cái nào?
- [ ] Kiểu dữ liệu: `string`, `number`, `boolean`, `null`, `undefined`, `array`, `object`
- [ ] Toán tử: `+`, `-`, `*`, `/`, `%`, `===`, `!==`, `&&`, `||`, `!`
- [ ] Câu lệnh điều kiện: `if/else`, `switch`
- [ ] Vòng lặp: `for`, `while`, `for...of`, `for...in`
- [ ] Functions: khai báo, arrow function, parameters, return

**Tài nguyên học:**
- 📖 [javascript.info](https://javascript.info/) – Tốt nhất cho người mới
- 🎮 [freeCodeCamp JS Algorithms](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/)

**Bài tập thực hành:**
```
✅ Bài 1: Viết hàm tính tổng mảng số
✅ Bài 2: Viết hàm kiểm tra số nguyên tố
✅ Bài 3: Viết hàm đảo ngược chuỗi
✅ Bài 4: Viết mini calculator (cộng trừ nhân chia) trong console
```

---

### Tuần 6 – JS Nâng cao + DOM

**Lý thuyết cần học:**
- [ ] Array methods: `map`, `filter`, `reduce`, `find`, `some`, `every`, `includes`
- [ ] Object: tạo object, truy cập property, destructuring
- [ ] Spread/Rest operator: `...`
- [ ] Template literals: `` `Hello ${name}` ``
- [ ] DOM: `querySelector`, `innerHTML`, `textContent`, `classList`
- [ ] Events: `addEventListener`, `click`, `input`, `submit`, `keydown`
- [ ] `e.preventDefault()`, `e.stopPropagation()`

**Bài tập thực hành:**
```
✅ Bài 1: To-do list (thêm, xóa, đánh dấu hoàn thành)
✅ Bài 2: Bộ đếm (counter) với nút tăng/giảm/reset
✅ Bài 3: Form validation (kiểm tra email, mật khẩu trước khi submit)
✅ Bài 4: Filter danh sách sản phẩm theo giá hoặc tên
```

---

### Tuần 7 – Bất đồng bộ (Async JS)

**Lý thuyết cần học:**
- [ ] Callback là gì? Callback hell là gì?
- [ ] Promise: `.then()`, `.catch()`, `.finally()`
- [ ] `async/await` – cú pháp hiện đại, dễ đọc hơn
- [ ] `fetch()` – gọi API lấy dữ liệu
- [ ] Event Loop: Microtask vs Macrotask (hiểu cơ bản)
- [ ] `try/catch` – xử lý lỗi

**Bài tập thực hành:**
```
✅ Bài 1: Gọi API công khai (JSONPlaceholder, OpenWeatherMap...) và hiển thị dữ liệu
✅ Bài 2: Tìm kiếm GitHub user theo username (dùng GitHub API)
✅ Bài 3: Hiển thị danh sách bài viết với loading spinner và xử lý lỗi
```

**API công khai để luyện tập:**
```
https://jsonplaceholder.typicode.com/posts     – Danh sách bài viết
https://api.github.com/users/octocat           – Thông tin GitHub user
https://pokeapi.co/api/v2/pokemon/ditto        – Pokemon API
https://api.unsplash.com/photos                – Ảnh random
```

---

### Tuần 8 – Scope, Closure, OOP & ES6+

**Lý thuyết cần học:**
- [ ] Scope: Global, Function, Block
- [ ] Hoisting: `var` vs `let/const`
- [ ] Closure – hiểu rõ và viết được ví dụ
- [ ] `this` keyword – cách hoạt động trong các ngữ cảnh khác nhau
- [ ] Prototype và Class (ES6)
- [ ] `Optional chaining ?.`, `Nullish coalescing ??`
- [ ] Modules: `import/export`

**Bài tập thực hành:**
```
✅ Bài 1: Viết class `BankAccount` có deposit, withdraw, getBalance
✅ Bài 2: Viết hàm `createCounter` dùng closure
✅ Bài 3: Đoán output các đoạn code liên quan đến scope và hoisting
```

**🏁 Project cuối giai đoạn 2:**
> Làm **Weather App**: nhập tên thành phố → gọi API → hiển thị thời tiết + nhiệt độ + icon. Có xử lý loading và lỗi.

---

## 📅 GIAI ĐOẠN 3 – TOOLS & REACT (Tuần 9–12)

### 🎯 Mục tiêu giai đoạn
Làm quen với hệ sinh thái hiện đại: Git để quản lý code, React để xây dựng UI theo component.

---

### Tuần 9 – Git & Command Line

**Lý thuyết cần học:**
- [ ] Terminal/Command line cơ bản: `cd`, `ls`, `mkdir`, `touch`
- [ ] Git init, clone, add, commit, push, pull
- [ ] Branch: tạo, chuyển, merge
- [ ] GitHub: tạo repo, push code, tạo Pull Request
- [ ] `.gitignore`

**Bài tập thực hành:**
```
✅ Bài 1: Tạo GitHub account và push project Weather App lên
✅ Bài 2: Tạo nhánh feature, sửa code, merge vào main
✅ Bài 3: Tạo Pull Request và review code của chính mình
```

---

### Tuần 10 – React Cơ bản

**Lý thuyết cần học:**
- [ ] React là gì? Tại sao dùng React? Virtual DOM là gì?
- [ ] Setup: `npm create vite@latest` với React template
- [ ] JSX: viết HTML trong JS
- [ ] Components: Function component
- [ ] Props: truyền dữ liệu từ cha xuống con
- [ ] `useState`: quản lý state nội bộ
- [ ] Render list: `array.map()` + `key` prop

**Tài nguyên học:**
- 📖 [React.dev (Official Docs)](https://react.dev/learn) – Mới nhất, tốt nhất
- 📺 [React Tutorial – Kevin Powell (YouTube)](https://www.youtube.com/results?search_query=react+tutorial+beginners+2024)

**Bài tập thực hành:**
```
✅ Bài 1: Chuyển To-do list thuần JS sang React
✅ Bài 2: Tạo danh sách sản phẩm (product card list) với dữ liệu giả
✅ Bài 3: Tạo counter với nút tăng/giảm dùng useState
```

---

### Tuần 11 – React Nâng cao

**Lý thuyết cần học:**
- [ ] `useEffect`: xử lý side effects, gọi API
- [ ] `useRef`: tham chiếu đến DOM element
- [ ] `useCallback` và `useMemo`: tối ưu performance
- [ ] Lifting state up: chia sẻ state giữa các component
- [ ] Component composition
- [ ] Conditional rendering
- [ ] Forms trong React: controlled components

**Bài tập thực hành:**
```
✅ Bài 1: Chuyển Weather App sang React
✅ Bài 2: Tạo search + filter list với useEffect
✅ Bài 3: Tạo form đăng nhập với validation
```

---

### Tuần 12 – Routing, TypeScript & Tooling

**Lý thuyết cần học:**
- [ ] React Router: `BrowserRouter`, `Route`, `Link`, `useParams`, `useNavigate`
- [ ] TypeScript cơ bản: types, interfaces, props typing
- [ ] npm/pnpm: cách quản lý packages
- [ ] Vite: build tool, cách cấu hình cơ bản
- [ ] Tailwind CSS (tùy chọn): utility-first CSS

**Bài tập thực hành:**
```
✅ Bài 1: Tạo app có nhiều trang dùng React Router (Home, About, Products, Detail)
✅ Bài 2: Convert component sang TypeScript
```

**🏁 Project cuối giai đoạn 3:**
> Làm **Movie/Book Finder App**: tìm kiếm phim/sách qua API → hiển thị kết quả → click vào xem chi tiết (nhiều trang dùng React Router). Có TypeScript.

---

## 📅 GIAI ĐOẠN 4 – PROJECT & JOB (Tuần 13–16)

### 🎯 Mục tiêu giai đoạn
Có portfolio đủ để xin việc Junior Front-End Developer.

---

### Tuần 13–14 – Portfolio Project

Làm **1 project lớn thật sự** để đưa vào portfolio. Gợi ý:

| Project | Độ khó | Công nghệ |
|---|---|---|
| **E-commerce mini** (danh sách sản phẩm, giỏ hàng) | ⭐⭐⭐ | React, Context API, React Router |
| **Blog platform** (đọc bài, tìm kiếm, filter tag) | ⭐⭐⭐ | React, TypeScript, API |
| **Dashboard quản lý** (chart, table, filter) | ⭐⭐⭐⭐ | React, Chart.js hoặc Recharts |
| **Social feed** (posts, like, comment, infinite scroll) | ⭐⭐⭐⭐ | React, TanStack Query |

**Yêu cầu bắt buộc của project:**
```
✅ Code sạch, chia component rõ ràng
✅ Responsive trên mobile và desktop
✅ Dùng Git đúng cách (commit thường xuyên, message rõ nghĩa)
✅ Deploy lên Vercel hoặc Netlify (miễn phí)
✅ README.md đầy đủ: mô tả project, cách chạy, screenshot
```

---

### Tuần 15 – Ôn tập phỏng vấn

**Lý thuyết cần ôn:**
- [ ] HTML: semantic, accessibility, SEO cơ bản
- [ ] CSS: specificity, box model, flexbox vs grid, responsive
- [ ] JS: closure, this, promise, event loop
- [ ] React: virtual DOM, hooks, lifecycle, state management
- [ ] Git: merge vs rebase, gitflow

**Thực hành:**
```
✅ Giải các câu hỏi trong file frontend_full_notes_vi.md – Mục 14
✅ Làm 5–10 bài coding trên leetcode.com (Easy level)
✅ Mock interview với bạn bè hoặc tự nói to câu trả lời
```

---

### Tuần 16 – Apply Job

**Chuẩn bị:**
- [ ] CV / Resume (1 trang, tiếng Anh hoặc tiếng Việt tùy công ty)
- [ ] LinkedIn profile đầy đủ
- [ ] GitHub profile: có ảnh, bio, pinned repos
- [ ] Portfolio website (nếu có) deploy lên Vercel

**Nơi tìm việc:**
- ITViec, TopDev (Việt Nam)
- LinkedIn Jobs
- Vietnamworks
- Built In (nước ngoài)

---

## 🛠️ Công cụ cần cài đặt

```bash
# Editor
Visual Studio Code – https://code.visualstudio.com/

# Extensions VS Code cần thiết
- Prettier (format code tự động)
- ESLint (phát hiện lỗi)
- GitLens (xem lịch sử git ngay trong editor)
- Auto Rename Tag
- Live Server (xem HTML thay đổi real-time)

# Node.js (cần cho npm và các tool JS)
https://nodejs.org/ – Tải bản LTS

# Git
https://git-scm.com/

# Trình duyệt
Google Chrome – DevTools rất mạnh
```

---

## 📚 Tài nguyên học miễn phí hay nhất

| Tên | Loại | Link |
|---|---|---|
| **MDN Web Docs** | Tài liệu | [developer.mozilla.org](https://developer.mozilla.org) |
| **javascript.info** | Khóa học | [javascript.info](https://javascript.info) |
| **react.dev** | Tài liệu React | [react.dev](https://react.dev) |
| **freeCodeCamp** | Khóa học + Chứng chỉ | [freecodecamp.org](https://freecodecamp.org) |
| **The Odin Project** | Lộ trình full | [theodinproject.com](https://www.theodinproject.com) |
| **Frontend Mentor** | Bài tập thực tế | [frontendmentor.io](https://frontendmentor.io) |
| **CSS Tricks** | Bài viết CSS | [css-tricks.com](https://css-tricks.com) |
| **Flexbox Froggy** | Game CSS | [flexboxfroggy.com](https://flexboxfroggy.com) |
| **Grid Garden** | Game CSS | [cssgridgarden.com](https://cssgridgarden.com) |
| **TypeScript Docs** | Tài liệu TS | [typescriptlang.org](https://www.typescriptlang.org/docs/) |

---

## ✅ Checklist cuối cùng trước khi xin việc

```
Kỹ năng kỹ thuật:
□ Viết được HTML semantic, không chỉ dùng div
□ CSS responsive không cần framework
□ Flexbox và Grid thành thạo
□ JavaScript ES6+ thoải mái
□ Gọi API bằng fetch/async-await
□ React: hooks, component, state, props
□ TypeScript cơ bản
□ Git: commit, branch, merge, push/pull

Portfolio:
□ Ít nhất 2–3 project có thể show
□ Tất cả đều deploy lên internet (Vercel/Netlify)
□ Code lên GitHub public
□ README đầy đủ

Mềm:
□ Có thể giải thích code của mình cho người khác
□ Biết cách Google và đọc documentation
□ Không sợ đọc thông báo lỗi (error message)
```

---

## 💬 Lời khuyên cuối

> Lập trình không cần thiên tài. Chỉ cần **kiên trì mỗi ngày**.
>
> Ngày nào cũng code – dù chỉ 30 phút – tốt hơn 10 tiếng 1 ngày rồi bỏ 1 tuần.
>
> **Stuck là bình thường.** Google, đọc docs, hỏi AI, hỏi cộng đồng – đó là kỹ năng quan trọng nhất của lập trình viên.

---

*📁 File tài liệu tham khảo đi kèm: `frontend_full_notes_vi.md` và `frontend_full_notes_en.md`*
