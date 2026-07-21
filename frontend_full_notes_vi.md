# 📚 Tổng Hợp Kiến Thức Front-End – Đầy Đủ & Xúc Tích

---

## 1. GIT

### 1.1 Khái niệm cốt lõi
- **Git là gì?** Hệ thống quản lý phiên bản (Version Control System), theo dõi thay đổi mã nguồn theo thời gian.
- **Git vs GitHub:** Git là phần mềm chạy trên máy local. GitHub là nơi lưu repo online (cloud).

### 1.2 Kiến trúc hoạt động – 3 vùng
| Vùng | Vai trò |
|---|---|
| **Working Directory** | Thư mục project đang làm việc |
| **Staging Area** | Chọn file nào sẽ commit |
| **Repository** | Nơi Git lưu lịch sử thay đổi |

> **Flow cơ bản:** Sửa file → `git add` → `git commit` → lưu lịch sử

### 1.3 So sánh

**Merge vs Rebase**
- `Merge`: Gộp branch, giữ toàn bộ lịch sử thật, sinh ra 1 "merge commit". **An toàn cho team**.
- `Rebase`: Dời commit lên đầu branch mới, lịch sử thẳng, gọn sạch. **Tuyệt đối không rebase branch đã push chung.**

**Reset vs Revert**
- `Reset`: Quay lại commit cũ, thay đổi lịch sử. Dùng local.
  - `--soft`: giữ code + staging
  - `--mixed` (mặc định): giữ code
  - `--hard`: xóa tất cả
- `Revert`: Tạo commit mới để undo. Giữ nguyên lịch sử, **an toàn cho shared repo**.

### 1.4 GitFlow – 5 loại branch
| Branch | Vai trò |
|---|---|
| `main` | Production (live) |
| `develop` | Code đang phát triển |
| `feature/*` | Phát triển tính năng mới |
| `release/*` | Chuẩn bị release, test, fix bug |
| `hotfix/*` | Sửa lỗi khẩn cấp trên production |

### 1.5 Lệnh cần thuộc nằm lòng
```bash
git init / git clone          # Khởi tạo / tải repo
git status / git log          # Xem trạng thái / lịch sử commit
git add / git commit          # Thêm vào staging / lưu lịch sử
git branch / git checkout     # Tạo-xem nhánh / chuyển nhánh
git merge                     # Gộp nhánh
git push / git pull           # Upload / cập nhật code từ remote
```

---

## 2. HTML

### 2.1 HTML là gì?
**HTML (HyperText Markup Language)** – ngôn ngữ đánh dấu dùng để tạo cấu trúc trang web bằng hệ thống thẻ (tags).

**HTML vs XHTML vs HTML5:**
- `HTML`: Cú pháp linh hoạt, không bắt buộc đóng thẻ.
- `XHTML`: Nghiêm ngặt, phải đóng tất cả thẻ, dựa trên XML.
- `HTML5`: Phiên bản mới nhất. Thêm semantic tags, APIs (Canvas, WebSocket, Geolocation, Web Workers...), Web Storage, native audio/video.

### 2.2 DOCTYPE & Cấu trúc cơ bản
```html
<!DOCTYPE html>   <!-- Khai báo HTML5, bắt buộc ở dòng đầu -->
<html>
  <head>          <!-- Metadata: title, meta, link, style -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Trang web</title>
  </head>
  <body>          <!-- Toàn bộ nội dung hiển thị -->
  </body>
</html>
```
> Không có `DOCTYPE` → trình duyệt vào **quirks mode**, CSS/box model có thể render sai.

### 2.3 Tag vs Element | Block vs Inline vs Inline-block
- **Tag** là cú pháp đánh dấu (`<p>`, `</p>`). **Element** = thẻ mở + nội dung + thẻ đóng (`<p>Hello</p>`).

| Loại | Đặc điểm | Ví dụ |
|---|---|---|
| **Block** | Chiếm full ngang, xuống dòng, set được width/height | `div`, `p`, `h1-h6`, `section` |
| **Inline** | Chỉ chiếm chỗ cần, không xuống dòng, không set width/height | `span`, `a`, `strong` |
| **Inline-block** | Cùng dòng như inline nhưng set được width/height | `button`, `input`, `img` |

### 2.4 Attribute (Thuộc tính)
- Cú pháp: `name="value"` viết trong thẻ mở.
- **Boolean attribute**: chỉ cần có mặt là `true` (VD: `disabled`, `checked`, `required`).
- **Custom data attribute**: `data-user-id="123"` – truy cập qua JS: `element.dataset.userId`.
- **id**: Duy nhất toàn trang. **class**: Dùng lại được, 1 element có thể có nhiều class.

### 2.5 Semantic HTML
Dùng thẻ có ý nghĩa thay vì `div/span` chung chung → tốt cho **SEO** và **Accessibility**.

| Thẻ | Vai trò |
|---|---|
| `<header>` | Phần đầu trang / section |
| `<nav>` | Điều hướng chính |
| `<main>` | Nội dung chính (duy nhất 1/page) |
| `<section>` | Nhóm nội dung có chủ đề, thường có `<h2>` |
| `<article>` | Nội dung độc lập, có thể đứng riêng (bài blog, card) |
| `<aside>` | Nội dung phụ (sidebar, ads) |
| `<footer>` | Phần cuối trang / section |
| `<figure>` + `<figcaption>` | Hình ảnh / biểu đồ + chú thích |
| `<time datetime="">` | Ngày giờ (quan trọng cho SEO) |
| `<details>` + `<summary>` | Accordion native, không cần JS |

### 2.6 HTML Form
**Các thành phần chính:**
- `<label>`: Luôn liên kết với input (qua `for`/`id` hoặc wrapping). Tăng click area.
- `<input>` types: `text`, `password`, `email`, `number`, `tel`, `date`, `checkbox`, `radio`, `file`, `hidden`, `submit`.
- `<select>`: Dropdown cố định. `<datalist>`: Gợi ý tự điền.
- `<fieldset>` + `<legend>`: Nhóm form controls liên quan.

**Trạng thái quan trọng:**
- `readonly`: Không sửa được nhưng **vẫn submit**.
- `disabled`: Không focus, không submit.

**Validation (HTML5):** `required`, `pattern`, `min/max`, `minlength/maxlength`.

**Method GET vs POST:**
- `GET`: Dữ liệu qua URL, giới hạn kích thước, dùng cho tìm kiếm.
- `POST`: Dữ liệu trong body, không giới hạn, dùng cho form nhạy cảm. (POST không tự bảo mật hơn GET — cần HTTPS.)

### 2.7 Web APIs nổi bật (HTML5)
| API | Dùng để |
|---|---|
| **Canvas** | Vẽ đồ họa pixel-based bằng JS (game) |
| **SVG** | Đồ họa vector, không mất nét, accessible |
| **Web Storage** | `localStorage` (vĩnh viễn ~5MB), `sessionStorage` (đóng tab là mất) |
| **IndexedDB** | Database NoSQL trong browser, lưu data lớn |
| **Web Worker** | Chạy JS background thread, không block UI |
| **Service Worker + PWA** | Offline caching, push notification, trải nghiệm như app native |
| **WebSocket** | Kết nối 2 chiều real-time (chat, live data) |
| **History API** | Thao tác browser history không reload (nền tảng SPA routing) |
| **Intersection Observer** | Theo dõi element vào/ra viewport (lazy load, infinite scroll) |
| **Geolocation API** | Lấy tọa độ thiết bị |

### 2.8 Web Accessibility (A11y)
- **WCAG** – 3 cấp (A, AA, AAA). Nguyên tắc: Perceivable, Operable, Understandable, Robust.
- **Color contrast**: Tối thiểu 4.5:1 (WCAG AA).
- **Heading hierarchy**: Screen reader điều hướng qua `h1-h6`, không nhảy cấp, 1 `<h1>` mỗi trang.
- **Alt text**: Ảnh thông tin → mô tả ngắn. Ảnh trang trí → `alt=""`.
- **Keyboard navigation**: Mọi tính năng phải dùng được bằng Tab/Enter/Space/Escape.
- **tabindex**: `0` (vào luồng tab tự nhiên), `-1` (chỉ focus bằng JS). Tránh `>0`.
- **ARIA**: `aria-label`, `aria-labelledby`, `aria-describedby`, `aria-live` – cung cấp ngữ nghĩa cho trình đọc màn hình.

### 2.9 SEO cơ bản
```html
<title>Tiêu đề trang (50-60 ký tự)</title>
<meta name="description" content="Mô tả (150-160 ký tự), ảnh hưởng CTR">
<link rel="canonical" href="URL chính thức"> <!-- Tránh duplicate content -->

<!-- Open Graph (hiển thị khi share lên MXH) -->
<meta property="og:title" content="...">
<meta property="og:image" content="...">
```
- **Sitemap XML**: Giúp bot Google crawl trang.
- **Robots.txt**: Chặn crawler ở cấp website/path.
- **Structured data (Schema.org / JSON-LD)**: Tạo rich snippets (rating, giá...) trên Google.
- **Core Web Vitals**: LCP < 2.5s, INP < 200ms, CLS < 0.1 – là ranking factor của Google.

---

## 3. CSS

### 3.1 CSS là gì?
**CSS (Cascading Style Sheets)** – ngôn ngữ định dạng giao diện cho HTML.

**3 cách viết CSS:**
- `Inline`: `style=""` trực tiếp trên thẻ.
- `Internal`: `<style>` trong `<head>`.
- `External`: File `.css` riêng, nhúng qua `<link>`.

### 3.2 Selectors
| Selector | Cú pháp | Ví dụ |
|---|---|---|
| Element | `tag` | `p {}` |
| Class | `.class` | `.btn {}` |
| ID | `#id` | `#header {}` |
| Universal | `*` | `* { margin: 0 }` |
| Attribute | `[attr="val"]` | `input[type="text"] {}` |
| Pseudo-class | `:hover`, `:nth-child(n)`, `:not()` | `a:hover {}` |
| Pseudo-element | `::before`, `::after`, `::first-letter` | `p::before {}` |

**CSS Combinators:**
- `div p` (Descendant – mọi cấp con)
- `div > p` (Child – con trực tiếp)
- `h1 + p` (Adjacent Sibling – ngay liền kề)
- `h1 ~ p` (General Sibling – tất cả anh em phía sau)

### 3.3 Đơn vị (Units)
| Đơn vị | Loại | Ý nghĩa |
|---|---|---|
| `px` | Absolute | Pixel cố định |
| `em` | Relative | Theo font-size phần tử cha |
| `rem` | Relative | Theo font-size `<html>` (root) |
| `%` | Relative | Theo phần tử cha |
| `vw / vh` | Relative | % chiều rộng / chiều cao viewport |

### 3.4 Box Model
```
Margin → Border → Padding → Content (Width × Height)
```
- `box-sizing: content-box` (mặc định): width chỉ tính Content.
- `box-sizing: border-box` **(khuyên dùng)**: width bao gồm cả Padding + Border.

### 3.5 Display & Position
**Display:**
| Giá trị | Đặc điểm |
|---|---|
| `block` | Chiếm full ngang, xuống dòng |
| `inline` | Cùng dòng, không set width/height |
| `inline-block` | Cùng dòng + set được width/height |
| `none` | Ẩn hoàn toàn, không chiếm chỗ |
| `flex` / `grid` | Layout hiện đại |

**Position:**
| Giá trị | Đặc điểm |
|---|---|
| `static` | Mặc định, theo luồng HTML |
| `relative` | Dịch chuyển so với vị trí gốc, giữ khoảng trống cũ |
| `absolute` | Theo phần tử cha gần nhất có `position` khác `static` |
| `fixed` | Cố định theo cửa sổ trình duyệt |
| `sticky` | Relative + tự chuyển thành fixed khi cuộn đến ngưỡng |

### 3.6 Inheritance (Kế thừa)
- **Có kế thừa** (liên quan text): `color`, `font-size`, `font-family`, `text-align`, `line-height`.
- **Không kế thừa** (liên quan layout): `margin`, `padding`, `border`, `width`, `height`, `background`.

### 3.7 Specificity (Độ ưu tiên)
```
!important > Inline style > ID > Class/Pseudo-class > Element
```
> Tránh dùng `!important` – khó override về sau. Tránh dùng `id` để style.

### 3.8 Những "bẫy" thường gặp
- **Margin Collapsing**: Margin trên/dưới của 2 khối bị gộp lại (lấy giá trị lớn hơn, không cộng dồn).
- **Float & Clearfix**: Phần tử cha "sập" chiều cao khi con dùng float → dùng `::after` clearfix.
- **Z-index**: Chỉ hoạt động trong cùng Stacking Context – nếu z-index không chạy, kiểm tra phần tử cha.

---

## 4. CSS PREPROCESSOR & POSTPROCESSOR

### 4.1 Preprocessor là gì?
Mở rộng CSS với tính năng lập trình, sau đó **compile** thành CSS thuần.

```
SCSS/Less/Stylus → Compile → CSS thuần → Trình duyệt
```

**Tính năng cốt lõi:**
- **Variables**: Lưu màu sắc, font... dùng lại nhiều nơi.
- **Nesting**: Viết CSS lồng theo cấu trúc HTML.
- **Mixins**: Nhóm thuộc tính tái sử dụng (như function).
- **Modularization**: Chia thành nhiều file nhỏ (`_variables.scss`, `_header.scss`...).

**Các Preprocessor phổ biến:**
| Tên | Đặc điểm |
|---|---|
| **SCSS/Sass** | Phổ biến nhất, cú pháp giống CSS |
| **Less** | Dễ học, dùng `@` cho biến |
| **Stylus** | Cú pháp tự do, không cần `{}` hay `;` |

### 4.2 Postprocessor
Can thiệp **sau khi** đã có CSS thuần để tối ưu hóa.
- **Autoprefixer**: Tự thêm `-webkit-`, `-moz-`... cho trình duyệt cũ.
- **Minify**: Xóa khoảng trắng, comment → file nhẹ hơn.
- **Công cụ**: PostCSS + các plugin.

```
SCSS → Compile → CSS thuần → PostCSS (prefix, minify) → CSS tối ưu → Server
```

---

## 5. CSS LAYOUT

### 5.1 Flexbox (1 chiều)
Dùng khi cần **căn chỉnh các phần tử trong 1 hàng hoặc 1 cột**.

**Thuộc tính cho Container (Cha):**
| Thuộc tính | Mô tả |
|---|---|
| `display: flex` | Bật Flexbox |
| `flex-direction` | Hướng trục chính (`row`, `column`) |
| `flex-wrap` | Cho phép xuống dòng (`wrap`, `nowrap`) |
| `justify-content` | Căn chỉnh theo trục chính (ngang) |
| `align-items` | Căn chỉnh theo trục phụ (dọc) |
| `align-content` | Căn chỉnh nhiều dòng theo trục phụ |
| `gap` | Khoảng cách giữa các item |

**Thuộc tính cho Items (Con):**
| Thuộc tính | Mô tả |
|---|---|
| `flex-grow` | Tỷ lệ giãn nở khi còn không gian thừa |
| `flex-shrink` | Tỷ lệ thu hẹp khi thiếu không gian |
| `flex-basis` | Kích thước mặc định trước khi phân phối space |
| `flex` | Viết tắt: `grow shrink basis` |
| `align-self` | Ghi đè `align-items` cho riêng item đó |
| `order` | Thay đổi thứ tự hiển thị |

### 5.2 CSS Grid (2 chiều)
Dùng khi cần **chia layout tổng thể** với cả hàng lẫn cột.

**Thuộc tính cho Container (Cha):**
| Thuộc tính | Mô tả |
|---|---|
| `display: grid` | Bật Grid |
| `grid-template-columns` | Xác định cột (px, %, fr, auto) |
| `grid-template-rows` | Xác định hàng |
| `grid-template-areas` | Sơ đồ layout bằng tên vùng |
| `column-gap / row-gap` | Khoảng cách giữa cột / hàng |
| `justify-items / align-items` | Căn chỉnh item trong ô |
| `justify-content / align-content` | Căn chỉnh toàn bộ lưới trong container |

**Thuộc tính cho Items (Con):**
- `grid-column: 1 / 3` (trải từ cột 1 đến 3)
- `grid-row: 1 / 2`
- `grid-area: tên` (kết hợp với `grid-template-areas`)

**Đơn vị & hàm đặc biệt:**
- `fr`: Phần không gian còn lại (VD: `1fr 2fr` = chia 1/3 và 2/3).
- `repeat(3, 1fr)`: Lặp lại 3 cột bằng nhau.
- `minmax(200px, 1fr)`: Không nhỏ hơn 200px, không lớn hơn 1fr.

### 5.3 Flexbox vs Grid – Khi nào dùng cái nào?
| | Flexbox | CSS Grid |
|---|---|---|
| **Số chiều** | 1 chiều (hàng HOẶC cột) | 2 chiều (hàng VÀ cột) |
| **Ưu tiên** | Nội dung (Content-first) | Bố cục (Layout-first) |
| **Dùng khi** | Căn chỉnh items trong component | Chia layout tổng thể trang |

---

## 6. CSS RESPONSIVE DESIGN

### 6.1 Responsive vs Adaptive
- **Adaptive (AWD)**: Nhiều phiên bản web cho từng loại thiết bị.
- **Responsive (RWD)**: 1 trang web, tự co giãn theo màn hình bằng CSS. **Phương pháp chủ yếu hiện nay.**

### 6.2 Mobile First
Viết CSS mặc định cho **mobile trước**, dùng `min-width` để scale lên màn hình lớn hơn.
```css
/* Mobile mặc định */
.container { padding: 16px; }

/* Tablet trở lên */
@media (min-width: 768px) { .container { padding: 32px; } }

/* Desktop */
@media (min-width: 1024px) { .container { padding: 48px; } }
```

### 6.3 Viewport Meta Tag (Bắt buộc)
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```
Không có thẻ này → trang bị thu nhỏ tí hon trên điện thoại.

### 6.4 Media Queries
```css
@media screen and (min-width: 768px) { ... }
@media (max-width: 480px) { ... }
@media print { ... }
```
- `screen`: Màn hình. `print`: In ấn. `all`: Tất cả.
- Toán tử: `and`, `not`, `,` (tương đương OR).

### 6.5 Responsive Images
```html
<img
  src="image-400.jpg"
  srcset="image-400.jpg 400w, image-800.jpg 800w"
  sizes="(max-width: 600px) 400px, 800px"
  alt="Mô tả ảnh"
>
```
Trình duyệt tự chọn ảnh phù hợp nhất → tiết kiệm băng thông.

---

## 7. CSS METHODOLOGIES

### BEM (Phổ biến nhất)
```css
/* Block */           .menu { }
/* Element */         .menu__item { }
/* Modifier */        .menu__item--active { }
```
> **Quy tắc vàng**: Chỉ dùng class selector. Không dùng ID, không dùng tag để style.

### OOCSS
- Tách cấu trúc (layout) và trang trí (màu, font) thành 2 class riêng.
- Nội dung không phụ thuộc vào container chứa nó.

### SMACSS – 5 lớp
1. **Base**: Style mặc định cho tag (reset, normalize).
2. **Layout**: Phân chia trang (header, footer, sidebar).
3. **Module**: Khối tái sử dụng.
4. **State**: Trạng thái (`.is-active`, `.is-hidden`).
5. **Theme**: Chủ đề giao diện có thể thay thế.

### Atomic CSS / Utility-first
1 class = 1 thuộc tính (`mt-10`, `text-center`). Nền tảng của **Tailwind CSS**.
- ✅ CSS rất nhỏ. ❌ HTML cồng kềnh, thiếu ngữ nghĩa.

---

## 8. JAVASCRIPT

### 8.1 JavaScript là gì?
Ngôn ngữ lập trình **thông dịch, đơn luồng** chạy trên trình duyệt (và Node.js). Giúp trang web có tính tương tác động.

### 8.2 Kiểu dữ liệu (Types)
**2 nhóm chính:**
- **Primitive (Tham trị):** `String`, `Number`, `BigInt`, `Boolean`, `Undefined`, `Symbol`, `Null` – gán là copy giá trị.
- **Reference (Tham chiếu):** `Object` (gồm `Array`, `Function`, `Date`...) – gán là copy địa chỉ bộ nhớ.

**So sánh `==` vs `===`:**
- `==`: Tự ép kiểu trước khi so sánh. `5 == "5"` → `true`.
- `===`: Nghiêm ngặt, không ép kiểu. `5 === "5"` → `false`.
- `null == undefined` → `true`. `null === undefined` → `false`.
- `NaN == NaN` → `false`. Kiểm tra bằng `Number.isNaN()`.
- `{a:1} == {a:1}` → `false` (so sánh theo địa chỉ tham chiếu).
- `typeof NaN` → `"number"` (quirk của JS).

### 8.3 var / let / const
| | `var` | `let` | `const` |
|---|---|---|---|
| **Scope** | Function | Block | Block |
| **Hoisting** | Có (undefined) | Có (TDZ – lỗi nếu dùng trước khai báo) | Có (TDZ) |
| **Reassign** | Được | Được | Không được |

> **Khuyên dùng**: Luôn dùng `const`, chỉ dùng `let` khi cần reassign. Tránh `var`.

### 8.4 Scope, Closure, Context (`this`)
- **Scope**: Phạm vi truy cập biến. Có 3 loại: Global, Function, Block.
- **Closure**: Hàm con ghi nhớ và truy cập được biến của hàm cha **dù hàm cha đã chạy xong**.
  ```javascript
  function createCounter() {
    let count = 0;
    return function() { return ++count; };
  }
  const counter = createCounter();
  counter(); // 1
  counter(); // 2
  ```
- **`this`**: Trỏ đến object gọi hàm. Phụ thuộc vào **cách hàm được gọi**. Arrow function không có `this` riêng – kế thừa từ scope bao ngoài.

### 8.5 Prototype & Class
- **Prototype chain**: Cơ chế kế thừa trong JS – mỗi object có `__proto__` trỏ đến prototype của constructor.
- **Class** (ES6): Cú pháp đẹp hơn, thực chất vẫn là prototype-based.
  ```javascript
  class Animal {
    constructor(name) { this.name = name; }
    speak() { return `${this.name} kêu!`; }
  }
  class Dog extends Animal {
    speak() { return `${this.name} sủa!`; }
  }
  ```

### 8.6 Bất đồng bộ (Async) – Event Loop
**JavaScript đơn luồng**, xử lý bất đồng bộ qua **Event Loop**:
1. Chạy hết code đồng bộ trong **Call Stack**.
2. Xử lý tất cả **Microtasks** (Promise `.then`, `queueMicrotask`).
3. Lấy 1 **Macrotask** (`setTimeout`, `setInterval`, I/O) rồi lặp lại.

> **Microtask luôn chạy trước Macrotask tiếp theo.**

```javascript
console.log("A");                                    // 1 – đồng bộ
setTimeout(() => console.log("B"), 0);               // 4 – Macrotask
Promise.resolve().then(() => console.log("C"));      // 3 – Microtask
console.log("D");                                    // 2 – đồng bộ
// Kết quả: A → D → C → B
```

### 8.7 Promise & Async/Await
```javascript
// Promise
fetch("/api/data")
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));

// Async/Await (cú pháp sạch hơn)
async function getData() {
  try {
    const res = await fetch("/api/data");
    return await res.json();
  } catch (err) {
    console.error(err);
  }
}
```
- `Promise.all([...])`: Chạy song song, lỗi 1 là fail toàn bộ.
- `Promise.allSettled([...])`: Chạy song song, trả kết quả dù lỗi.
- `Promise.race([...])`: Lấy kết quả cái nào xong trước.

### 8.8 Array Methods phổ biến
```javascript
const arr = [1, 2, 3, 4, 5];

arr.map(x => x * 2);                    // [2,4,6,8,10] – biến đổi, trả array mới
arr.filter(x => x > 2);                 // [3,4,5] – lọc, trả array mới
arr.reduce((acc, x) => acc + x, 0);     // 15 – gộp thành 1 giá trị
arr.find(x => x > 3);                   // 4 – phần tử đầu tiên thỏa mãn
arr.findIndex(x => x > 3);              // 3 – index của phần tử đó
arr.some(x => x > 4);                   // true – có ít nhất 1 thỏa mãn
arr.every(x => x > 0);                  // true – tất cả thỏa mãn
arr.includes(3);                        // true – kiểm tra tồn tại
arr.flat(depth);                        // Làm phẳng mảng lồng nhau
```

### 8.9 ES6+ Cú pháp quan trọng
```javascript
// Destructuring
const { name, age } = user;
const [first, ...rest] = arr;

// Spread / Rest
const newArr = [...arr1, ...arr2];
function sum(...args) { return args.reduce((a,b) => a+b, 0); }

// Template Literals
const msg = `Xin chào, ${name}!`;

// Optional Chaining
const city = user?.address?.city;

// Nullish Coalescing
const name = user.name ?? "Ẩn danh"; // fallback khi null/undefined (khác || fallback khi falsy)

// Modules
import { func } from './utils.js';
export default MyComponent;
```

### 8.10 DOM Manipulation
```javascript
// Tìm kiếm
document.querySelector(".class");
document.querySelectorAll("li");

// Thay đổi
el.textContent = "text";
el.innerHTML = "<b>HTML</b>";
el.setAttribute("href", "/path");
el.classList.add("active");
el.classList.toggle("visible");

// Tạo / xóa
const div = document.createElement("div");
parent.appendChild(div);
parent.removeChild(child);

// Event
el.addEventListener("click", (e) => {
  e.preventDefault();   // Ngăn hành vi mặc định
  e.stopPropagation();  // Ngăn event bubbling lên cha
});
```

**Event Delegation**: Đặt listener trên cha, kiểm tra `e.target` để xử lý – hiệu quả hơn gắn listener cho từng con.

### 8.11 Các khái niệm nâng cao quan trọng

**Hoisting**: `var` và khai báo hàm được đưa lên đầu scope. `let/const` có TDZ (Temporal Dead Zone) – lỗi nếu dùng trước khai báo.

**Debounce vs Throttle**:
- **Debounce**: Chỉ gọi hàm sau khi người dùng ngừng hành động X ms (VD: search input).
- **Throttle**: Gọi tối đa 1 lần mỗi X ms dù sự kiện liên tục (VD: scroll, resize).

**Deep Clone vs Shallow Clone**:
```javascript
const shallow = { ...obj };                         // Shallow – không copy nested
const deep = structuredClone(obj);                  // Deep – chuẩn nhất (ES2022)
const deep2 = JSON.parse(JSON.stringify(obj));       // Deep – đơn giản, mất function
```

**Coercion (Ép kiểu)**:
- `"5" - 1` → `4` (string ép thành number khi dùng `-`).
- `"5" + 1` → `"51"` (number ép thành string vì `+` ưu tiên nối chuỗi).

---

## 9. CÁC KHÁI NIỆM WEB TỔNG QUÁT

### 9.1 SPA vs MPA
| | SPA (Single Page App) | MPA (Multi Page App) |
|---|---|---|
| **Ví dụ** | React, Vue, Angular app | Website truyền thống |
| **Điều hướng** | JS cập nhật DOM, không reload | Reload toàn bộ trang |
| **Ưu** | Trải nghiệm mượt mà | SEO tốt hơn tự nhiên |
| **Nhược** | SEO khó hơn, load lần đầu chậm | Chuyển trang chậm |

### 9.2 CSR vs SSR vs SSG
| | CSR | SSR | SSG |
|---|---|---|---|
| **Render ở** | Client (trình duyệt) | Server (mỗi request) | Build time |
| **Load lần đầu** | Chậm | Nhanh | Rất nhanh |
| **SEO** | Kém | Tốt | Rất tốt |
| **Ví dụ** | React thuần | Next.js | Gatsby |

### 9.3 CORS
Cơ chế bảo mật trình duyệt ngăn Frontend (domain A) gọi API từ Backend (domain B) nếu server B không cho phép qua header `Access-Control-Allow-Origin`.

### 9.4 HTTP Methods & Status Codes
| Method | Dùng để |
|---|---|
| `GET` | Lấy dữ liệu |
| `POST` | Tạo mới |
| `PUT` | Cập nhật toàn bộ |
| `PATCH` | Cập nhật một phần |
| `DELETE` | Xóa |

| Code | Ý nghĩa |
|---|---|
| `200` | OK |
| `201` | Created |
| `301/302` | Redirect |
| `400` | Bad Request |
| `401` | Unauthorized (chưa đăng nhập) |
| `403` | Forbidden (không có quyền) |
| `404` | Not Found |
| `500` | Internal Server Error |

### 9.5 Browser Rendering Pipeline
```
Parse HTML → DOM Tree
Parse CSS  → CSSOM Tree
           → Render Tree
           → Layout (Reflow) – tính vị trí, kích thước
           → Paint – vẽ pixels
           → Composite – gộp layers
```
> **Reflow** (thay đổi layout) tốn kém hơn **Repaint** (thay đổi màu sắc). Hạn chế thao tác DOM thừa.

### 9.6 Web Performance – Tối ưu
- Minify CSS/JS, dùng CDN.
- Lazy load ảnh (`loading="lazy"`).
- Code splitting – chỉ tải JS khi cần.
- Cache với `Cache-Control`, Service Worker.
- Dùng `async`/`defer` cho `<script>`.
- Tối ưu Core Web Vitals (LCP < 2.5s, INP < 200ms, CLS < 0.1).

---

## 10. BÀI TẬP THỰC HÀNH

**Bài 1 – Kiểu dữ liệu:**
```javascript
console.log([] == ![]);     // ?
console.log(NaN === NaN);   // ?
console.log(typeof null);   // ?
```
> **Đáp án**: `true` | `false` | `"object"`
> - `![]` = `false`, cả hai bị ép thành `0` nên bằng nhau.
> - NaN không bằng chính nó.
> - `typeof null` là quirk lịch sử của JS.

---

**Bài 2 – Event Loop:**
```javascript
console.log("A");
setTimeout(() => console.log("B"), 0);
Promise.resolve().then(() => console.log("C"));
console.log("D");
```
> **Đáp án**: `A → D → C → B`
> - A, D: đồng bộ (Call Stack) → C: Microtask (Promise) → B: Macrotask (setTimeout)

---

**Bài 3 – Closure:**
```javascript
// Hãy viết hàm createGreeting sao cho:
const sayHello = createGreeting("Xin chào");
console.log(sayHello("Alice")); // "Xin chào, Alice"
```
> **Đáp án:**
> ```javascript
> function createGreeting(greeting) {
>   return function(name) {
>     return `${greeting}, ${name}`;
>   };
> }
> ```

---

## 11. CSS HIỆN ĐẠI (2024–2026)

### 11.1 CSS Container Queries
Trước đây chỉ có **Media Queries** (responsive theo viewport). Container Queries cho phép responsive theo **kích thước của phần tử cha** – phù hợp hơn cho component-based design.

```css
/* 1. Khai báo container */
.card-wrapper {
  container-type: inline-size;
  container-name: card;
}

/* 2. Style con dựa theo kích thước container cha */
@container card (min-width: 400px) {
  .card {
    display: flex;
    flex-direction: row;
  }
}
```

> **Tại sao quan trọng?** Cùng 1 component `.card` có thể hiển thị theo cột khi ở sidebar nhỏ, và theo hàng khi ở main content rộng – mà không cần biết viewport là bao nhiêu. Hỗ trợ: Chrome 105+, Firefox 110+, Safari 16+ ✅

### 11.2 CSS `@layer` (Cascade Layers)
Giải quyết vấn đề specificity conflict mà không cần dùng `!important`.

```css
/* Khai báo thứ tự ưu tiên – layer sau ghi đè layer trước */
@layer base, components, utilities;

@layer base {
  a { color: blue; }
}

@layer components {
  .btn { color: white; background: green; }
}

@layer utilities {
  .text-red { color: red; } /* Luôn thắng dù specificity thấp */
}
```

> **Ý nghĩa**: Style trong layer sau luôn thắng layer trước, **bất kể specificity**. Rất hữu ích khi nhập CSS từ thư viện bên thứ 3 mà không muốn bị ghi đè.

### 11.3 View Transitions API
Tạo animation mượt mà khi chuyển đổi nội dung – **native, không cần thư viện**.

```javascript
document.startViewTransition(() => {
  updateContent(); // Thay đổi DOM bên trong
});
```

```css
::view-transition-old(root) { animation: fade-out 0.3s ease; }
::view-transition-new(root) { animation: fade-in 0.3s ease; }
```

> **Ứng dụng**: Chuyển trang SPA mượt mà, shared element transition (ảnh "bay" từ list sang detail). Hỗ trợ Chrome 111+, Safari 18+.

---

## 12. TYPESCRIPT CƠ BẢN

### 12.1 TypeScript là gì?
**TypeScript (TS)** là JavaScript có thêm **kiểu dữ liệu tĩnh (static typing)**, compile thành JS trước khi chạy.

```
TypeScript (.ts) → Compile (tsc) → JavaScript (.js) → Trình duyệt
```

**Lợi ích**: Phát hiện lỗi khi viết code, autocomplete tốt hơn, dễ maintain. **Gần như bắt buộc trong hầu hết job Frontend 2024–2026.**

### 12.2 Kiểu dữ liệu cơ bản
```typescript
let name: string = "Alice";
let age: number = 25;
let isActive: boolean = true;
let scores: number[] = [1, 2, 3];
let point: [number, number] = [10, 20]; // Tuple

// any – tránh dùng (mất hết lợi ích TS)
// unknown – an toàn hơn any, phải check type trước khi dùng
let value: unknown = getData();
if (typeof value === "string") console.log(value.toUpperCase());

function log(msg: string): void { console.log(msg); }       // void – không return
function fail(msg: string): never { throw new Error(msg); } // never – không kết thúc
```

### 12.3 Interface & Type Alias
```typescript
// Interface – dùng cho object shape, có thể extend
interface User {
  id: number;
  name: string;
  email?: string;       // Tùy chọn
  readonly createdAt: Date; // Không thể thay đổi sau khi tạo
}

// Type Alias – linh hoạt hơn, dùng cho union/intersection
type ID = string | number;
type Status = "active" | "inactive" | "pending"; // Union type (literal)
type AdminUser = User & { role: "admin" };        // Intersection type
```

> **Khi nào dùng cái nào?** `interface` cho object/class definition. `type` cho union, tuple, complex types.

### 12.4 Generics
```typescript
function getFirst<T>(arr: T[]): T { return arr[0]; }

getFirst<number>([1, 2, 3]); // 1
getFirst<string>(["a", "b"]); // "a"
```

### 12.5 Utility Types phổ biến
```typescript
interface User { id: number; name: string; email: string; age: number; }

type PartialUser   = Partial<User>;           // Tất cả thành optional
type UserPreview   = Pick<User, "id" | "name">; // Chọn 1 số thuộc tính
type UserWithoutAge = Omit<User, "age">;       // Bỏ 1 số thuộc tính
type ReadonlyUser  = Readonly<User>;           // Tất cả không thể thay đổi
type UserMap       = Record<string, User>;     // Object map key-value
```

### 12.6 TypeScript với React
```typescript
interface ButtonProps {
  label: string;
  onClick: () => void;
  disabled?: boolean;
  variant?: "primary" | "secondary";
}

const Button: React.FC<ButtonProps> = ({ label, onClick, disabled = false }) => (
  <button onClick={onClick} disabled={disabled}>{label}</button>
);

// useState với type
const [count, setCount] = useState<number>(0);
const [user, setUser] = useState<User | null>(null);

// useRef
const inputRef = useRef<HTMLInputElement>(null);
```

---

## 13. CÔNG CỤ & HỆ SINH THÁI HIỆN ĐẠI

### 13.1 Package Manager
| Công cụ | Đặc điểm |
|---|---|
| **npm** | Mặc định với Node.js |
| **yarn** | Nhanh hơn, lock file nhất quán |
| **pnpm** | Tiết kiệm disk space, nhanh (2024 trend) |
| **bun** | Runtime + package manager, siêu nhanh |

### 13.2 Build Tools
| Công cụ | Đặc điểm |
|---|---|
| **Vite** | Dev server cực nhanh (ESM native). **Chuẩn hiện tại 2024–2026** |
| **Webpack** | Vẫn nhiều dự án dùng, cấu hình phức tạp |
| **esbuild** | Cực nhanh (viết bằng Go), core của nhiều tool khác |
| **Turbopack** | Successor của Webpack, tích hợp trong Next.js |

### 13.3 Framework & Thư viện
| Tên | Loại | Nổi bật |
|---|---|---|
| **React 18+** | UI Library | Concurrent Mode, Server Components |
| **Next.js 14+** | Full-stack | App Router, Server Actions |
| **Vue 3** | Framework | Composition API, nhỏ gọn |
| **Astro** | Static/SSR | Islands architecture, 0 JS mặc định |
| **Svelte/SvelteKit** | Compiler | Không có Virtual DOM, code gọn |

### 13.4 State Management
| Tên | Khi nào dùng |
|---|---|
| `useState` / `useReducer` | Local state đơn giản |
| **Context API** | Global state nhỏ, ít update |
| **Zustand** | Global state gọn nhẹ (trending 2024) |
| **TanStack Query** | Async/server state (cache, sync) |
| **Redux Toolkit** | Complex state trong app rất lớn |

### 13.5 Testing
| Loại | Công cụ |
|---|---|
| **Unit test** | Vitest (nhanh, tích hợp Vite), Jest |
| **Component test** | React Testing Library |
| **E2E test** | Playwright (chuẩn 2024+), Cypress |

---

## 14. CÂU HỎI PHỎNG VẤN HAY GẶP

### CSS
- **`display: none` vs `visibility: hidden`?**
  > `none`: Xóa khỏi layout, không chiếm chỗ. `hidden`: Ẩn nhưng vẫn chiếm chỗ.
- **`em` vs `rem`?**
  > `rem` an toàn hơn – luôn tính từ root, không bị ảnh hưởng bởi nesting.
- **Stacking context là gì?**
  > Ngữ cảnh xếp chồng, tạo ra bởi `position` + `z-index`, `opacity < 1`, `transform`... Z-index chỉ so sánh trong cùng stacking context.

### JavaScript
- **`null` vs `undefined`?**
  > `undefined`: Biến khai báo nhưng chưa gán. `null`: Giá trị rỗng được gán cố ý.
- **`call` vs `apply` vs `bind`?**
  > Đều thay đổi `this`. `call(ctx, a, b)` gọi ngay. `apply(ctx, [a,b])` gọi ngay bằng mảng. `bind(ctx)` trả về hàm mới.
- **Debounce vs Throttle?**
  > Debounce: chờ người dùng ngừng rồi mới gọi (search input). Throttle: gọi tối đa 1 lần/X ms (scroll, resize).
- **Shallow copy vs Deep copy?**
  > `{...obj}` là shallow. `structuredClone(obj)` là deep copy chuẩn nhất.

### React
- **`useEffect` cleanup function dùng để làm gì?**
  > Dọn dẹp side effects (hủy subscription, clearTimeout...) khi component unmount hoặc dependency thay đổi.
- **`useMemo` vs `useCallback`?**
  > `useMemo`: Ghi nhớ **kết quả tính toán**. `useCallback`: Ghi nhớ **hàm** (tránh tạo lại mỗi render).
- **Key trong list dùng để làm gì?**
  > Giúp React xác định phần tử nào thay đổi. Key phải unique và ổn định – **không dùng index nếu list thay đổi thứ tự**.
- **Virtual DOM là gì?**
  > Bản sao nhẹ của DOM thật trong bộ nhớ. React so sánh (diff) để tìm thay đổi tối thiểu rồi mới cập nhật DOM thật.

### Git
- **`git stash` dùng khi nào?**
  > Cần chuyển nhánh gấp nhưng code đang dang dở chưa muốn commit – stash lưu tạm, pop lại sau.
- **`git cherry-pick` là gì?**
  > Áp dụng 1 commit cụ thể từ nhánh khác vào nhánh hiện tại mà không merge toàn bộ.

