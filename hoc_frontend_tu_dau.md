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
- [ ] React là gì? Tại sao dùng React? Virtual DOM hoạt động thế nào?
- [ ] Setup project: `npm create vite@latest my-app -- --template react`
- [ ] Cấu trúc thư mục React project
- [ ] JSX: quy tắc, className, self-closing, expression `{}`
- [ ] Function Component: viết và export đúng cách
- [ ] Props: truyền xuống, destructuring, default value
- [ ] `useState`: giá trị ban đầu, functional update, object/array state
- [ ] Render list: `array.map()` + `key` prop (tại sao key quan trọng?)
- [ ] Conditional rendering: ternary `? :` và `&&`

**Tài nguyên học:**
- 📖 [React.dev – Learn React](https://react.dev/learn) – Tốt nhất, có interactive
- 📖 [reactjs_full_notes_vi.md](reactjs_full_notes_vi.md) – File ghi chú chi tiết
- 📺 [Scrimba – Learn React for free](https://scrimba.com/learn/learnreact)

**Bài tập thực hành:**
```
✅ Bài 1: Chuyển To-do list thuần JS sang React (thêm, xóa, đánh dấu done)
✅ Bài 2: Tạo ProductCard component – nhận props: name, price, image, onAddToCart
✅ Bài 3: Tạo Counter với useState – nút +/–/reset, không cho âm
✅ Bài 4: Render danh sách 10 user từ mảng JSON giả (mock data)
```

**Kiểm tra hiểu bài:**
> - `key` prop trong list là gì? Tại sao không nên dùng index?
> - Props khác State ở chỗ nào?
> - Tại sao không được mutate state trực tiếp (`state.count = 1`)?

---

### Tuần 11 – React Nâng cao (Hooks)

**Lý thuyết cần học:**
- [ ] `useEffect`: 4 pattern (run always / once / on dep change / cleanup)
- [ ] Gọi API trong useEffect: async/await, loading state, error state
- [ ] Race condition là gì? Cách fix bằng cleanup function
- [ ] `useRef`: truy cập DOM, lưu giá trị không trigger re-render
- [ ] `useContext`: chia sẻ state không cần prop drilling
- [ ] `useReducer`: thay useState khi logic phức tạp
- [ ] `useMemo`: cache kết quả tính toán nặng
- [ ] `useCallback`: cache function reference cho React.memo
- [ ] `React.memo`: tránh re-render không cần thiết
- [ ] Controlled vs Uncontrolled Form
- [ ] Lifting state up: chia sẻ state giữa sibling components
- [ ] Custom Hook: tách logic tái sử dụng (`useFetch`, `useLocalStorage`)

**Bài tập thực hành:**
```
✅ Bài 1: Chuyển Weather App sang React + gọi API thật + loading/error state
✅ Bài 2: Tạo search + filter list dùng useEffect + useMemo
✅ Bài 3: Tạo form đăng nhập: validation, controlled input, submit handler
✅ Bài 4: Viết Custom Hook useFetch(url) tái sử dụng được
✅ Bài 5: Dark/Light mode toggle dùng useContext
```

**Kiểm tra hiểu bài:**
> - `useEffect` với `[]` khác gì với không có dependency array?
> - Stale closure trong useEffect là gì?
> - Khi nào nên dùng `useReducer` thay `useState`?

---

### Tuần 12 – React Router, State Management & Tooling

**Lý thuyết cần học:**

**React Router v6:**
- [ ] `BrowserRouter`, `Routes`, `Route`, `Link`, `NavLink`
- [ ] `useParams` – lấy `:id` từ URL
- [ ] `useNavigate` – chuyển trang bằng code
- [ ] `useSearchParams` – đọc query string
- [ ] Protected Route – chặn trang khi chưa đăng nhập
- [ ] Nested routes, layout route

**State Management:**
- [ ] Zustand (đơn giản): `create`, `set`, `get` – khuyến nghị cho dự án vừa
- [ ] Context API – dùng cho theme, auth
- [ ] Redux Toolkit (cơ bản) – `createSlice`, `configureStore`, `useSelector`, `useDispatch`

**Tooling:**
- [ ] TypeScript cơ bản: `type`, `interface`, props typing với `React.FC`
- [ ] Vite: `npm run dev`, `npm run build`, env variables
- [ ] ESLint + Prettier: cấu hình cơ bản
- [ ] React DevTools (browser extension) – debug component tree

**Bài tập thực hành:**
```
✅ Bài 1: Multi-page app: Home / Products / Product Detail / Cart (React Router)
✅ Bài 2: Giỏ hàng với Zustand (thêm, xóa, tính tổng)
✅ Bài 3: Convert 1 component sang TypeScript đầy đủ
✅ Bài 4: Thêm Protected Route – redirect nếu chưa login
```

**🏁 Project cuối giai đoạn 3:**
> Làm **Movie/Book Finder App**: tìm kiếm qua API → hiển thị kết quả dạng grid → click xem chi tiết → bookmark bằng Zustand → nhiều trang React Router. Có TypeScript + deploy Vercel.

---

## 📅 GIAI ĐOẠN 3.5 – REACT CHUYÊN SÂU (Tùy chọn — nên học trước khi xin việc)

> Nếu bạn muốn làm **Senior Junior** hoặc nhắm công ty có dự án React lớn, hãy học thêm phần này sau khi xong Giai đoạn 3.

---

### 🔥 React Performance

**Lý thuyết:**
- [ ] `React.memo` + `useCallback` kết hợp đúng cách
- [ ] `useMemo` cho tính toán nặng
- [ ] Code Splitting + `React.lazy` + `Suspense`
- [ ] Virtualization – `react-window` cho list dài (1000+ items)
- [ ] React DevTools Profiler – đo render time
- [ ] Tránh re-render không cần thiết: state placement, component split

**Bài tập:**
```
✅ Dùng Profiler đo render time của to-do list 500 items
✅ Implement react-window cho list 1000 items
✅ Lazy load từng trang trong React Router
```

---

### 🌐 Data Fetching Hiện Đại

**Lý thuyết:**
- [ ] TanStack Query (React Query): `useQuery`, `useMutation`, `invalidateQueries`
- [ ] Tại sao dùng React Query thay `useEffect + fetch`?
- [ ] Cache, staleTime, refetchOnWindowFocus
- [ ] Optimistic Update – cập nhật UI trước, rollback nếu lỗi
- [ ] Axios: `axios.create`, interceptor, error handling

**Bài tập:**
```
✅ Chuyển Weather App từ useEffect sang useQuery
✅ CRUD đơn giản với useMutation + invalidateQueries
✅ Thêm Optimistic Update cho nút Like
```

---

### 🏗️ Architecture & Patterns

**Lý thuyết:**
- [ ] Cấu trúc thư mục chuẩn: `features/`, `components/`, `hooks/`, `services/`
- [ ] Compound Component Pattern
- [ ] Render Props Pattern
- [ ] HOC (Higher-Order Component)
- [ ] Error Boundary – bắt lỗi trong component tree
- [ ] Suspense cho data fetching

**Bài tập:**
```
✅ Tái cấu trúc Movie App theo features/ pattern
✅ Viết ErrorBoundary bọc toàn bộ app
✅ Tạo Modal component dùng Compound Pattern
```

---

### 🧪 Testing React

**Lý thuyết:**
- [ ] React Testing Library: `render`, `screen`, `userEvent`
- [ ] Query: `getByRole`, `getByText`, `findByText` (async)
- [ ] Mock fetch/API trong test
- [ ] Nguyên tắc: test hành vi user, không test implementation

**Bài tập:**
```
✅ Viết test cho Counter component
✅ Viết test cho Form component (validation)
✅ Viết test async cho UserList (mock fetch)
```

---

### 🚀 Next.js (Framework React Phổ Biến Nhất)

**Lý thuyết:**
- [ ] Next.js là gì? SSR vs CSR vs SSG vs ISR
- [ ] App Router (Next.js 13+): `app/`, `page.tsx`, `layout.tsx`
- [ ] Server Component vs Client Component
- [ ] `fetch` trong Server Component (tự cache)
- [ ] `loading.tsx`, `error.tsx`, `not-found.tsx`
- [ ] Image optimization: `next/image`
- [ ] Deploy lên Vercel (1 click)

**Bài tập:**
```
✅ Tạo blog đơn giản với Next.js App Router
✅ Fetch data từ API trong Server Component
✅ Deploy lên Vercel
```

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
- [ ] JS: closure, this, promise, event loop, scope, hoisting
- [ ] React: Virtual DOM, Reconciliation, hooks, lifecycle, state management
- [ ] React: `memo`, `useMemo`, `useCallback` – khác nhau chỗ nào?
- [ ] React: Controlled vs Uncontrolled, Prop Drilling, Context
- [ ] Git: merge vs rebase, gitflow

**Thực hành:**
```
✅ Ôn câu hỏi trong file frontend_interview_questions_vi.md
✅ Ôn kiến thức trong reactjs_full_notes_vi.md – Mục 20 (Interview Q&A)
✅ Làm 5–10 bài coding trên leetcode.com (Easy level)
✅ Mock interview: tự nói to câu trả lời, ghi âm, nghe lại
✅ Giải thích Virtual DOM và useEffect cho người không biết React
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
| **javascript.info** | Khóa học JS | [javascript.info](https://javascript.info) |
| **react.dev** | Tài liệu React chính thức | [react.dev](https://react.dev) |
| **freeCodeCamp** | Khóa học + Chứng chỉ | [freecodecamp.org](https://freecodecamp.org) |
| **The Odin Project** | Lộ trình full | [theodinproject.com](https://www.theodinproject.com) |
| **Frontend Mentor** | Bài tập thực tế | [frontendmentor.io](https://frontendmentor.io) |
| **CSS Tricks** | Bài viết CSS | [css-tricks.com](https://css-tricks.com) |
| **Flexbox Froggy** | Game CSS | [flexboxfroggy.com](https://flexboxfroggy.com) |
| **Grid Garden** | Game CSS | [cssgridgarden.com](https://cssgridgarden.com) |
| **TypeScript Docs** | Tài liệu TS | [typescriptlang.org](https://www.typescriptlang.org/docs/) |
| **TanStack Query Docs** | Data fetching | [tanstack.com/query](https://tanstack.com/query/latest) |
| **Zustand Docs** | State management | [zustand-demo.pmnd.rs](https://zustand-demo.pmnd.rs/) |
| **React Router Docs** | Routing | [reactrouter.com](https://reactrouter.com/) |
| **Next.js Docs** | Full-stack React | [nextjs.org/docs](https://nextjs.org/docs) |
| **Testing Library** | Testing React | [testing-library.com](https://testing-library.com/docs/react-testing-library/intro/) |

---

## ✅ Checklist cuối cùng trước khi xin việc

```
Kỹ năng kỹ thuật:
□ Viết được HTML semantic, không chỉ dùng div
□ CSS responsive không cần framework
□ Flexbox và Grid thành thạo
□ JavaScript ES6+ thoải mái (closure, promise, async/await)
□ Gọi API bằng fetch/async-await, xử lý loading + error
□ React: JSX, component, props, state (useState)
□ React Hooks: useEffect, useRef, useContext, useCallback, useMemo
□ React Router: điều hướng nhiều trang, dynamic route
□ State Management: Zustand hoặc Context API
□ TypeScript cơ bản: type, interface, props typing
□ Git: commit, branch, merge, pull request, gitflow

React nâng cao (bonus):
□ Custom Hooks: useFetch, useLocalStorage, useDebounce
□ React Query / TanStack Query
□ React.memo + useCallback kết hợp đúng
□ Code splitting với React.lazy + Suspense
□ Error Boundary
□ Biết cơ bản về Next.js

Portfolio:
□ Ít nhất 2–3 project React có thể show
□ Tất cả đều deploy lên Vercel/Netlify
□ Code lên GitHub public với README đầy đủ
□ Ít nhất 1 project dùng API thật + đa trang

Mềm:
□ Giải thích được Virtual DOM và tại sao React nhanh
□ Giải thích được useEffect cleanup và stale closure
□ Biết cách Google và đọc documentation tiếng Anh
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

*📁 Tài liệu tham khảo đi kèm:*
- *[frontend_full_notes_vi.md](frontend_full_notes_vi.md) / [frontend_full_notes_en.md](frontend_full_notes_en.md)*
- *[reactjs_full_notes_vi.md](reactjs_full_notes_vi.md) / [reactjs_full_notes_en.md](reactjs_full_notes_en.md)*
- *[frontend_interview_questions_vi.md](frontend_interview_questions_vi.md) / [frontend_interview_questions_en.md](frontend_interview_questions_en.md)*
