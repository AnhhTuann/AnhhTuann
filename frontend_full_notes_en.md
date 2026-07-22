# 📚 Front-End Knowledge Summary – Complete & Concise

---

## 1. GIT

### 1.1 Core Concepts
- **What is Git?** A Version Control System (VCS) that tracks changes to source code over time.
- **Git vs GitHub:** Git is software running locally on your machine. GitHub is an online platform for hosting repos in the cloud.

### 1.2 Working Architecture – 3 Areas
| Area | Role |
|---|---|
| **Working Directory** | The project folder you're actively editing |
| **Staging Area** | Where you select which files to include in the next commit |
| **Repository** | Where Git stores the full history of changes |

> **Basic flow:** Edit file → `git add` → `git commit` → history saved

### 1.3 Key Comparisons

**Merge vs Rebase**
- `Merge`: Combines branches, preserves the full real history, creates a "merge commit". **Safe for team collaboration.**
- `Rebase`: Moves commits on top of another branch tip, results in a clean linear history. **Never rebase a shared/pushed branch.**

**Reset vs Revert**
- `Reset`: Rolls back to a previous commit, **rewrites history**. Use locally only.
  - `--soft`: keeps code + staging
  - `--mixed` (default): keeps code
  - `--hard`: deletes everything
- `Revert`: Creates a **new commit** to undo a previous one. Preserves history — **safe for shared repos.**

### 1.4 GitFlow – 5 Branch Types
| Branch | Role |
|---|---|
| `main` | Production (live) |
| `develop` | Ongoing development |
| `feature/*` | New features |
| `release/*` | Pre-release testing & bug fixing |
| `hotfix/*` | Urgent fixes directly on production |

### 1.5 Commands to Know by Heart
```bash
git init / git clone          # Initialize / clone a repo
git status / git log          # Check status / view commit history
git add / git commit          # Stage files / save to history
git branch / git checkout     # Create-view branches / switch branch
git merge                     # Merge a branch
git push / git pull           # Upload / sync code from remote
git stash / git stash pop     # Temporarily shelve / restore changes
git cherry-pick <hash>        # Apply a specific commit from another branch
```

---

## 2. HTML

### 2.1 What is HTML?
**HTML (HyperText Markup Language)** – a markup language used to define the structure and content of web pages using a system of tags.

**HTML vs XHTML vs HTML5:**
- `HTML`: Flexible syntax, closing some tags is optional.
- `XHTML`: Strict, all tags must be closed, based on XML.
- `HTML5`: The current standard. Adds semantic tags, rich APIs (Canvas, WebSocket, Geolocation, Web Workers...), Web Storage, and native audio/video support.

### 2.2 DOCTYPE & Basic Structure
```html
<!DOCTYPE html>   <!-- Declares HTML5, must be the first line -->
<html>
  <head>          <!-- Metadata: title, meta, link, style -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Page Title</title>
  </head>
  <body>          <!-- All visible page content -->
  </body>
</html>
```
> No `DOCTYPE` → browser enters **quirks mode**, which can cause inconsistent CSS/box model rendering.

### 2.3 Tag vs Element | Block vs Inline vs Inline-block
- **Tag** is the markup syntax (`<p>`, `</p>`). **Element** = opening tag + content + closing tag (`<p>Hello</p>`).

| Type | Characteristics | Examples |
|---|---|---|
| **Block** | Takes full width, starts on a new line, accepts width/height | `div`, `p`, `h1-h6`, `section` |
| **Inline** | Takes only necessary space, no new line, no width/height | `span`, `a`, `strong` |
| **Inline-block** | Same line as inline, but accepts width/height | `button`, `input`, `img` |

### 2.4 Attributes
- Syntax: `name="value"` written inside the opening tag.
- **Boolean attribute**: presence means `true` (e.g., `disabled`, `checked`, `required`).
- **Custom data attribute**: `data-user-id="123"` – access via JS: `element.dataset.userId`.
- **id**: Must be unique per page. **class**: Reusable, one element can have multiple classes.

### 2.5 Semantic HTML
Use meaningful tags instead of generic `div/span` → better **SEO** and **Accessibility**.

| Tag | Role |
|---|---|
| `<header>` | Page or section header |
| `<nav>` | Primary navigation links |
| `<main>` | Main content (only 1 per page) |
| `<section>` | Grouped related content, usually has a heading |
| `<article>` | Self-contained content (blog post, card) |
| `<aside>` | Supplementary content (sidebar, ads) |
| `<footer>` | Page or section footer |
| `<figure>` + `<figcaption>` | Media content + caption |
| `<time datetime="">` | Dates/times (important for SEO) |
| `<details>` + `<summary>` | Native accordion, no JS needed |

### 2.6 HTML Forms
**Key components:**
- `<label>`: Always associate with an input (via `for`/`id` or wrapping). Increases click area.
- `<input>` types: `text`, `password`, `email`, `number`, `tel`, `date`, `checkbox`, `radio`, `file`, `hidden`, `submit`.
- `<select>`: Fixed dropdown. `<datalist>`: Autocomplete suggestions.
- `<fieldset>` + `<legend>`: Group related form controls.

**Important states:**
- `readonly`: Cannot edit, but **still submits**.
- `disabled`: Cannot focus, **does not submit**.

**HTML5 Validation:** `required`, `pattern`, `min/max`, `minlength/maxlength`.

**GET vs POST:**
- `GET`: Data in URL, size-limited, for searches/filtering.
- `POST`: Data in body, no size limit, for sensitive forms. (POST is NOT inherently more secure than GET — always use HTTPS.)

### 2.7 Notable Web APIs (HTML5)
| API | Used for |
|---|---|
| **Canvas** | Pixel-based graphics with JS (games) |
| **SVG** | Vector graphics, scalable, accessible |
| **Web Storage** | `localStorage` (persistent ~5MB), `sessionStorage` (cleared on tab close) |
| **IndexedDB** | NoSQL database in the browser for large data |
| **Web Worker** | Run JS in a background thread, non-blocking |
| **Service Worker + PWA** | Offline caching, push notifications, native-like experience |
| **WebSocket** | Persistent two-way real-time connection (chat, live data) |
| **History API** | Manipulate browser history without reloading (foundation of SPA routing) |
| **Intersection Observer** | Track element entering/leaving viewport (lazy load, infinite scroll) |
| **Geolocation API** | Get device location coordinates |

### 2.8 Web Accessibility (A11y)
- **WCAG** – 3 levels (A, AA, AAA). Principles: Perceivable, Operable, Understandable, Robust.
- **Color contrast**: Minimum 4.5:1 ratio (WCAG AA).
- **Heading hierarchy**: Screen readers navigate via `h1-h6`, don't skip levels, 1 `<h1>` per page.
- **Alt text**: Informational images → brief description. Decorative images → `alt=""`.
- **Keyboard navigation**: All features must work with Tab/Enter/Space/Escape.
- **tabindex**: `0` (natural tab order), `-1` (focus via JS only). Avoid `>0`.
- **ARIA**: `aria-label`, `aria-labelledby`, `aria-describedby`, `aria-live` – adds semantic meaning for screen readers.

### 2.9 Basic SEO
```html
<title>Page Title (50-60 characters)</title>
<meta name="description" content="Description (150-160 chars), affects CTR">
<link rel="canonical" href="https://example.com/canonical-url"> <!-- Prevent duplicate content -->

<!-- Open Graph (controls appearance when link is shared on social media) -->
<meta property="og:title" content="...">
<meta property="og:image" content="...">
```
- **XML Sitemap**: Helps Google bots discover and crawl pages.
- **Robots.txt**: Blocks crawlers at the site/path level.
- **Structured data (Schema.org / JSON-LD)**: Enables rich snippets (ratings, prices) in Google results.
- **Core Web Vitals**: LCP < 2.5s, INP < 200ms, CLS < 0.1 – official Google ranking factors.

---

## 3. CSS

### 3.1 What is CSS?
**CSS (Cascading Style Sheets)** – a language for styling and formatting HTML documents.

**3 ways to write CSS:**
- `Inline`: `style=""` directly on the tag.
- `Internal`: `<style>` inside `<head>`.
- `External`: Separate `.css` file, linked via `<link>`.

### 3.2 Selectors
| Selector | Syntax | Example |
|---|---|---|
| Element | `tag` | `p {}` |
| Class | `.class` | `.btn {}` |
| ID | `#id` | `#header {}` |
| Universal | `*` | `* { margin: 0 }` |
| Attribute | `[attr="val"]` | `input[type="text"] {}` |
| Pseudo-class | `:hover`, `:nth-child(n)`, `:not()` | `a:hover {}` |
| Pseudo-element | `::before`, `::after`, `::first-letter` | `p::before {}` |

**CSS Combinators:**
- `div p` (Descendant – all levels deep)
- `div > p` (Child – direct children only)
- `h1 + p` (Adjacent Sibling – immediately after)
- `h1 ~ p` (General Sibling – all siblings after)

### 3.3 Units
| Unit | Type | Meaning |
|---|---|---|
| `px` | Absolute | Fixed pixel |
| `em` | Relative | Relative to parent's font-size |
| `rem` | Relative | Relative to root (`<html>`) font-size |
| `%` | Relative | Relative to parent |
| `vw / vh` | Relative | % of viewport width / height |

### 3.4 Box Model
```
Margin → Border → Padding → Content (Width × Height)
```
- `box-sizing: content-box` (default): width only counts Content.
- `box-sizing: border-box` **(recommended)**: width includes Padding + Border.

### 3.5 Display & Position
**Display:**
| Value | Characteristics |
|---|---|
| `block` | Full width, new line |
| `inline` | Same line, no width/height |
| `inline-block` | Same line + accepts width/height |
| `none` | Completely hidden, takes no space |
| `flex` / `grid` | Modern layout models |

**Position:**
| Value | Characteristics |
|---|---|
| `static` | Default, follows normal document flow |
| `relative` | Offset from its original position, keeps original space |
| `absolute` | Positioned relative to nearest ancestor with `position` ≠ `static` |
| `fixed` | Fixed relative to the browser window |
| `sticky` | Acts as `relative`, turns `fixed` when scrolling past a threshold |

### 3.6 Inheritance
- **Inherited** (text-related): `color`, `font-size`, `font-family`, `text-align`, `line-height`.
- **Not inherited** (layout-related): `margin`, `padding`, `border`, `width`, `height`, `background`.

### 3.7 Specificity (Priority)
```
!important > Inline style > ID > Class/Pseudo-class > Element
```
> Avoid `!important` – hard to override later. Avoid using `id` for styling.

### 3.8 Common CSS Pitfalls
- **Margin Collapsing**: Top/bottom margins of adjacent blocks merge into one (takes the larger value, not the sum).
- **Float & Clearfix**: Parent collapses to zero height when children use float → use `::after` clearfix.
- **Z-index**: Only works within the same Stacking Context — if z-index isn't working, check the parent element.

---

## 4. CSS PREPROCESSORS & POSTPROCESSORS

### 4.1 What is a Preprocessor?
Extends CSS with programming-like features, then **compiles** to plain CSS.

```
SCSS/Less/Stylus → Compile → Plain CSS → Browser
```

**Core features:**
- **Variables**: Store colors, font sizes, etc. and reuse everywhere.
- **Nesting**: Write CSS nested like HTML structure.
- **Mixins**: Reusable groups of properties (like functions).
- **Modularization**: Split into multiple small files (`_variables.scss`, `_header.scss`...).

**Popular preprocessors:**
| Name | Characteristics |
|---|---|
| **SCSS/Sass** | Most popular, CSS-like syntax |
| **Less** | Easy to learn, uses `@` for variables |
| **Stylus** | Flexible syntax, no `{}` or `;` required |

### 4.2 What is a Postprocessor?
Processes **after** plain CSS is generated to optimize it.
- **Autoprefixer**: Auto-adds `-webkit-`, `-moz-`... for older browsers.
- **Minify**: Removes whitespace and comments → smaller file size.
- **Tool**: PostCSS + plugins.

```
SCSS → Compile → Plain CSS → PostCSS (prefix, minify) → Optimized CSS → Server
```

---

## 5. CSS LAYOUT

### 5.1 Flexbox (1-Dimensional)
Use when you need to **align elements in a single row or column**.

**Container (Parent) Properties:**
| Property | Description |
|---|---|
| `display: flex` | Enable Flexbox |
| `flex-direction` | Main axis direction (`row`, `column`) |
| `flex-wrap` | Allow items to wrap to next line (`wrap`, `nowrap`) |
| `justify-content` | Alignment along the main axis |
| `align-items` | Alignment along the cross axis |
| `align-content` | Alignment of multiple lines along the cross axis |
| `gap` | Space between items |

**Item (Child) Properties:**
| Property | Description |
|---|---|
| `flex-grow` | Expansion ratio when there is extra space |
| `flex-shrink` | Shrink ratio when there is not enough space |
| `flex-basis` | Default size before space is distributed |
| `flex` | Shorthand: `grow shrink basis` |
| `align-self` | Override `align-items` for this item only |
| `order` | Change the display order |

### 5.2 CSS Grid (2-Dimensional)
Use when you need to **divide an overall layout** across both rows and columns.

**Container (Parent) Properties:**
| Property | Description |
|---|---|
| `display: grid` | Enable Grid |
| `grid-template-columns` | Define columns (px, %, fr, auto) |
| `grid-template-rows` | Define rows |
| `grid-template-areas` | Visual layout map using named areas |
| `column-gap / row-gap` | Space between columns / rows |
| `justify-items / align-items` | Align items within their cells |
| `justify-content / align-content` | Align the entire grid within the container |

**Item (Child) Properties:**
- `grid-column: 1 / 3` (span from column line 1 to 3)
- `grid-row: 1 / 2`
- `grid-area: name` (used with `grid-template-areas`)

**Special units & functions:**
- `fr`: Fractional unit of remaining space (e.g., `1fr 2fr` = 1/3 and 2/3 split).
- `repeat(3, 1fr)`: Shorthand for 3 equal columns.
- `minmax(200px, 1fr)`: Not smaller than 200px, not larger than 1fr.

### 5.3 Flexbox vs Grid – When to Use Which?
| | Flexbox | CSS Grid |
|---|---|---|
| **Dimensions** | 1D (row OR column) | 2D (rows AND columns) |
| **Approach** | Content-first | Layout-first |
| **Use when** | Aligning items within a component | Defining overall page layout |

---

## 6. CSS RESPONSIVE DESIGN

### 6.1 Responsive vs Adaptive
- **Adaptive (AWD)**: Multiple versions of the site for different device types.
- **Responsive (RWD)**: Single website that auto-adjusts based on screen size using CSS. **The dominant approach today.**

### 6.2 Mobile First
Write default CSS for **mobile first**, then use `min-width` to scale up for larger screens.
```css
/* Mobile default */
.container { padding: 16px; }

/* Tablet and up */
@media (min-width: 768px) { .container { padding: 32px; } }

/* Desktop */
@media (min-width: 1024px) { .container { padding: 48px; } }
```

### 6.3 Viewport Meta Tag (Required)
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```
Without this tag → page shrinks to a tiny size on mobile.

### 6.4 Media Queries
```css
@media screen and (min-width: 768px) { ... }
@media (max-width: 480px) { ... }
@media print { ... }
```
- `screen`: Screens. `print`: Printing. `all`: All media types.
- Operators: `and`, `not`, `,` (equivalent to OR).

### 6.5 Responsive Images
```html
<img
  src="image-400.jpg"
  srcset="image-400.jpg 400w, image-800.jpg 800w"
  sizes="(max-width: 600px) 400px, 800px"
  alt="Image description"
>
```
Browser automatically selects the best-fit image → saves bandwidth.

---

## 7. CSS METHODOLOGIES

### BEM (Most Popular)
```css
/* Block */     .menu { }
/* Element */   .menu__item { }
/* Modifier */  .menu__item--active { }
```
> **Golden rule**: Use class selectors only. No IDs, no tag selectors for styling.

### OOCSS
- Separate structure (layout) from skin (colors, fonts) into distinct classes.
- Content should not depend on its container.

### SMACSS – 5 Layers
1. **Base**: Default tag styles (reset, normalize).
2. **Layout**: Page-dividing components (header, footer, sidebar).
3. **Module**: Reusable blocks.
4. **State**: States (`.is-active`, `.is-hidden`).
5. **Theme**: Swappable visual themes.

### Atomic CSS / Utility-First
1 class = 1 property (`mt-10`, `text-center`). The foundation of **Tailwind CSS**.
- ✅ Very small CSS file. ❌ Verbose HTML, lacks semantic meaning.

---

## 8. JAVASCRIPT

### 8.1 What is JavaScript?
An **interpreted, single-threaded** programming language that runs in the browser (and Node.js). It enables dynamic interaction on web pages.

### 8.2 Data Types
**2 main categories:**
- **Primitive (by value):** `String`, `Number`, `BigInt`, `Boolean`, `Undefined`, `Symbol`, `Null` – assignment copies the value.
- **Reference (by reference):** `Object` (incl. `Array`, `Function`, `Date`...) – assignment copies the memory address.

**`==` vs `===`:**
- `==`: Performs type coercion before comparison. `5 == "5"` → `true`.
- `===`: Strict, no coercion. `5 === "5"` → `false`.
- `null == undefined` → `true`. `null === undefined` → `false`.
- `NaN == NaN` → `false`. Check with `Number.isNaN()`.
- `{a:1} == {a:1}` → `false` (compared by reference, not value).
- `typeof NaN` → `"number"` (a historical quirk of JS).

### 8.3 `var`, `let`, `const` Differences (Crucial)

| Behavior | `var` (Legacy) | `let` (ES6) | `const` (ES6) |
|---|---|---|---|
| **Scope** | `Function` (lives inside entire function) | `Block` (dies outside `{}`) | `Block` (dies outside `{}`) |
| **Reassign** | ✅ Yes | ✅ Yes | ❌ No |
| **Redeclare** | ✅ Yes | ❌ No | ❌ No |
| **Hoisting** | Hoisted and initialized with `undefined` | Hoisted but trapped in TDZ → Error | Hoisted but trapped in TDZ → Error |

**1. Scope:**
- `var`: Only scoped by functions. If declared inside `if {}` or `for {}`, it leaks out.
- `let` / `const`: Block-scoped. Trapped by the closest `{}` braces.
```javascript
if (true) {
  var a = 1;
  let b = 2;
}
console.log(a); // ✅ 1 (var leaks out)
console.log(b); // ❌ Error (let is trapped)
```

**2. Reassignment:**
- Use `let` when the value will change (e.g., counters, loops).
- Use `const` for fixed values. **Note:** Using `const` with Objects/Arrays prevents reassignment to a new Object/Array, but **mutating their properties is still allowed**.
```javascript
const user = { name: "A" };
user.name = "B";  // ✅ Mutating property is OK
user = {};        // ❌ Error: Reassigning a constant
```

**3. Hoisting:**
All three are hoisted to the top of their scope by JS, but handled differently:
```javascript
console.log(name); // ✅ undefined (code doesn't crash)
var name = "Tuan";

console.log(age);  // ❌ ReferenceError (crashes due to TDZ - Temporal Dead Zone)
let age = 25; 
```

> **🔥 BEST PRACTICES:**
> - Default to `const`.
> - If you know the variable will be reassigned (e.g., `count++`), switch to `let`.
> - **Never use `var`** in modern code.

### 8.4 Scope, Closure, Context (`this`)

**1. Scope:**
Where a variable can be seen and used. There are 3 main types:
- **Global Scope:** Declared at the top level, accessible EVERYWHERE.
  ```javascript
  const globalVar = "Hello";
  function test() { console.log(globalVar); } // ✅ Works perfectly
  ```
- **Function Scope:** Declared inside a function (especially using `var`), only accessible within that function.
  ```javascript
  function test() {
    var funcVar = "Hi";
  }
  console.log(funcVar); // ❌ Error: funcVar is not defined
  ```
- **Block Scope:** Declared using `let` or `const` inside `{}` (like `if`, `for`). It dies once outside the `{}`.
  ```javascript
  if (true) {
    let blockVar = "Hey";
  }
  console.log(blockVar); // ❌ Error: blockVar is not defined
  ```
- **Closure**: An inner function that **remembers and can access variables from its outer function** even after the outer function has returned.
  ```javascript
  function createCounter() {
    let count = 0;
    return function() { return ++count; };
  }
  const counter = createCounter();
  counter(); // 1
  counter(); // 2
  ```
- **`this`**: Refers to the object calling the function. Depends on **how the function is invoked**, not where it's defined. Arrow functions inherit `this` from their surrounding lexical scope.

### 8.5 Prototype & Class
- **Prototype chain**: Every object has `__proto__` pointing to its constructor's prototype. This is JS's inheritance mechanism.
- **Class** (ES6): Cleaner syntax, but still prototype-based under the hood.
  ```javascript
  class Animal {
    constructor(name) { this.name = name; }
    speak() { return `${this.name} makes a sound!`; }
  }
  class Dog extends Animal {
    speak() { return `${this.name} barks!`; }
  }
  ```

### 8.6 Async – Event Loop
**JavaScript is single-threaded**, handling async via the **Event Loop**:
1. Run all synchronous code in the **Call Stack**.
2. Process all **Microtasks** (Promise `.then`, `queueMicrotask`).
3. Take 1 **Macrotask** (`setTimeout`, `setInterval`, I/O) then repeat.

> **Microtasks always run before the next Macrotask.**

```javascript
console.log("A");                                    // 1 – sync
setTimeout(() => console.log("B"), 0);               // 4 – Macrotask
Promise.resolve().then(() => console.log("C"));      // 3 – Microtask
console.log("D");                                    // 2 – sync
// Output: A → D → C → B
```

### 8.7 Promise & Async/Await
```javascript
// Promise
fetch("/api/data")
  .then(res => res.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));

// Async/Await (cleaner syntax)
async function getData() {
  try {
    const res = await fetch("/api/data");
    return await res.json();
  } catch (err) {
    console.error(err);
  }
}
```
- `Promise.all([...])`: Runs in parallel, fails if any one fails.
- `Promise.allSettled([...])`: Runs in parallel, returns all results regardless of failure.
- `Promise.race([...])`: Returns the result of whichever resolves/rejects first.

### 8.8 Common Array Methods
```javascript
const arr = [1, 2, 3, 4, 5];

arr.map(x => x * 2);                    // [2,4,6,8,10] – transform, returns new array
arr.filter(x => x > 2);                 // [3,4,5] – filter, returns new array
arr.reduce((acc, x) => acc + x, 0);     // 15 – reduce to a single value
arr.find(x => x > 3);                   // 4 – first element matching condition
arr.findIndex(x => x > 3);              // 3 – index of that element
arr.some(x => x > 4);                   // true – at least one matches
arr.every(x => x > 0);                  // true – all match
arr.includes(3);                        // true – checks existence
arr.flat(depth);                        // Flatten nested arrays
```

### 8.9 Key ES6+ Syntax
```javascript
// Destructuring
const { name, age } = user;
const [first, ...rest] = arr;

// Spread / Rest
const newArr = [...arr1, ...arr2];
function sum(...args) { return args.reduce((a,b) => a+b, 0); }

// Template Literals
const msg = `Hello, ${name}!`;

// Optional Chaining
const city = user?.address?.city;

// Nullish Coalescing
const name = user.name ?? "Anonymous"; // fallback only on null/undefined (unlike || which is for any falsy)

// Modules
import { func } from './utils.js';
export default MyComponent;
```

### 8.10 DOM Manipulation
```javascript
// Selection
document.querySelector(".class");
document.querySelectorAll("li");

// Modification
el.textContent = "text";
el.innerHTML = "<b>HTML</b>";
el.setAttribute("href", "/path");
el.classList.add("active");
el.classList.toggle("visible");

// Create / remove
const div = document.createElement("div");
parent.appendChild(div);
parent.removeChild(child);

// Events
el.addEventListener("click", (e) => {
  e.preventDefault();   // Prevent default behavior
  e.stopPropagation();  // Stop event bubbling to parent
});
```

**Event Delegation**: Place the listener on the parent, check `e.target` to handle children — more efficient than attaching a listener to every child.

### 8.11 Advanced Concepts

**Hoisting**: `var` and function declarations are hoisted to the top of their scope. `let/const` have a TDZ (Temporal Dead Zone) — error if used before declaration.

**Debounce vs Throttle**:
- **Debounce**: Only fires after the user stops the action for X ms (e.g., search input).
- **Throttle**: Fires at most once per X ms regardless of how often the event fires (e.g., scroll, resize).

**Deep Clone vs Shallow Clone**:
```javascript
const shallow = { ...obj };                         // Shallow – doesn't copy nested objects
const deep = structuredClone(obj);                  // Deep – best approach (ES2022)
const deep2 = JSON.parse(JSON.stringify(obj));       // Deep – simple, but loses functions/dates
```

**Type Coercion**:
- `"5" - 1` → `4` (string coerced to number with `-`).
- `"5" + 1` → `"51"` (number coerced to string because `+` favors concatenation).

---

## 9. GENERAL WEB CONCEPTS

### 9.1 SPA vs MPA
| | SPA (Single Page App) | MPA (Multi Page App) |
|---|---|---|
| **Examples** | React, Vue, Angular apps | Traditional websites |
| **Navigation** | JS updates the DOM, no reload | Full page reload every time |
| **Pros** | Smooth, app-like experience | Better natural SEO |
| **Cons** | SEO harder, slower first load | Slower page transitions |

### 9.2 CSR vs SSR vs SSG
| | CSR | SSR | SSG |
|---|---|---|---|
| **Rendered in** | Client (browser) | Server (per request) | Build time |
| **First load** | Slow | Fast | Very fast |
| **SEO** | Poor | Good | Excellent |
| **Examples** | Plain React app | Next.js | Gatsby, Astro |

### 9.3 CORS
A browser security mechanism that blocks a Frontend on one domain from calling APIs on a Backend on a different domain unless the server permits it via the `Access-Control-Allow-Origin` header.

### 9.4 HTTP Methods & Status Codes
| Method | Used for |
|---|---|
| `GET` | Retrieve data |
| `POST` | Create a resource |
| `PUT` | Replace a resource entirely |
| `PATCH` | Partially update a resource |
| `DELETE` | Remove a resource |

| Code | Meaning |
|---|---|
| `200` | OK |
| `201` | Created |
| `301/302` | Redirect |
| `400` | Bad Request |
| `401` | Unauthorized (not logged in) |
| `403` | Forbidden (no permission) |
| `404` | Not Found |
| `500` | Internal Server Error |

### 9.5 Browser Rendering Pipeline
```
Parse HTML → DOM Tree
Parse CSS  → CSSOM Tree
           → Render Tree
           → Layout (Reflow) – calculate positions & sizes
           → Paint – draw pixels to screen
           → Composite – merge layers
```
> **Reflow** (layout changes) is more expensive than **Repaint** (color changes). Minimize unnecessary DOM operations.

### 9.6 Web Performance – Key Optimizations
- Minify CSS/JS, use a CDN.
- Lazy load images (`loading="lazy"`).
- Code splitting – only load JS when needed.
- Cache with `Cache-Control` headers and Service Worker.
- Use `async`/`defer` for `<script>` tags.
- Optimize Core Web Vitals (LCP < 2.5s, INP < 200ms, CLS < 0.1).

---

## 10. PRACTICE EXERCISES

**Exercise 1 – Data Types:**
```javascript
console.log([] == ![]);     // ?
console.log(NaN === NaN);   // ?
console.log(typeof null);   // ?
```
> **Answers**: `true` | `false` | `"object"`
> - `![]` = `false`, both coerced to `0` so they're equal.
> - NaN is never equal to itself.
> - `typeof null` is a historical JS quirk.

---

**Exercise 2 – Event Loop:**
```javascript
console.log("A");
setTimeout(() => console.log("B"), 0);
Promise.resolve().then(() => console.log("C"));
console.log("D");
```
> **Answer**: `A → D → C → B`
> - A, D: synchronous (Call Stack) → C: Microtask (Promise) → B: Macrotask (setTimeout)

---

**Exercise 3 – Closure:**
```javascript
// Write the createGreeting function so that:
const sayHello = createGreeting("Hello");
console.log(sayHello("Alice")); // "Hello, Alice"
```
> **Answer:**
> ```javascript
> function createGreeting(greeting) {
>   return function(name) {
>     return `${greeting}, ${name}`;
>   };
> }
> ```

---

## 11. MODERN CSS (2024–2026)

### 11.1 CSS Container Queries
Previously only **Media Queries** (responsive to viewport). Container Queries allow responsiveness based on the **size of the parent container** — better suited for component-based design.

```css
/* 1. Declare the container */
.card-wrapper {
  container-type: inline-size;
  container-name: card;
}

/* 2. Style children based on the container's size */
@container card (min-width: 400px) {
  .card {
    display: flex;
    flex-direction: row;
  }
}
```

> **Why it matters?** The same `.card` component can display as a column in a narrow sidebar, and as a row in a wide main area — without needing to know the viewport size. Support: Chrome 105+, Firefox 110+, Safari 16+ ✅

### 11.2 CSS `@layer` (Cascade Layers)
Solves specificity conflicts without relying on `!important`.

```css
/* Declare layer order – later layers override earlier ones */
@layer base, components, utilities;

@layer base {
  a { color: blue; }
}

@layer components {
  .btn { color: white; background: green; }
}

@layer utilities {
  .text-red { color: red; } /* Always wins, regardless of specificity */
}
```

> **Key insight**: Styles in a later layer always win over earlier layers, **regardless of specificity**. Very useful when importing third-party CSS libraries.

### 11.3 View Transitions API
Create smooth animations when transitioning content — **native, no library needed**.

```javascript
document.startViewTransition(() => {
  updateContent(); // Change the DOM inside
});
```

```css
::view-transition-old(root) { animation: fade-out 0.3s ease; }
::view-transition-new(root) { animation: fade-in 0.3s ease; }
```

> **Use cases**: Smooth SPA page transitions, shared element transitions (image "flying" from list to detail view). Support: Chrome 111+, Safari 18+.

---

## 12. TYPESCRIPT BASICS

### 12.1 What is TypeScript?
**TypeScript (TS)** is JavaScript with **static typing**, compiled to JS before running.

```
TypeScript (.ts) → Compile (tsc) → JavaScript (.js) → Browser
```

**Benefits**: Catch errors at write-time, better autocomplete, easier to maintain. **Nearly required in most Frontend jobs in 2024–2026.**

### 12.2 Basic Types
```typescript
let name: string = "Alice";
let age: number = 25;
let isActive: boolean = true;
let scores: number[] = [1, 2, 3];
let point: [number, number] = [10, 20]; // Tuple

// any – avoid (defeats the purpose of TS)
// unknown – safer than any, must check type before using
let value: unknown = getData();
if (typeof value === "string") console.log(value.toUpperCase());

function log(msg: string): void { console.log(msg); }       // void – no return value
function fail(msg: string): never { throw new Error(msg); } // never – never returns
```

### 12.3 Interface & Type Alias
```typescript
// Interface – for object shapes, extendable
interface User {
  id: number;
  name: string;
  email?: string;           // Optional
  readonly createdAt: Date; // Cannot be modified after creation
}

// Type Alias – more flexible, for unions/intersections
type ID = string | number;
type Status = "active" | "inactive" | "pending"; // Union (literal) type
type AdminUser = User & { role: "admin" };        // Intersection type
```

> **When to use which?** `interface` for object/class definitions. `type` for unions, tuples, and complex types.

### 12.4 Generics
```typescript
function getFirst<T>(arr: T[]): T { return arr[0]; }

getFirst<number>([1, 2, 3]); // 1
getFirst<string>(["a", "b"]); // "a"
```

### 12.5 Common Utility Types
```typescript
interface User { id: number; name: string; email: string; age: number; }

type PartialUser    = Partial<User>;              // All properties become optional
type UserPreview    = Pick<User, "id" | "name">;  // Select specific properties
type UserWithoutAge = Omit<User, "age">;          // Exclude specific properties
type ReadonlyUser   = Readonly<User>;             // All properties immutable
type UserMap        = Record<string, User>;       // Object with string keys and User values
```

### 12.6 TypeScript with React
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

// useState with types
const [count, setCount] = useState<number>(0);
const [user, setUser] = useState<User | null>(null);

// useRef
const inputRef = useRef<HTMLInputElement>(null);
```

---

## 13. MODERN TOOLING & ECOSYSTEM

### 13.1 Package Managers
| Tool | Characteristics |
|---|---|
| **npm** | Default with Node.js |
| **yarn** | Faster, consistent lockfile |
| **pnpm** | Disk-efficient via symlinks, fast (2024 trend) |
| **bun** | Runtime + package manager, extremely fast |

### 13.2 Build Tools
| Tool | Characteristics |
|---|---|
| **Vite** | Ultra-fast dev server (native ESM). **The standard in 2024–2026** |
| **Webpack** | Still widely used in legacy projects, complex config |
| **esbuild** | Blazing fast (written in Go), core of many tools |
| **Turbopack** | Webpack's successor, integrated in Next.js |

### 13.3 Frameworks & Libraries
| Name | Type | Highlights |
|---|---|---|
| **React 18+** | UI Library | Concurrent Mode, Server Components |
| **Next.js 14+** | Full-stack | App Router, Server Actions |
| **Vue 3** | Framework | Composition API, smaller bundle |
| **Astro** | Static/SSR | Islands architecture, zero JS by default |
| **Svelte/SvelteKit** | Compiler | No Virtual DOM, concise code |

### 13.4 State Management
| Name | When to use |
|---|---|
| `useState` / `useReducer` | Simple local state |
| **Context API** | Small global state with infrequent updates |
| **Zustand** | Lightweight global state (trending 2024) |
| **TanStack Query** | Async / server state (caching, syncing) |
| **Redux Toolkit** | Complex state in very large apps |

### 13.5 Testing
| Type | Tools |
|---|---|
| **Unit testing** | Vitest (fast, Vite-integrated), Jest |
| **Component testing** | React Testing Library |
| **E2E testing** | Playwright (standard 2024+), Cypress |

---

## 14. COMMON INTERVIEW QUESTIONS

### CSS
- **`display: none` vs `visibility: hidden`?**
  > `none`: Removed from layout entirely, takes no space. `hidden`: Invisible but still takes up space.
- **`em` vs `rem`?**
  > `rem` is safer – always relative to the root, unaffected by nesting.
- **What is a Stacking Context?**
  > A local stacking order created by `position` + `z-index`, `opacity < 1`, `transform`, etc. Z-index only compares within the same stacking context.

### JavaScript
- **`null` vs `undefined`?**
  > `undefined`: Declared but not yet assigned. `null`: Intentionally assigned an empty/absent value.
- **`call` vs `apply` vs `bind`?**
  > All change `this`. `call(ctx, a, b)` invokes immediately. `apply(ctx, [a,b])` invokes immediately with an array. `bind(ctx)` returns a new function with `this` bound.
- **Debounce vs Throttle?**
  > Debounce: waits until the user stops acting (search input). Throttle: limits calls to at most once per X ms (scroll, resize).
- **Shallow copy vs Deep copy?**
  > `{...obj}` is shallow. `structuredClone(obj)` is the best deep copy approach.

### React
- **What does the `useEffect` cleanup function do?**
  > Cleans up side effects (cancel subscriptions, clear timers...) when the component unmounts or before the effect re-runs due to dependency changes.
- **`useMemo` vs `useCallback`?**
  > `useMemo`: Memoizes a **computed value**. `useCallback`: Memoizes a **function reference** (avoids recreating it on every render).
- **Why are `key` props needed in lists?**
  > Helps React identify which items changed, were added, or removed during reconciliation. Keys must be unique and stable — **never use array index if the list can reorder**.
- **What is the Virtual DOM?**
  > A lightweight in-memory copy of the real DOM. React diffs old vs new Virtual DOM to calculate the minimal set of changes, then updates the real DOM.

### Git
- **When do you use `git stash`?**
  > When you need to switch branches urgently but have uncommitted work in progress — stash it temporarily and pop it back later.
- **What is `git cherry-pick`?**
  > Applies a specific commit from another branch to the current branch without merging the entire branch.
