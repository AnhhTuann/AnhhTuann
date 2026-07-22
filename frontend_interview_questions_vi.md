# 🎯 Câu Hỏi Phỏng Vấn Front-End – Đầy Đủ & Thực Chiến

> **Cách dùng:** Mỗi câu hỏi có phần **Câu hỏi**, **Trả lời nhanh (TL;DR)** và **Giải thích chi tiết**. Luyện trả lời phần TL;DR trước, sau đó bổ sung chi tiết khi PV hỏi thêm.

---

## 📌 MỤC LỤC
1. [GIT](#1-git)
2. [HTML](#2-html)
3. [CSS](#3-css)
4. [CSS Layout (Flexbox & Grid)](#4-css-layout)
5. [Responsive Design](#5-responsive-design)
6. [JavaScript Cơ Bản](#6-javascript-cơ-bản)
7. [JavaScript Nâng Cao](#7-javascript-nâng-cao)
8. [TypeScript](#8-typescript)
9. [Web Tổng Quát (CORS, HTTP, Browser)](#9-web-tổng-quát)
10. [React](#10-react)
11. [Công Cụ & Hệ Sinh Thái](#11-công-cụ--hệ-sinh-thái)
12. [Câu Hỏi Tình Huống (Scenario)](#12-câu-hỏi-tình-huống)
13. [Bài Tập Code Trực Tiếp](#13-bài-tập-code-trực-tiếp)

---

## 1. GIT

### ❓ Git là gì? Git và GitHub khác nhau như thế nào?
> **TL;DR:** Git là hệ thống quản lý phiên bản (VCS) chạy local. GitHub là nơi lưu trữ repo Git trên cloud.

**Chi tiết:**
- Git theo dõi toàn bộ lịch sử thay đổi code theo thời gian, cho phép quay lui, so sánh, phân nhánh.
- GitHub (/ GitLab / Bitbucket) là dịch vụ hosting + công cụ cộng tác (Pull Request, CI/CD...).

---

### ❓ 3 vùng của Git là gì? Giải thích flow làm việc cơ bản.
> **TL;DR:** Working Directory → `git add` → Staging Area → `git commit` → Repository.

| Vùng | Vai trò |
|---|---|
| **Working Directory** | File đang chỉnh sửa |
| **Staging Area** | Chọn thay đổi nào sẽ đưa vào commit |
| **Repository** | Lịch sử commit đã lưu |

---

### ❓ Merge vs Rebase – Khi nào dùng cái nào?
> **TL;DR:** Merge an toàn cho team vì giữ lịch sử thật. Rebase làm lịch sử sạch hơn nhưng **không rebase branch đã push chung**.

| | Merge | Rebase |
|---|---|---|
| **Lịch sử** | Giữ nguyên, tạo thêm merge commit | Viết lại, lịch sử thẳng |
| **An toàn** | ✅ Dùng được trên shared branch | ⚠️ Nguy hiểm nếu branch đã push |
| **Dùng khi** | Gộp feature vào `main` | Cập nhật feature branch từ `develop` |

---

### ❓ Reset vs Revert – Sự khác biệt?
> **TL;DR:** `reset` thay đổi lịch sử (dùng local). `revert` tạo commit mới để undo (an toàn cho shared repo).

```bash
# Reset: quay về commit cũ
git reset --soft HEAD~1    # Giữ code + staging
git reset --mixed HEAD~1   # Giữ code, bỏ staging
git reset --hard HEAD~1    # Xóa cả code

# Revert: tạo commit mới đảo ngược commit chỉ định
git revert <commit-hash>
```

---

### ❓ GitFlow là gì? Giải thích 5 loại branch.
> **TL;DR:** Quy trình quản lý branch chuẩn với 5 loại: `main`, `develop`, `feature/*`, `release/*`, `hotfix/*`.

| Branch | Vai trò |
|---|---|
| `main` | Production đang live |
| `develop` | Code đang phát triển |
| `feature/*` | Tính năng mới |
| `release/*` | Chuẩn bị release, fix bug nhỏ |
| `hotfix/*` | Sửa lỗi khẩn cấp trên production |

---

### ❓ `git stash` dùng khi nào?
> **TL;DR:** Khi cần chuyển nhánh gấp mà code đang dang dở, chưa sẵn sàng commit.

```bash
git stash          # Lưu tạm thay đổi
git checkout other-branch
# Làm việc...
git checkout original-branch
git stash pop      # Lấy lại code đã stash
```

---

### ❓ `git cherry-pick` là gì?
> **TL;DR:** Áp dụng một commit cụ thể từ nhánh khác vào nhánh hiện tại, không merge toàn bộ nhánh.

```bash
git cherry-pick <commit-hash>
```
**Use case:** Hotfix ở `develop` cần đưa ngay lên `main` mà không muốn merge hết.

---

## 2. HTML

### ❓ DOCTYPE là gì? Tại sao cần khai báo?
> **TL;DR:** Khai báo phiên bản HTML cho trình duyệt. Không có DOCTYPE → trình duyệt vào **quirks mode**, render sai.

```html
<!DOCTYPE html>  <!-- Bắt buộc ở dòng đầu tiên -->
```

---

### ❓ Semantic HTML là gì? Tại sao quan trọng?
> **TL;DR:** Dùng thẻ có ý nghĩa (`<header>`, `<nav>`, `<main>`...) thay vì `<div>` chung chung. Quan trọng vì: **SEO tốt hơn** và **Accessibility tốt hơn**.

| Thẻ | Vai trò |
|---|---|
| `<header>` | Phần đầu trang / section |
| `<nav>` | Điều hướng chính |
| `<main>` | Nội dung chính (duy nhất 1/page) |
| `<section>` | Nhóm nội dung có chủ đề |
| `<article>` | Nội dung độc lập (bài blog, card) |
| `<aside>` | Nội dung phụ (sidebar) |
| `<footer>` | Phần cuối trang |

---

### ❓ Block vs Inline vs Inline-block – Khác nhau như thế nào?
> **TL;DR:** Block chiếm full ngang, Inline chỉ chiếm chỗ cần, Inline-block = Inline nhưng set được width/height.

| Loại | Xuống dòng | Set width/height | Ví dụ |
|---|---|---|---|
| Block | ✅ | ✅ | `div`, `p`, `h1` |
| Inline | ❌ | ❌ | `span`, `a`, `strong` |
| Inline-block | ❌ | ✅ | `button`, `input`, `img` |

---

### ❓ Form: `readonly` vs `disabled` khác nhau thế nào?
> **TL;DR:** `readonly` không sửa được nhưng **vẫn submit**. `disabled` không focus, không submit.

---

### ❓ `localStorage` vs `sessionStorage` vs `Cookie` – Dùng cái nào khi nào?
> **TL;DR:** localStorage vĩnh viễn ~5MB. sessionStorage mất khi đóng tab. Cookie nhỏ (4KB), tự động gửi lên server, có thể set expiry.

| | localStorage | sessionStorage | Cookie |
|---|---|---|---|
| **Dung lượng** | ~5MB | ~5MB | ~4KB |
| **Thời gian** | Vĩnh viễn | Đóng tab là mất | Có thể set expiry |
| **Gửi server** | ❌ | ❌ | ✅ Tự động |
| **Dùng khi** | Cài đặt, theme | Tab-scoped state | Auth token, session |

---

### ❓ Web Accessibility (A11y) – Làm thế nào để website accessible?
> **TL;DR:** Dùng Semantic HTML, alt text, keyboard navigation, đủ contrast màu, ARIA khi cần.

- **Color contrast**: Tối thiểu 4.5:1 (WCAG AA)
- **Alt text**: Ảnh thông tin → mô tả ngắn. Ảnh trang trí → `alt=""`
- **Keyboard**: Mọi tính năng phải dùng được bằng Tab/Enter/Space/Escape
- **tabindex**: `0` (vào luồng tab tự nhiên), `-1` (chỉ focus bằng JS)
- **ARIA**: `aria-label`, `aria-live` cung cấp ngữ nghĩa cho screen reader

---

## 3. CSS

### ❓ Specificity (Độ ưu tiên) CSS hoạt động như thế nào?
> **TL;DR:** `!important` > Inline style > ID > Class/Pseudo-class > Element.

```
!important > inline (1,0,0,0) > ID (0,1,0,0) > Class (0,0,1,0) > Element (0,0,0,1)
```
> ⚠️ **Tránh dùng `!important`** – rất khó override về sau. Tránh dùng `#id` để style.

---

### ❓ Box Model là gì? `content-box` vs `border-box`?
> **TL;DR:** Mọi element là 1 box: Content → Padding → Border → Margin. `border-box` làm width bao gồm padding + border → dễ tính toán hơn.

```css
/* Khuyên dùng border-box cho toàn trang */
*, *::before, *::after {
  box-sizing: border-box;
}
```

---

### ❓ `display: none` vs `visibility: hidden` – Khác nhau thế nào?
> **TL;DR:** `none` xóa khỏi layout, không chiếm chỗ. `hidden` ẩn nhưng **vẫn chiếm chỗ trong layout**.

| | display: none | visibility: hidden | opacity: 0 |
|---|---|---|---|
| Chiếm chỗ | ❌ | ✅ | ✅ |
| Click được | ❌ | ❌ | ✅ |
| Accessible | ❌ | ❌ | ✅ |

---

### ❓ Position: `relative` vs `absolute` vs `fixed` vs `sticky`?
> **TL;DR:** relative: dịch từ vị trí gốc. absolute: theo cha có position. fixed: theo viewport. sticky: kết hợp relative + fixed khi scroll.

| Giá trị | Tham chiếu | Chiếm chỗ trong flow |
|---|---|---|
| `static` | Luồng bình thường | ✅ |
| `relative` | Vị trí gốc của chính nó | ✅ |
| `absolute` | Cha gần nhất có position ≠ static | ❌ |
| `fixed` | Viewport (cửa sổ trình duyệt) | ❌ |
| `sticky` | Cha (cho đến khi scroll đến threshold) | ✅ |

---

### ❓ `em` vs `rem` – Dùng cái nào?
> **TL;DR:** `rem` an toàn hơn – luôn tính từ root `<html>`, không bị ảnh hưởng bởi nesting như `em`.

```css
html { font-size: 16px; }
.parent { font-size: 20px; }
.child-em  { font-size: 1.5em; }  /* 20 × 1.5 = 30px – phụ thuộc cha */
.child-rem { font-size: 1.5rem; } /* 16 × 1.5 = 24px – luôn từ root */
```

---

### ❓ Stacking Context (Z-index) – Khi nào z-index không hoạt động?
> **TL;DR:** Z-index chỉ so sánh **trong cùng stacking context**. Nếu z-index không chạy, kiểm tra phần tử cha có tạo stacking context mới không.

**Các trường hợp tạo stacking context mới:**
- `position` + `z-index` khác `auto`
- `opacity < 1`
- `transform`, `filter`, `clip-path`

---

### ❓ Margin Collapsing là gì?
> **TL;DR:** Khi hai phần tử block có margin top/bottom gần nhau, chúng **gộp lại** lấy giá trị lớn hơn thay vì cộng dồn.

```css
/* Hai div đều có margin: 20px → không phải 40px mà chỉ 20px */
.box1 { margin-bottom: 20px; }
.box2 { margin-top: 20px; }
```
**Cách phá vỡ:** Dùng `overflow: hidden`, `padding`, `border` hoặc Flexbox/Grid trên cha.

---

### ❓ BEM là gì? Tại sao dùng?
> **TL;DR:** Block__Element--Modifier – quy ước đặt tên class giúp code CSS có cấu trúc, tránh conflict, dễ đọc.

```css
.card { }               /* Block */
.card__title { }        /* Element */
.card__title--large { } /* Modifier */
```

---

## 4. CSS Layout

### ❓ Flexbox dùng khi nào? Giải thích các thuộc tính quan trọng.
> **TL;DR:** Dùng khi cần căn chỉnh items **trong 1 hàng hoặc 1 cột** (1 chiều).

**Thuộc tính container quan trọng:**
```css
.container {
  display: flex;
  flex-direction: row;        /* row | column | row-reverse | column-reverse */
  justify-content: center;    /* Căn theo trục chính */
  align-items: center;        /* Căn theo trục phụ */
  flex-wrap: wrap;            /* Cho phép xuống dòng */
  gap: 16px;
}
```

**Thuộc tính item quan trọng:**
```css
.item {
  flex: 1;                    /* = flex-grow: 1, flex-shrink: 1, flex-basis: 0 */
  align-self: flex-start;     /* Ghi đè align-items cho item này */
  order: -1;                  /* Đưa item lên đầu */
}
```

---

### ❓ CSS Grid dùng khi nào? Khác Flexbox thế nào?
> **TL;DR:** Grid dùng khi cần layout **2 chiều** (cả hàng lẫn cột). Flexbox là 1 chiều.

```css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 cột bằng nhau */
  grid-template-rows: auto;
  gap: 16px;
}

/* Item trải qua nhiều cột/hàng */
.featured { grid-column: 1 / 3; }
```

**Khi nào dùng cái nào:**
- **Flexbox**: Navigation bar, card row, centering đơn giản
- **Grid**: Page layout, dashboard, gallery phức tạp

---

## 5. Responsive Design

### ❓ Mobile First là gì? Tại sao nên dùng?
> **TL;DR:** Viết CSS mặc định cho mobile trước, dùng `min-width` để scale lên. Tốt hơn vì: performance trên mobile, buộc ưu tiên nội dung quan trọng.

```css
/* Mobile mặc định */
.card { flex-direction: column; }

/* Tablet trở lên */
@media (min-width: 768px) { .card { flex-direction: row; } }
```

---

### ❓ Media Queries hoạt động như thế nào?
> **TL;DR:** Áp dụng CSS theo điều kiện về viewport, device, orientation...

```css
@media (max-width: 768px) { /* Mobile */ }
@media (min-width: 768px) { /* Tablet+ */ }
@media (prefers-color-scheme: dark) { /* Dark mode */ }
@media print { /* Khi in */ }
```

---

### ❓ CSS Container Queries là gì? Tại sao hữu ích hơn Media Queries?
> **TL;DR:** Responsive theo **kích thước phần tử cha** chứ không phải viewport – phù hợp hơn cho component-based design.

```css
/* Component card tự responsive theo container cha của nó */
.card-wrapper { container-type: inline-size; }

@container (min-width: 400px) {
  .card { display: flex; flex-direction: row; }
}
```
> Cùng 1 `.card` có thể hiển thị dọc ở sidebar nhỏ, ngang ở main content rộng.

---

## 6. JavaScript Cơ Bản

### ❓ `var` vs `let` vs `const` – Phân biệt?
> **TL;DR:** Dùng `const` mặc định, `let` khi cần reassign. **Không dùng `var`** vì scope lạ và hoisting gây nhầm lẫn.

| | `var` | `let` | `const` |
|---|---|---|---|
| **Scope** | Function | Block | Block |
| **Hoisting** | Có (undefined) | Có (TDZ – lỗi) | Có (TDZ – lỗi) |
| **Reassign** | ✅ | ✅ | ❌ |
| **Redeclare** | ✅ | ❌ | ❌ |

---

### ❓ `==` vs `===` – Nên dùng cái nào?
> **TL;DR:** Luôn dùng `===`. `==` tự ép kiểu gây ra kết quả bất ngờ.

```javascript
5 == "5"           // true  (ép kiểu)
5 === "5"          // false (strict)
null == undefined  // true
null === undefined // false
NaN == NaN         // false (NaN không bằng chính nó!)
```

---

### ❓ `null` vs `undefined` – Khác nhau thế nào?
> **TL;DR:** `undefined` = biến khai báo nhưng chưa gán. `null` = giá trị rỗng được gán **cố ý**.

```javascript
let a;         // undefined – tự nhiên, chưa có giá trị
let b = null;  // null – lập trình viên chủ động đặt "không có giá trị"

typeof undefined // "undefined"
typeof null      // "object" ← quirk lịch sử của JS!
```

---

### ❓ Primitive vs Reference – Khác nhau khi gán/copy?
> **TL;DR:** Primitive copy giá trị. Reference copy **địa chỉ bộ nhớ** → thay đổi 1 chỗ ảnh hưởng nơi khác.

```javascript
// Primitive: copy giá trị
let a = 5;
let b = a;
b = 10;
console.log(a); // 5 – không bị ảnh hưởng

// Reference: copy địa chỉ
let obj1 = { name: "Alice" };
let obj2 = obj1;
obj2.name = "Bob";
console.log(obj1.name); // "Bob" – bị ảnh hưởng!
```

---

### ❓ Closure là gì? Cho ví dụ thực tế.
> **TL;DR:** Hàm con ghi nhớ và truy cập được biến của hàm cha **dù hàm cha đã chạy xong**.

```javascript
function createCounter() {
  let count = 0;
  return {
    increment: () => ++count,
    decrement: () => --count,
    value: () => count,
  };
}

const counter = createCounter();
counter.increment(); // 1
counter.increment(); // 2
counter.decrement(); // 1
counter.value();     // 1
```
**Ứng dụng thực tế:** Module pattern, memoization, factory functions.

---

### ❓ Hoisting là gì?
> **TL;DR:** JS đưa khai báo biến và hàm lên đầu scope trước khi chạy. `var` hoisted với giá trị `undefined`. `let/const` hoisted nhưng vào TDZ (Temporal Dead Zone – lỗi nếu dùng trước khai báo).

```javascript
console.log(a); // undefined (không lỗi vì var hoisted)
var a = 5;

console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 5;

sayHi(); // "Hi!" – Function declaration hoisted hoàn toàn
function sayHi() { console.log("Hi!"); }
```

---

### ❓ Prototype Chain là gì?
> **TL;DR:** Cơ chế kế thừa của JS – khi truy cập thuộc tính không tồn tại trên object, JS tìm lên `__proto__` (prototype của constructor) cho đến `null`.

```javascript
const dog = { name: "Rex" };
// dog.__proto__ → Object.prototype → null
// Khi dog.toString() → tìm trong dog (không có) → tìm Object.prototype (có!)
```

---

## 7. JavaScript Nâng Cao

### ❓ Event Loop – Giải thích cơ chế bất đồng bộ của JS.
> **TL;DR:** JS đơn luồng. Event Loop xử lý theo thứ tự: **Đồng bộ → Microtask (Promise) → Macrotask (setTimeout)**.

```javascript
console.log("A");                               // 1 – đồng bộ
setTimeout(() => console.log("B"), 0);          // 4 – Macrotask
Promise.resolve().then(() => console.log("C")); // 3 – Microtask
console.log("D");                               // 2 – đồng bộ

// Kết quả: A → D → C → B
```

> **Microtask luôn chạy TRƯỚC Macrotask tiếp theo**, dù timeout là 0ms.

---

### ❓ Promise vs Async/Await – Nên dùng cái nào?
> **TL;DR:** Cùng là bất đồng bộ. `async/await` là "syntactic sugar" của Promise, code đọc dễ hơn như đồng bộ.

```javascript
// Promise (chain)
fetch("/api/user")
  .then(res => res.json())
  .then(user => console.log(user))
  .catch(err => console.error(err));

// Async/Await (sạch hơn, dễ đọc hơn)
async function getUser() {
  try {
    const res = await fetch("/api/user");
    const user = await res.json();
    console.log(user);
  } catch (err) {
    console.error(err);
  }
}
```

---

### ❓ `Promise.all` vs `Promise.allSettled` vs `Promise.race`?
> **TL;DR:** `all` = song song, lỗi 1 là fail hết. `allSettled` = song song, trả hết dù lỗi. `race` = lấy cái nào xong trước.

```javascript
// Dùng Promise.all khi cần tất cả đều thành công
const [user, posts] = await Promise.all([fetchUser(), fetchPosts()]);

// Dùng allSettled khi muốn biết kết quả từng cái dù lỗi
const results = await Promise.allSettled([fetchA(), fetchB()]);
results.forEach(r => {
  if (r.status === "fulfilled") console.log(r.value);
  else console.error(r.reason);
});
```

---

### ❓ Debounce vs Throttle – Phân biệt và ví dụ dùng?
> **TL;DR:** Debounce: chờ ngừng hành động rồi mới gọi (search input). Throttle: gọi tối đa 1 lần/X ms (scroll, resize).

```javascript
// Debounce – chỉ gọi sau 300ms kể từ lần gõ cuối cùng
function debounce(fn, delay) {
  let timer;
  return (...args) => {
    clearTimeout(timer);
    timer = setTimeout(() => fn(...args), delay);
  };
}
const handleSearch = debounce((query) => fetchResults(query), 300);

// Throttle – tối đa 1 lần mỗi 200ms
function throttle(fn, limit) {
  let lastCall = 0;
  return (...args) => {
    const now = Date.now();
    if (now - lastCall >= limit) {
      lastCall = now;
      fn(...args);
    }
  };
}
const handleScroll = throttle(() => updateUI(), 200);
```

---

### ❓ Shallow Copy vs Deep Copy?
> **TL;DR:** Shallow copy chỉ copy 1 cấp – object/array lồng bên trong vẫn share địa chỉ. Deep copy tạo bản sao hoàn toàn độc lập.

```javascript
const obj = { a: 1, b: { c: 2 } };

// Shallow – thay đổi obj.b.c sẽ ảnh hưởng copy
const shallow = { ...obj };
const shallow2 = Object.assign({}, obj);

// Deep – hoàn toàn độc lập
const deep = structuredClone(obj);                  // ✅ Chuẩn nhất (ES2022)
const deep2 = JSON.parse(JSON.stringify(obj));       // ⚠️ Mất function, Date...
```

---

### ❓ `call` vs `apply` vs `bind`?
> **TL;DR:** Đều thay đổi `this`. `call` gọi ngay với args riêng lẻ. `apply` gọi ngay với args dạng mảng. `bind` trả về hàm mới.

```javascript
function greet(greeting, punctuation) {
  return `${greeting}, ${this.name}${punctuation}`;
}
const user = { name: "Alice" };

greet.call(user, "Hello", "!");     // "Hello, Alice!" – gọi ngay
greet.apply(user, ["Hi", "."]);     // "Hi, Alice." – gọi ngay bằng mảng
const boundGreet = greet.bind(user, "Hey"); // Trả về hàm mới, chưa gọi
boundGreet("?"); // "Hey, Alice?"
```

---

### ❓ `this` trong JS hoạt động như thế nào?
> **TL;DR:** `this` phụ thuộc vào **cách hàm được gọi**, không phải nơi định nghĩa. Arrow function không có `this` riêng.

```javascript
const obj = {
  name: "Alice",
  regular: function() { return this.name; }, // this = obj
  arrow: () => this.name,                    // this = outer scope (thường là window)
};
obj.regular(); // "Alice"
obj.arrow();   // undefined (hoặc global name)
```

---

### ❓ Event Delegation là gì? Tại sao dùng?
> **TL;DR:** Đặt listener trên cha thay vì từng phần tử con. Hiệu quả hơn khi có nhiều items hoặc items được tạo động.

```javascript
// ❌ Không tốt: 100 items = 100 event listeners
document.querySelectorAll(".item").forEach(item => {
  item.addEventListener("click", handleClick);
});

// ✅ Tốt: 1 listener trên cha
document.querySelector(".list").addEventListener("click", (e) => {
  if (e.target.matches(".item")) handleClick(e.target);
});
```

---

## 8. TypeScript

### ❓ TypeScript là gì? Lợi ích so với JS?
> **TL;DR:** JS + kiểu dữ liệu tĩnh. Phát hiện lỗi ngay khi viết code, autocomplete tốt hơn, dễ maintain trong dự án lớn.

```
TypeScript (.ts) → Compile (tsc) → JavaScript (.js) → Trình duyệt
```

---

### ❓ `interface` vs `type` – Dùng cái nào?
> **TL;DR:** `interface` cho object/class. `type` cho union, tuple, complex types.

```typescript
// Interface – có thể extend, merge
interface User {
  id: number;
  name: string;
  email?: string;           // Optional
  readonly createdAt: Date; // Không thể thay đổi
}
interface AdminUser extends User { role: "admin"; }

// Type – linh hoạt hơn
type ID = string | number;                  // Union
type Status = "active" | "inactive";        // Literal union
type AdminUser = User & { role: "admin" };  // Intersection
```

---

### ❓ Generics là gì? Cho ví dụ?
> **TL;DR:** Cho phép viết hàm/component hoạt động với nhiều kiểu dữ liệu khác nhau mà vẫn type-safe.

```typescript
// Không có Generic – phải viết nhiều hàm
function getFirstNumber(arr: number[]): number { return arr[0]; }
function getFirstString(arr: string[]): string { return arr[0]; }

// Với Generic – 1 hàm dùng cho mọi kiểu
function getFirst<T>(arr: T[]): T { return arr[0]; }

getFirst<number>([1, 2, 3]);  // 1, type: number
getFirst<string>(["a", "b"]); // "a", type: string
```

---

### ❓ Các Utility Types thường dùng?
> **TL;DR:** `Partial`, `Pick`, `Omit`, `Readonly`, `Record` – biến đổi type có sẵn mà không cần định nghĩa lại.

```typescript
interface User { id: number; name: string; email: string; age: number; }

type OptionalUser  = Partial<User>;             // Tất cả thành optional
type UserCard      = Pick<User, "id" | "name">; // Chỉ lấy id và name
type NoAge         = Omit<User, "age">;         // Bỏ age
type ImmutableUser = Readonly<User>;            // Không thể sửa
type UserMap       = Record<string, User>;      // { [key: string]: User }
```

---

## 9. Web Tổng Quát

### ❓ CORS là gì? Khi nào gặp lỗi CORS và cách fix?
> **TL;DR:** Cơ chế bảo mật trình duyệt chặn request từ domain này sang domain khác. Fix từ **phía server** bằng cách thêm header `Access-Control-Allow-Origin`.

```
Frontend: http://localhost:3000
Backend API: http://api.example.com
→ Trình duyệt chặn vì khác origin!
```

**Fix:**
- Server thêm: `Access-Control-Allow-Origin: http://localhost:3000`
- Dev: Dùng proxy trong Vite config (`/api` → forward đến backend)

---

### ❓ HTTP Methods – Phân biệt và khi nào dùng?
> **TL;DR:** GET (lấy), POST (tạo), PUT (cập nhật toàn bộ), PATCH (cập nhật một phần), DELETE (xóa).

| Method | Idempotent | Body | Dùng khi |
|---|---|---|---|
| `GET` | ✅ | ❌ | Lấy dữ liệu |
| `POST` | ❌ | ✅ | Tạo mới |
| `PUT` | ✅ | ✅ | Cập nhật toàn bộ |
| `PATCH` | ✅ | ✅ | Cập nhật một phần |
| `DELETE` | ✅ | ❌ | Xóa |

---

### ❓ HTTP Status Codes quan trọng?
> **TL;DR:** 2xx = thành công, 3xx = redirect, 4xx = lỗi client, 5xx = lỗi server.

| Code | Ý nghĩa |
|---|---|
| `200` | OK |
| `201` | Created |
| `204` | No Content (thường sau DELETE) |
| `301/302` | Redirect (vĩnh viễn / tạm thời) |
| `400` | Bad Request |
| `401` | Unauthorized (chưa đăng nhập) |
| `403` | Forbidden (không có quyền) |
| `404` | Not Found |
| `422` | Unprocessable Entity (validate fail) |
| `500` | Internal Server Error |

---

### ❓ SPA vs MPA – Ưu nhược điểm?
> **TL;DR:** SPA mượt mà nhưng SEO khó, load lần đầu chậm. MPA SEO tốt nhưng chuyển trang chậm.

| | SPA | MPA |
|---|---|---|
| **Điều hướng** | JS cập nhật DOM, không reload | Reload toàn trang |
| **SEO** | ⚠️ Cần SSR/SSG thêm | ✅ Tự nhiên |
| **UX** | ✅ Mượt mà | ⚠️ Chuyển trang có flash |
| **Ví dụ** | React app, Gmail | Wikipedia, e-commerce truyền thống |

---

### ❓ CSR vs SSR vs SSG – Khi nào chọn cái nào?
> **TL;DR:** CSR = render client-side (SEO kém). SSR = render server mỗi request (SEO tốt, fresh data). SSG = build sẵn HTML tĩnh (nhanh nhất, SEO tốt nhất).

| | CSR | SSR | SSG |
|---|---|---|---|
| **Render ở** | Browser | Server | Build time |
| **SEO** | ❌ Kém | ✅ Tốt | ✅ Rất tốt |
| **Tốc độ** | Chậm ban đầu | Trung bình | ✅ Rất nhanh |
| **Data** | Luôn mới | Luôn mới | Cũ đến khi rebuild |
| **Dùng khi** | Dashboard, app cần auth | E-commerce, news | Blog, docs, landing page |

---

### ❓ Browser Rendering Pipeline là gì?
> **TL;DR:** HTML/CSS → DOM/CSSOM → Render Tree → Layout (Reflow) → Paint → Composite.

```
Parse HTML → DOM Tree ─┐
Parse CSS  → CSSOM    ─┘→ Render Tree → Layout → Paint → Composite
```

- **Reflow** (thay đổi layout: width, height, position): **Rất tốn kém**
- **Repaint** (thay đổi visual: color, background): Tốn kém nhưng ít hơn reflow
- **Composite** (transform, opacity): **Nhanh nhất** – xảy ra trên GPU

**Tối ưu:** Dùng `transform` và `opacity` cho animation thay vì `left`/`top`.

---

### ❓ Core Web Vitals là gì?
> **TL;DR:** 3 chỉ số performance quan trọng của Google, ảnh hưởng SEO ranking.

| Chỉ số | Tên đầy đủ | Mục tiêu | Đo gì |
|---|---|---|---|
| **LCP** | Largest Contentful Paint | < 2.5s | Thời gian load phần tử lớn nhất |
| **INP** | Interaction to Next Paint | < 200ms | Độ nhạy với tương tác user |
| **CLS** | Cumulative Layout Shift | < 0.1 | Độ ổn định layout khi load |

---

## 10. React

### ❓ Virtual DOM là gì? Tại sao dùng?
> **TL;DR:** Bản sao nhẹ của DOM thật trong bộ nhớ. React so sánh (diffing) để tìm thay đổi tối thiểu rồi mới cập nhật DOM thật – tránh reflow/repaint không cần thiết.

```
State thay đổi
→ React tạo Virtual DOM mới
→ Diff với Virtual DOM cũ (Reconciliation)
→ Chỉ cập nhật phần thay đổi thật sự lên DOM thật
```

---

### ❓ `useEffect` – Giải thích và các trường hợp dùng?
> **TL;DR:** Chạy side effects sau khi render. Dependency array kiểm soát khi nào re-run.

```javascript
// Chạy sau mỗi render
useEffect(() => { /* ... */ });

// Chạy 1 lần sau mount (componentDidMount)
useEffect(() => { /* ... */ }, []);

// Chạy khi userId thay đổi
useEffect(() => {
  fetchUser(userId);
}, [userId]);

// Cleanup – chạy khi unmount hoặc trước khi effect re-run
useEffect(() => {
  const sub = subscribe(userId);
  return () => sub.unsubscribe(); // Cleanup!
}, [userId]);
```

---

### ❓ `useMemo` vs `useCallback` – Khi nào dùng?
> **TL;DR:** `useMemo` ghi nhớ **kết quả tính toán**. `useCallback` ghi nhớ **hàm** (tránh tạo lại mỗi render).

```javascript
// useMemo – tính toán nặng, không muốn tính lại nếu input không đổi
const expensiveValue = useMemo(() => {
  return heavyCalculation(data);
}, [data]);

// useCallback – hàm truyền vào component con có React.memo
const handleClick = useCallback(() => {
  doSomething(userId);
}, [userId]);
```

> ⚠️ Đừng dùng bừa bãi – chỉ dùng khi thực sự có vấn đề performance.

---

### ❓ Key trong list – Tại sao quan trọng? Tại sao không dùng index?
> **TL;DR:** Key giúp React nhận ra phần tử nào thay đổi trong list. Không dùng index nếu list thay đổi thứ tự vì React sẽ re-render sai.

```javascript
// ❌ Sai – thêm item đầu list → mọi item đều re-render
{items.map((item, index) => <Item key={index} data={item} />)}

// ✅ Đúng – key ổn định, unique
{items.map(item => <Item key={item.id} data={item} />)}
```

---

### ❓ `useEffect` cleanup function dùng để làm gì?
> **TL;DR:** Dọn dẹp side effects khi component unmount hoặc dependency thay đổi. Tránh memory leak.

```javascript
useEffect(() => {
  const controller = new AbortController();
  fetch("/api/data", { signal: controller.signal });

  return () => controller.abort(); // Cleanup: hủy request nếu unmount
}, []);
```

---

### ❓ useState vs useReducer – Dùng cái nào?
> **TL;DR:** `useState` cho state đơn giản, độc lập. `useReducer` khi state phức tạp, nhiều actions liên quan nhau.

```javascript
// useState – đơn giản
const [count, setCount] = useState(0);

// useReducer – state phức tạp, nhiều transitions
const [state, dispatch] = useReducer((state, action) => {
  switch (action.type) {
    case "INCREMENT": return { ...state, count: state.count + 1 };
    case "RESET":     return { count: 0, error: null };
    default: return state;
  }
}, { count: 0, error: null });
```

---

## 11. Công Cụ & Hệ Sinh Thái

### ❓ Vite vs Webpack – Khác nhau thế nào?
> **TL;DR:** Vite dùng ESM native → dev server cực nhanh, HMR tức thì. Webpack bundle toàn bộ → chậm hơn ở dev.

| | Vite | Webpack |
|---|---|---|
| **Dev server** | ESM native, cực nhanh | Bundle toàn bộ, chậm hơn |
| **HMR** | Cực nhanh (module-level) | Chậm hơn (bundle-level) |
| **Dùng khi** | Dự án mới (2024+) | Legacy projects, Next.js |

---

### ❓ State Management – Khi nào cần Zustand/Redux?
> **TL;DR:** Không phải lúc nào cũng cần global state. Thứ tự ưu tiên: local state → Context API → Zustand → Redux Toolkit.

| Tool | Khi nào dùng |
|---|---|
| `useState/useReducer` | Component-level state |
| **Context API** | Global state ít thay đổi (theme, auth user) |
| **Zustand** | Global state cần update thường xuyên, gọn nhẹ |
| **TanStack Query** | Server/async state – cache, refetch, pagination |
| **Redux Toolkit** | App rất lớn, team lớn, cần devtools mạnh |

---

## 12. Câu Hỏi Tình Huống

### ❓ Website load chậm – Bạn debug như thế nào?
> **TL;DR:** Dùng Chrome DevTools (Lighthouse, Network, Performance tab) để xác định bottleneck.

**Quy trình debug:**
1. **Lighthouse** → xem điểm Core Web Vitals, gợi ý cụ thể
2. **Network tab** → file nào lớn? Request nào chậm?
3. **Performance tab** → script nào block? Layout shift ở đâu?

**Giải pháp phổ biến:**
- Ảnh lớn → dùng WebP, lazy load, `srcset`
- JS nhiều → code splitting, tree shaking
- Render blocking → `async`/`defer` cho script
- API chậm → cache, pagination, skeleton UI

---

### ❓ Làm sao để tránh memory leak trong React?
> **TL;DR:** Cleanup trong `useEffect`, tránh setState sau khi unmount, dùng AbortController cho fetch.

```javascript
useEffect(() => {
  let isActive = true;

  fetchData().then(data => {
    if (isActive) setData(data); // ✅ Không setState nếu đã unmount
  });

  return () => { isActive = false; };
}, []);
```

---

### ❓ Nếu gặp infinite loop trong `useEffect` – Làm sao fix?
> **TL;DR:** Kiểm tra dependency array. Object/array trong deps bị tạo mới mỗi render → cần `useMemo`/`useCallback`.

```javascript
// ❌ Bug: options tạo mới mỗi render → effect chạy mãi
const options = { limit: 10 }; // Object mới mỗi render
useEffect(() => { fetch("/api", options); }, [options]);

// ✅ Fix 1: useMemo
const options = useMemo(() => ({ limit: 10 }), []);

// ✅ Fix 2: Dùng primitive value
useEffect(() => { fetch(`/api?limit=${limit}`); }, [limit]);
```

---

## 13. Bài Tập Code Trực Tiếp

### 💻 Bài 1 – Output là gì?
```javascript
console.log([] == ![]);         // ?
console.log(NaN === NaN);       // ?
console.log(typeof null);       // ?
console.log(0.1 + 0.2 === 0.3); // ?
```
> **Đáp án:** `true` | `false` | `"object"` | `false`
> - `![]` = `false`, cả hai ép thành `0`; NaN ≠ NaN; typeof null là quirk; floating point precision

---

### 💻 Bài 2 – Event Loop: Thứ tự output?
```javascript
console.log("1");
setTimeout(() => console.log("2"), 0);
Promise.resolve().then(() => console.log("3"));
setTimeout(() => console.log("4"), 0);
Promise.resolve().then(() => console.log("5"));
console.log("6");
```
> **Đáp án:** `1 → 6 → 3 → 5 → 2 → 4`
> - 1, 6: đồng bộ → 3, 5: Microtasks → 2, 4: Macrotasks

---

### 💻 Bài 3 – Viết hàm `debounce`
```javascript
function debounce(fn, delay) {
  // Implement ở đây
}
const search = debounce((q) => console.log("Searching:", q), 300);
```
> **Đáp án:**
> ```javascript
> function debounce(fn, delay) {
>   let timer;
>   return function(...args) {
>     clearTimeout(timer);
>     timer = setTimeout(() => fn.apply(this, args), delay);
>   };
> }
> ```

---

### 💻 Bài 4 – Flatten mảng lồng nhau (không dùng `.flat()`)
```javascript
// Input:  [1, [2, [3, [4]], 5]]
// Output: [1, 2, 3, 4, 5]
function flatten(arr) { /* ... */ }
```
> **Đáp án:**
> ```javascript
> function flatten(arr) {
>   return arr.reduce((acc, item) =>
>     Array.isArray(item) ? [...acc, ...flatten(item)] : [...acc, item], []);
> }
> ```

---

### 💻 Bài 5 – React custom hook `useFetch`
```typescript
function useFetch<T>(url: string) {
  // Return: { data, loading, error }
}
```
> **Đáp án:**
> ```typescript
> function useFetch<T>(url: string) {
>   const [data, setData] = useState<T | null>(null);
>   const [loading, setLoading] = useState(true);
>   const [error, setError] = useState<Error | null>(null);
>
>   useEffect(() => {
>     const controller = new AbortController();
>     setLoading(true);
>     fetch(url, { signal: controller.signal })
>       .then(res => { if (!res.ok) throw new Error(`HTTP ${res.status}`); return res.json(); })
>       .then(data => { setData(data); setLoading(false); })
>       .catch(err => { if (err.name !== "AbortError") { setError(err); setLoading(false); } });
>     return () => controller.abort();
>   }, [url]);
>
>   return { data, loading, error };
> }
> ```

---

## 🚀 Tips Trả Lời PV Hiệu Quả

### Cấu trúc STAR cho câu hỏi tình huống
> **S**ituation → **T**ask → **A**ction → **R**esult

### Câu hay hỏi ngược lại PV
- "Stack công nghệ hiện tại của team là gì?"
- "Team có bao nhiêu người? Workflow FE & BE như thế nào?"
- "Sản phẩm đang ở giai đoạn nào? Scale thế nào?"
- "Cơ hội học hỏi và phát triển trong team?"

### Từ khóa gây ấn tượng với PV
- **Performance**: Core Web Vitals, LCP, CLS, code splitting, lazy loading
- **DX**: TypeScript, ESLint, Prettier, Husky, CI/CD
- **Best practices**: BEM, Clean code, accessibility, semantic HTML
- **Trending 2024–2026**: Vite, pnpm, TanStack Query, Zustand, Server Components, Container Queries

---

*Tổng hợp từ [frontend_full_notes_vi.md](file:///d:/practices/frontend_full_notes_vi.md)*
