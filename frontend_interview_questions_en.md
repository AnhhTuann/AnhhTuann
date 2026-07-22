# 🎯 Front-End Interview Questions – Complete & Battle-Tested

> **How to use:** Each question has a **Quick Answer (TL;DR)** and **Detailed Explanation**. Practice the TL;DR first, then expand with details when the interviewer asks follow-up questions.

---

## 📌 TABLE OF CONTENTS
1. [GIT](#1-git)
2. [HTML](#2-html)
3. [CSS](#3-css)
4. [CSS Layout (Flexbox & Grid)](#4-css-layout)
5. [Responsive Design](#5-responsive-design)
6. [JavaScript Basics](#6-javascript-basics)
7. [JavaScript Advanced](#7-javascript-advanced)
8. [TypeScript](#8-typescript)
9. [Web Fundamentals (CORS, HTTP, Browser)](#9-web-fundamentals)
10. [React](#10-react)
11. [Tooling & Ecosystem](#11-tooling--ecosystem)
12. [Scenario Questions](#12-scenario-questions)
13. [Live Coding Exercises](#13-live-coding-exercises)

---

## 1. GIT

### What is Git? How is Git different from GitHub?
> **TL;DR:** Git is a local Version Control System (VCS). GitHub is a cloud hosting platform for Git repositories.

- Git tracks all code changes over time, allowing rollback, comparison, and branching.
- GitHub (/ GitLab / Bitbucket) is a hosting service + collaboration tooling (Pull Requests, CI/CD...).

---

### What are Git's 3 areas? Explain the basic workflow.
> **TL;DR:** Working Directory -> `git add` -> Staging Area -> `git commit` -> Repository.

| Area | Role |
|---|---|
| **Working Directory** | Files you are currently editing |
| **Staging Area** | Changes selected to include in the next commit |
| **Repository** | Saved commit history |

---

### Merge vs Rebase - When to use which?
> **TL;DR:** Merge is safer for teams (preserves real history). Rebase creates cleaner history but **never rebase a shared/pushed branch**.

| | Merge | Rebase |
|---|---|---|
| **History** | Preserved, adds a merge commit | Rewritten, linear history |
| **Safety** | Safe on shared branches | Dangerous on pushed branches |
| **Use when** | Merging a feature into `main` | Updating feature branch from `develop` |

---

### Reset vs Revert - What is the difference?
> **TL;DR:** `reset` rewrites history (use locally only). `revert` creates a new undo commit (safe for shared repos).

```bash
git reset --soft HEAD~1    # Keep code + staging
git reset --mixed HEAD~1   # Keep code, clear staging
git reset --hard HEAD~1    # Discard everything
git revert <commit-hash>   # Create a new undo commit
```

---

### What is GitFlow? Explain the 5 branch types.
> **TL;DR:** A standard branch management workflow: `main`, `develop`, `feature/*`, `release/*`, `hotfix/*`.

| Branch | Role |
|---|---|
| `main` | Live production code |
| `develop` | Active development |
| `feature/*` | New features |
| `release/*` | Pre-release stabilization |
| `hotfix/*` | Urgent production bug fixes |

---

### When do you use `git stash`?
> **TL;DR:** When you need to switch branches urgently but your work is not ready to commit.

```bash
git stash          # Save current changes temporarily
git checkout other-branch
git stash pop      # Restore stashed changes
```

---

### What is `git cherry-pick`?
> **TL;DR:** Apply a specific commit from another branch without merging the whole branch.

```bash
git cherry-pick <commit-hash>
```
**Use case:** A hotfix in `develop` needs to go to `main` immediately.

---

## 2. HTML

### What is DOCTYPE? Why is it required?
> **TL;DR:** Declares the HTML version to the browser. Without it, browsers enter **quirks mode** and render incorrectly.

```html
<!DOCTYPE html>  <!-- Must be the very first line -->
```

---

### What is Semantic HTML? Why does it matter?
> **TL;DR:** Using meaningful tags (`<header>`, `<nav>`, `<main>`...) instead of generic `<div>`. Better **SEO** and **Accessibility**.

| Tag | Role |
|---|---|
| `<header>` | Page or section header |
| `<nav>` | Main navigation |
| `<main>` | Primary content (only one per page) |
| `<section>` | Thematically grouped content |
| `<article>` | Self-contained content (blog post, card) |
| `<aside>` | Secondary content (sidebar) |
| `<footer>` | Page or section footer |

---

### Block vs Inline vs Inline-block - Differences?
> **TL;DR:** Block takes full width. Inline only takes needed space. Inline-block = Inline but allows setting width/height.

| Type | Line break | Set width/height | Examples |
|---|---|---|---|
| Block | Yes | Yes | `div`, `p`, `h1` |
| Inline | No | No | `span`, `a`, `strong` |
| Inline-block | No | Yes | `button`, `input`, `img` |

---

### Form: `readonly` vs `disabled` - What is the difference?
> **TL;DR:** `readonly` prevents editing but **still submits the value**. `disabled` cannot be focused and value is **not submitted**.

---

### `localStorage` vs `sessionStorage` vs `Cookie` - When to use each?
> **TL;DR:** localStorage is permanent (~5MB). sessionStorage clears on tab close. Cookie is small (4KB), auto-sent to server.

| | localStorage | sessionStorage | Cookie |
|---|---|---|---|
| **Size** | ~5MB | ~5MB | ~4KB |
| **Lifetime** | Permanent | Until tab closes | Configurable expiry |
| **Sent to server** | No | No | Yes - automatically |
| **Use for** | Settings, theme | Tab-scoped state | Auth token, session |

---

### Web Accessibility (A11y) - How do you make a website accessible?
> **TL;DR:** Semantic HTML, alt text, keyboard navigation, sufficient color contrast, ARIA when needed.

- **Color contrast**: Minimum 4.5:1 ratio (WCAG AA)
- **Alt text**: Informational images -> descriptive text. Decorative -> `alt=""`
- **Keyboard**: Every feature must work with Tab/Enter/Space/Escape
- **tabindex**: `0` (natural tab flow), `-1` (JS-only focus)
- **ARIA**: `aria-label`, `aria-live` provide semantics to screen readers

---

## 3. CSS

### How does CSS Specificity work?
> **TL;DR:** `!important` > Inline style > ID > Class/Pseudo-class > Element.

```
!important > inline (1,0,0,0) > ID (0,1,0,0) > Class (0,0,1,0) > Element (0,0,0,1)
```
> Avoid `!important` - very hard to override later. Avoid `#id` for styling.

---

### What is the Box Model? `content-box` vs `border-box`?
> **TL;DR:** Every element is a box: Content -> Padding -> Border -> Margin. `border-box` includes padding + border in width.

```css
*, *::before, *::after { box-sizing: border-box; } /* Recommended globally */
```

---

### `display: none` vs `visibility: hidden` - Difference?
> **TL;DR:** `none` removes from layout, takes no space. `hidden` is invisible but **still takes up space**.

| | display: none | visibility: hidden | opacity: 0 |
|---|---|---|---|
| Takes up space | No | Yes | Yes |
| Clickable | No | No | Yes |
| Accessible | No | No | Yes |

---

### Position: relative vs absolute vs fixed vs sticky?
> **TL;DR:** relative: offset from original. absolute: relative to nearest positioned ancestor. fixed: relative to viewport. sticky: relative until scroll threshold.

| Value | Reference point | In document flow |
|---|---|---|
| `static` | Normal flow | Yes |
| `relative` | Its own original position | Yes |
| `absolute` | Nearest ancestor with position != static | No |
| `fixed` | Viewport | No |
| `sticky` | Scroll container | Yes |

---

### `em` vs `rem` - Which should you use?
> **TL;DR:** `rem` is safer - always relative to the root `<html>`, unaffected by nesting.

```css
html { font-size: 16px; }
.parent { font-size: 20px; }
.child-em  { font-size: 1.5em; }  /* 20 x 1.5 = 30px - depends on parent */
.child-rem { font-size: 1.5rem; } /* 16 x 1.5 = 24px - always from root */
```

---

### Stacking Context - Why does z-index sometimes not work?
> **TL;DR:** Z-index only compares elements **within the same stacking context**. Check if a parent is creating a new one.

**What creates a new stacking context:** `position` + `z-index` != auto, `opacity < 1`, `transform`, `filter`, `clip-path`

---

### What is Margin Collapsing?
> **TL;DR:** Adjacent vertical margins collapse into one equal to the larger value - not the sum.

```css
.box1 { margin-bottom: 20px; }
.box2 { margin-top: 20px; }
/* Result: 20px gap, NOT 40px */
```
**Prevention:** Use `overflow: hidden`, `padding`, `border`, or Flexbox/Grid on parent.

---

### What is BEM? Why use it?
> **TL;DR:** Block__Element--Modifier - a class naming convention for structured, conflict-free CSS.

```css
.card { }               /* Block */
.card__title { }        /* Element */
.card__title--large { } /* Modifier */
```

---

## 4. CSS Layout

### When do you use Flexbox? Key properties?
> **TL;DR:** Use for arranging items **in a single row or column** (1-dimensional).

```css
.container {
  display: flex;
  flex-direction: row;
  justify-content: center;    /* Main axis alignment */
  align-items: center;        /* Cross axis alignment */
  flex-wrap: wrap;
  gap: 16px;
}
.item { flex: 1; align-self: flex-start; order: -1; }
```

---

### When do you use CSS Grid? How is it different from Flexbox?
> **TL;DR:** Grid for **2-dimensional** layouts. Flexbox is 1-dimensional.

```css
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
.featured { grid-column: 1 / 3; }
```

- **Flexbox**: Navigation bars, card rows, simple centering
- **Grid**: Page layouts, dashboards, complex galleries

---

## 5. Responsive Design

### What is Mobile First? Why is it recommended?
> **TL;DR:** Write default CSS for mobile, use `min-width` queries to scale up. Better performance, forces content prioritization.

```css
.card { flex-direction: column; }
@media (min-width: 768px) { .card { flex-direction: row; } }
```

---

### How do Media Queries work?
> **TL;DR:** Apply CSS conditionally based on viewport, device type, orientation, user preferences...

```css
@media (max-width: 768px) { /* Mobile */ }
@media (min-width: 768px) { /* Tablet+ */ }
@media (prefers-color-scheme: dark) { /* Dark mode */ }
```

---

### What are CSS Container Queries? Why better than Media Queries for components?
> **TL;DR:** Respond to **parent element size** rather than viewport - better for component-based design.

```css
.card-wrapper { container-type: inline-size; }
@container (min-width: 400px) {
  .card { display: flex; flex-direction: row; }
}
```

---

## 6. JavaScript Basics

### `var` vs `let` vs `const` - Differences?
> **TL;DR:** Default to `const`, use `let` for reassignment. **Never use `var`**.

| | `var` | `let` | `const` |
|---|---|---|---|
| **Scope** | Function | Block | Block |
| **Hoisting** | Yes (undefined) | Yes (TDZ - error) | Yes (TDZ - error) |
| **Reassign** | Yes | Yes | No |
| **Redeclare** | Yes | No | No |

---

### `==` vs `===` - Which should you use?
> **TL;DR:** Always use `===`. `==` performs type coercion and produces surprising results.

```javascript
5 == "5"           // true  (type coercion)
5 === "5"          // false (strict)
null == undefined  // true
NaN == NaN         // false (NaN never equals itself!)
```

---

### `null` vs `undefined` - Difference?
> **TL;DR:** `undefined` = declared but not assigned. `null` = intentionally set to "no value".

```javascript
let a;         // undefined - natural, no value yet
let b = null;  // null - developer deliberately set empty
typeof undefined // "undefined"
typeof null      // "object" - historical JS quirk!
```

---

### Primitive vs Reference - How do they differ when copying?
> **TL;DR:** Primitives copy the value. References copy the **memory address**.

```javascript
// Primitive: copies value - independent
let a = 5; let b = a; b = 10;
console.log(a); // 5

// Reference: copies address - linked
let obj1 = { name: "Alice" }; let obj2 = obj1;
obj2.name = "Bob";
console.log(obj1.name); // "Bob" - affected!
```

---

### What is a Closure? Give a real-world example.
> **TL;DR:** An inner function that remembers outer function variables **even after the outer function has returned**.

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
```
**Uses:** Module pattern, memoization, factory functions.

---

### What is Hoisting?
> **TL;DR:** JS moves declarations to the top of scope before execution. `var` -> `undefined`. `let/const` -> TDZ error.

```javascript
console.log(a); // undefined (no error)
var a = 5;

console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 5;

sayHi(); // "Hi!" - function declarations are fully hoisted
function sayHi() { console.log("Hi!"); }
```

---

### What is the Prototype Chain?
> **TL;DR:** JS inheritance - when a property is missing, JS walks up `__proto__` until `null`.

```javascript
const dog = { name: "Rex" };
// dog.__proto__ -> Object.prototype -> null
// dog.toString() -> not on dog -> found on Object.prototype!
```

---

## 7. JavaScript Advanced

### What is the Event Loop? Explain JS async mechanism.
> **TL;DR:** JS is single-threaded. Event Loop: **Synchronous -> Microtasks (Promises) -> Macrotasks (setTimeout)**.

```javascript
console.log("A");                                // 1 - sync
setTimeout(() => console.log("B"), 0);           // 4 - Macrotask
Promise.resolve().then(() => console.log("C"));  // 3 - Microtask
console.log("D");                                // 2 - sync
// Output: A -> D -> C -> B
```
> **Microtasks always run BEFORE the next Macrotask**, even with 0ms timeout.

---

### Promise vs Async/Await - Which to use?
> **TL;DR:** `async/await` is syntactic sugar over Promises. Use it for all new code - reads like synchronous code.

```javascript
// Promise chain
fetch("/api/user").then(res => res.json()).then(console.log).catch(console.error);

// Async/Await - cleaner
async function getUser() {
  try {
    const res = await fetch("/api/user");
    return await res.json();
  } catch (err) { console.error(err); }
}
```

---

### `Promise.all` vs `Promise.allSettled` vs `Promise.race`?
> **TL;DR:** `all` = parallel, fails if any fails. `allSettled` = all results regardless. `race` = first to resolve/reject wins.

```javascript
const [user, posts] = await Promise.all([fetchUser(), fetchPosts()]);

const results = await Promise.allSettled([fetchA(), fetchB()]);
results.forEach(r => {
  if (r.status === "fulfilled") console.log(r.value);
  else console.error(r.reason);
});
```

---

### Debounce vs Throttle - Explain with examples.
> **TL;DR:** Debounce: wait until user stops acting, then fire (search). Throttle: fire at most once per X ms (scroll).

```javascript
function debounce(fn, delay) {
  let timer;
  return (...args) => { clearTimeout(timer); timer = setTimeout(() => fn(...args), delay); };
}

function throttle(fn, limit) {
  let lastCall = 0;
  return (...args) => {
    const now = Date.now();
    if (now - lastCall >= limit) { lastCall = now; fn(...args); }
  };
}
```

---

### Shallow Copy vs Deep Copy?
> **TL;DR:** Shallow copies 1 level - nested objects still share memory. Deep copy creates a fully independent clone.

```javascript
const obj = { a: 1, b: { c: 2 } };
const shallow = { ...obj };                         // Shallow
const deep = structuredClone(obj);                  // Deep - best (ES2022)
const deep2 = JSON.parse(JSON.stringify(obj));       // Deep - loses functions/Date
```

---

### `call` vs `apply` vs `bind`?
> **TL;DR:** All change `this`. `call` invokes with individual args. `apply` invokes with array. `bind` returns new function.

```javascript
function greet(greeting, mark) { return `${greeting}, ${this.name}${mark}`; }
const user = { name: "Alice" };

greet.call(user, "Hello", "!");      // "Hello, Alice!" - invoked immediately
greet.apply(user, ["Hi", "."]);      // "Hi, Alice." - invoked with array
const bound = greet.bind(user, "Hey"); // Returns new function
bound("?"); // "Hey, Alice?"
```

---

### How does `this` work in JavaScript?
> **TL;DR:** `this` depends on **how the function is called**. Arrow functions inherit `this` from outer scope.

```javascript
const obj = {
  name: "Alice",
  regular: function() { return this.name; }, // this = obj -> "Alice"
  arrow: () => this.name,                    // this = outer scope -> undefined
};
```

---

### What is Event Delegation? Why use it?
> **TL;DR:** Attach one listener to a parent instead of each child. Efficient for many or dynamically created items.

```javascript
// Bad: 100 items = 100 listeners
document.querySelectorAll(".item").forEach(el => el.addEventListener("click", fn));

// Good: 1 listener on parent
document.querySelector(".list").addEventListener("click", (e) => {
  if (e.target.matches(".item")) fn(e.target);
});
```

---

## 8. TypeScript

### What is TypeScript? Benefits over JS?
> **TL;DR:** JS with static typing. Catches errors while coding, better autocomplete, easier to maintain.

```
TypeScript (.ts) -> Compile (tsc) -> JavaScript (.js) -> Browser
```

---

### `interface` vs `type` - When to use each?
> **TL;DR:** `interface` for object shapes/classes. `type` for unions, tuples, and complex types.

```typescript
interface User {
  id: number;
  name: string;
  email?: string;            // Optional
  readonly createdAt: Date;  // Read-only
}
interface AdminUser extends User { role: "admin"; }

type ID = string | number;                  // Union
type Status = "active" | "inactive";        // Literal union
type AdminUser = User & { role: "admin" };  // Intersection
```

---

### What are Generics? Give an example.
> **TL;DR:** Write type-safe functions/components that work with multiple types.

```typescript
function getFirst<T>(arr: T[]): T { return arr[0]; }

getFirst<number>([1, 2, 3]);  // 1, type: number
getFirst<string>(["a", "b"]); // "a", type: string
```

---

### Common Utility Types?
> **TL;DR:** `Partial`, `Pick`, `Omit`, `Readonly`, `Record` - transform existing types without redefining.

```typescript
interface User { id: number; name: string; email: string; age: number; }

type OptionalUser  = Partial<User>;             // All optional
type UserCard      = Pick<User, "id" | "name">; // Only id and name
type NoAge         = Omit<User, "age">;         // Without age
type ImmutableUser = Readonly<User>;            // All read-only
type UserMap       = Record<string, User>;      // { [key: string]: User }
```

---

## 9. Web Fundamentals

### What is CORS? When does it occur and how to fix?
> **TL;DR:** Browser security that blocks cross-origin requests. Fix **on the server** with `Access-Control-Allow-Origin` header.

```
Frontend: http://localhost:3000
Backend: http://api.example.com
-> Browser blocks it - different origins!
```
**Fixes:** Server adds `Access-Control-Allow-Origin` header. Dev: use Vite proxy config.

---

### HTTP Methods - Differences and use cases?
> **TL;DR:** GET (fetch), POST (create), PUT (full update), PATCH (partial update), DELETE (remove).

| Method | Idempotent | Body | Use when |
|---|---|---|---|
| `GET` | Yes | No | Fetching data |
| `POST` | No | Yes | Creating a resource |
| `PUT` | Yes | Yes | Full replacement update |
| `PATCH` | Yes | Yes | Partial update |
| `DELETE` | Yes | No | Deleting a resource |

---

### Important HTTP Status Codes?
> **TL;DR:** 2xx = success, 3xx = redirect, 4xx = client error, 5xx = server error.

| Code | Meaning |
|---|---|
| `200` | OK |
| `201` | Created |
| `204` | No Content |
| `301/302` | Redirect (permanent / temporary) |
| `400` | Bad Request |
| `401` | Unauthorized (not logged in) |
| `403` | Forbidden (no permission) |
| `404` | Not Found |
| `422` | Unprocessable Entity (validation failed) |
| `500` | Internal Server Error |

---

### SPA vs MPA - Pros and cons?
> **TL;DR:** SPA is smooth but SEO-challenged and slow first load. MPA has great SEO but slower page transitions.

| | SPA | MPA |
|---|---|---|
| **Navigation** | JS updates DOM, no full reload | Full page reload |
| **SEO** | Needs SSR/SSG | Natural |
| **UX** | Smooth | Page flash on navigation |
| **Examples** | React app, Gmail | Wikipedia, traditional e-commerce |

---

### CSR vs SSR vs SSG - When to choose each?
> **TL;DR:** CSR = client renders (poor SEO). SSR = server per request (good SEO, fresh). SSG = pre-built HTML (fastest).

| | CSR | SSR | SSG |
|---|---|---|---|
| **Rendered on** | Browser | Server | Build time |
| **SEO** | Poor | Good | Excellent |
| **Speed** | Slow initially | Medium | Very fast |
| **Use for** | Dashboards, auth apps | E-commerce, news | Blogs, docs, landing pages |

---

### What is the Browser Rendering Pipeline?
> **TL;DR:** HTML/CSS -> DOM/CSSOM -> Render Tree -> Layout (Reflow) -> Paint -> Composite.

```
Parse HTML -> DOM Tree ->
Parse CSS  -> CSSOM    -> Render Tree -> Layout -> Paint -> Composite
```
- **Reflow** (layout changes): **Most expensive** - avoid triggering in loops
- **Repaint** (color, background): Expensive but less than reflow
- **Composite** (transform, opacity): **Fastest** - happens on GPU

**Tip:** Use `transform` and `opacity` for animations, not `left`/`top`.

---

### What are Core Web Vitals?
> **TL;DR:** Google's 3 performance metrics - they directly impact SEO ranking.

| Metric | Full Name | Target | Measures |
|---|---|---|---|
| **LCP** | Largest Contentful Paint | < 2.5s | Time to load the largest visible element |
| **INP** | Interaction to Next Paint | < 200ms | Responsiveness to user interactions |
| **CLS** | Cumulative Layout Shift | < 0.1 | Visual stability while loading |

---

## 10. React

### What is the Virtual DOM? Why is it used?
> **TL;DR:** A lightweight in-memory copy of the real DOM. React diffs it to find minimal changes, then updates the real DOM.

```
State changes
-> React creates new Virtual DOM
-> Diffs against old Virtual DOM (Reconciliation)
-> Applies only the minimal real DOM updates
```

---

### `useEffect` - Explain and use cases?
> **TL;DR:** Runs side effects after rendering. Dependency array controls when it re-runs.

```javascript
useEffect(() => { /* runs after every render */ });
useEffect(() => { /* runs once after mount */ }, []);
useEffect(() => { fetchUser(userId); }, [userId]);
useEffect(() => {
  const sub = subscribe(userId);
  return () => sub.unsubscribe(); // Cleanup on unmount or dep change
}, [userId]);
```

---

### `useMemo` vs `useCallback` - When to use each?
> **TL;DR:** `useMemo` memoizes a **computed value**. `useCallback` memoizes a **function reference**.

```javascript
const expensiveValue = useMemo(() => heavyCalculation(data), [data]);
const handleClick = useCallback(() => doSomething(userId), [userId]);
```
> Only use when you have a real performance problem - premature optimization hurts readability.

---

### Keys in lists - Why important? Why not use index?
> **TL;DR:** Keys help React identify changed items. Don't use index if the list can reorder.

```javascript
// Wrong - adding item at start causes all items to re-render
{items.map((item, index) => <Item key={index} data={item} />)}

// Correct - stable, unique key
{items.map(item => <Item key={item.id} data={item} />)}
```

---

### What is the `useEffect` cleanup function?
> **TL;DR:** Cleans up side effects when unmounting or before effect re-runs. Prevents memory leaks.

```javascript
useEffect(() => {
  const controller = new AbortController();
  fetch("/api/data", { signal: controller.signal });
  return () => controller.abort(); // Cancel fetch on unmount
}, []);
```

---

### `useState` vs `useReducer` - When to use each?
> **TL;DR:** `useState` for simple state. `useReducer` for complex state with multiple related actions.

```javascript
const [count, setCount] = useState(0);

const [state, dispatch] = useReducer((state, action) => {
  switch (action.type) {
    case "INCREMENT": return { ...state, count: state.count + 1 };
    case "RESET":     return { count: 0, error: null };
    default: return state;
  }
}, { count: 0, error: null });
```

---

## 11. Tooling & Ecosystem

### Vite vs Webpack - Differences?
> **TL;DR:** Vite uses native ESM -> blazing fast dev server and HMR. Webpack bundles everything -> slower in development.

| | Vite | Webpack |
|---|---|---|
| **Dev server** | Native ESM, very fast | Bundles everything, slower |
| **HMR** | Module-level (instant) | Bundle-level (slower) |
| **Use for** | New projects (2024+) | Legacy projects, Next.js |

---

### State Management - When do you need Zustand/Redux?
> **TL;DR:** Priority: local state -> Context API -> Zustand -> Redux Toolkit.

| Tool | When to use |
|---|---|
| `useState/useReducer` | Component-level state |
| **Context API** | Global state that rarely changes (theme, auth) |
| **Zustand** | Frequent global state updates, lightweight |
| **TanStack Query** | Server/async state - caching, refetching |
| **Redux Toolkit** | Very large apps, large teams |

---

## 12. Scenario Questions

### A website is loading slowly - How do you debug it?
> **TL;DR:** Chrome DevTools: Lighthouse -> Network tab -> Performance tab.

**Process:**
1. **Lighthouse** -> Core Web Vitals scores and suggestions
2. **Network tab** -> large files? slow requests?
3. **Performance tab** -> blocking scripts? layout shifts?

**Common fixes:**
- Large images -> WebP, lazy loading, `srcset`
- Too much JS -> code splitting, tree shaking
- Render blocking -> `async`/`defer` scripts
- Slow API -> caching, pagination, skeleton UI

---

### How do you prevent memory leaks in React?
> **TL;DR:** Cleanup in `useEffect`, avoid setState after unmount, use AbortController for fetches.

```javascript
useEffect(() => {
  let isActive = true;
  fetchData().then(data => {
    if (isActive) setData(data);
  });
  return () => { isActive = false; };
}, []);
```

---

### How do you handle complex forms in React?
> **TL;DR:** React Hook Form + Zod/Yup for schema validation.

```javascript
import { useForm } from "react-hook-form";
import { zodResolver } from "@hookform/resolvers/zod";
import { z } from "zod";

const schema = z.object({ email: z.string().email(), password: z.string().min(8) });
const { register, handleSubmit, formState: { errors } } = useForm({ resolver: zodResolver(schema) });
```

---

### Infinite loop in `useEffect` - How to fix it?
> **TL;DR:** Check dependency array. Objects/arrays in deps are new references each render.

```javascript
// Bug: options is new object every render -> infinite loop
const options = { limit: 10 };
useEffect(() => { fetch("/api", options); }, [options]);

// Fix 1: useMemo
const options = useMemo(() => ({ limit: 10 }), []);

// Fix 2: Use primitive values
useEffect(() => { fetch(`/api?limit=${limit}`); }, [limit]);
```

---

## 13. Live Coding Exercises

### Exercise 1 - What is the output?
```javascript
console.log([] == ![]);         // ?
console.log(NaN === NaN);       // ?
console.log(typeof null);       // ?
console.log(0.1 + 0.2 === 0.3); // ?
```
> **Answers:** `true` | `false` | `"object"` | `false`
> - `![]` = `false`; both coerce to `0` -> equal; NaN never equals itself; floating point precision

---

### Exercise 2 - Event Loop output order?
```javascript
console.log("1");
setTimeout(() => console.log("2"), 0);
Promise.resolve().then(() => console.log("3"));
setTimeout(() => console.log("4"), 0);
Promise.resolve().then(() => console.log("5"));
console.log("6");
```
> **Answer:** `1 -> 6 -> 3 -> 5 -> 2 -> 4`
> Synchronous -> Microtasks (Promises) -> Macrotasks (setTimeout)

---

### Exercise 3 - Implement `debounce`
```javascript
function debounce(fn, delay) { /* implement here */ }
const search = debounce((q) => console.log("Searching:", q), 300);
```
> **Answer:**
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

### Exercise 4 - Flatten nested array (no `.flat()`)
```javascript
// Input:  [1, [2, [3, [4]], 5]]
// Output: [1, 2, 3, 4, 5]
function flatten(arr) { /* implement */ }
```
> **Answer:**
> ```javascript
> // Recursive
> function flatten(arr) {
>   return arr.reduce((acc, item) =>
>     Array.isArray(item) ? [...acc, ...flatten(item)] : [...acc, item], []);
> }
> ```

---

### Exercise 5 - React `useFetch` custom hook
```typescript
function useFetch<T>(url: string) {
  // Return: { data, loading, error }
}
```
> **Answer:**
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

## Tips for Acing the Interview

### Use STAR for scenario questions
> **S**ituation -> **T**ask -> **A**ction -> **R**esult

### Good questions to ask the interviewer
- "What is the current tech stack your team uses?"
- "How big is the team? What does the FE/BE workflow look like?"
- "What stage is the product at? How does it scale?"
- "What does career growth look like on this team?"

### Buzzwords that impress interviewers
- **Performance**: Core Web Vitals, LCP, CLS, code splitting, lazy loading
- **DX**: TypeScript, ESLint, Prettier, Husky, CI/CD
- **Best practices**: BEM, Clean code, SOLID, accessibility, semantic HTML
- **Trending 2024-2026**: Vite, pnpm, TanStack Query, Zustand, Server Components, Container Queries

---

*Based on [frontend_full_notes_en.md](file:///d:/practices/frontend_full_notes_en.md) and [frontend_interview_questions_vi.md](file:///d:/practices/frontend_interview_questions_vi.md)*
