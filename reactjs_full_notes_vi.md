# ⚛️ Tổng Hợp Kiến Thức ReactJS – Đầy Đủ & Xúc Tích (Tiếng Việt)

> **Dành cho:** Developer đã biết JS cơ bản muốn nắm chắc React  
> **Phiên bản:** React 18+  
> **Phiên bản EN:** [reactjs_full_notes_en.md](reactjs_full_notes_en.md)

---

## Mục Lục

1. [React Là Gì & Tại Sao Dùng](#1-react-là-gì--tại-sao-dùng)
2. [JSX](#2-jsx)
3. [Component](#3-component)
4. [Props](#4-props)
5. [State & useState](#5-state--usestate)
6. [Vòng Đời Component (Lifecycle)](#6-vòng-đời-component-lifecycle)
7. [useEffect](#7-useeffect)
8. [useRef](#8-useref)
9. [useContext](#9-usecontext)
10. [useReducer](#10-usereducer)
11. [useMemo & useCallback](#11-usememo--usecallback)
12. [Custom Hook](#12-custom-hook)
13. [React Router](#13-react-router)
14. [State Management (Redux / Zustand)](#14-state-management-redux--zustand)
15. [Gọi API trong React](#15-gọi-api-trong-react)
16. [Performance Optimization](#16-performance-optimization)
17. [Error Boundary](#17-error-boundary)
18. [Patterns Hay Dùng](#18-patterns-hay-dùng)
19. [Testing React](#19-testing-react)
20. [Câu Hỏi Phỏng Vấn Nhanh](#20-câu-hỏi-phỏng-vấn-nhanh)

---

## 1. React Là Gì & Tại Sao Dùng

**React** là thư viện JavaScript do Meta phát triển để xây dựng UI (User Interface), đặc biệt là Single Page Application (SPA).

### React vs Angular vs Vue

| Tiêu chí | React | Angular | Vue |
|---|---|---|---|
| Loại | Thư viện (Library) | Framework đầy đủ | Framework nhẹ |
| Ngôn ngữ | JSX (JS + HTML) | TypeScript | Template syntax |
| Learning curve | Trung bình | Cao | Thấp |
| Virtual DOM | ✅ | ❌ | ✅ |
| Backing | Meta | Google | Community |
| Dùng cho | SPA, phức tạp | Enterprise | Linh hoạt |

### Tại Sao React Phổ Biến?

- **Component-based:** Chia UI thành các mảnh nhỏ tái sử dụng
- **Virtual DOM:** Cập nhật DOM hiệu quả, chỉ re-render phần thay đổi
- **Unidirectional data flow:** Dữ liệu chảy 1 chiều → dễ debug
- **Ecosystem lớn:** React Router, Redux, Next.js, React Query...
- **React Native:** Dùng cùng kiến thức xây dựng app mobile

### Virtual DOM Hoạt Động Như Thế Nào?

```
1. State/Props thay đổi
2. React tạo Virtual DOM mới (bản copy nhẹ của DOM thật)
3. Diffing: So sánh Virtual DOM mới vs cũ (Reconciliation)
4. Chỉ cập nhật phần thay đổi vào Real DOM (Commit phase)
```

> **Tại sao nhanh hơn?** Thao tác trên JS Object (Virtual DOM) nhanh hơn thao tác trực tiếp trên DOM thật rất nhiều.

---

## 2. JSX

**JSX (JavaScript XML)** — cú pháp mở rộng của JS, cho phép viết HTML trong file JS.

```jsx
// JSX
const element = <h1 className="title">Hello, World!</h1>;

// Sau khi Babel biên dịch (thực chất là):
const element = React.createElement('h1', { className: 'title' }, 'Hello, World!');
```

### Quy Tắc JSX Quan Trọng

```jsx
// ✅ 1. Phải có 1 root element (hoặc dùng Fragment)
return (
  <>
    <h1>Title</h1>
    <p>Content</p>
  </>
);

// ✅ 2. class → className, for → htmlFor
<div className="container">
<label htmlFor="email">Email</label>

// ✅ 3. Tag tự đóng phải có /
<img src="photo.jpg" alt="photo" />
<input type="text" />
<br />

// ✅ 4. JavaScript expression trong {}
const name = "Tuan";
<h1>Hello, {name}!</h1>
<p>{2 + 2}</p>
<p>{isLoggedIn ? "Welcome!" : "Please login"}</p>

// ✅ 5. Style là object, không phải string
<div style={{ color: 'red', fontSize: '16px' }}>Text</div>

// ❌ SAI — style là string (HTML thuần)
<div style="color: red">Text</div>
```

### Render Điều Kiện

```jsx
// Cách 1: Ternary
{isLoggedIn ? <UserPanel /> : <LoginForm />}

// Cách 2: && (short-circuit)
{isAdmin && <AdminPanel />}

// Cách 3: if/else (trong function, không trong JSX trực tiếp)
function Button({ isLoading }) {
  if (isLoading) return <Spinner />;
  return <button>Submit</button>;
}
```

### Render Danh Sách

```jsx
const fruits = ['Apple', 'Banana', 'Orange'];

// ✅ Luôn phải có key duy nhất
<ul>
  {fruits.map((fruit, index) => (
    <li key={fruit}>{fruit}</li>  // Dùng giá trị unique thay index nếu có
  ))}
</ul>

// ⚠️ Tránh dùng index làm key nếu list có thể thay đổi thứ tự
```

---

## 3. Component

### Function Component (Chuẩn hiện nay)

```jsx
// Arrow function
const Greeting = ({ name }) => {
  return <h1>Hello, {name}!</h1>;
};

// Regular function
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

// Dùng
<Greeting name="Tuan" />
```

### Component Quy Tắc

```
✅ Tên component PHẢI bắt đầu bằng chữ HOA: <MyComponent />
❌ Tên chữ thường bị hiểu là HTML tag: <myComponent />

✅ Component phải return JSX hoặc null
✅ Component là pure function — không side effect trong render
✅ Không thay đổi props (read-only)
```

### Composition vs Inheritance

React **ưu tiên Composition** thay vì Inheritance (kế thừa):

```jsx
// ✅ Composition — lồng component vào nhau
function Card({ children, title }) {
  return (
    <div className="card">
      <h2>{title}</h2>
      <div className="card-body">{children}</div>
    </div>
  );
}

// Dùng
<Card title="Profile">
  <Avatar />
  <UserInfo />
</Card>
```

---

## 4. Props

**Props (Properties)** — dữ liệu truyền từ parent xuống child component.

```jsx
// Parent truyền props
<Button label="Submit" onClick={handleSubmit} disabled={false} />

// Child nhận props
function Button({ label, onClick, disabled = false }) {
  return (
    <button onClick={onClick} disabled={disabled}>
      {label}
    </button>
  );
}
```

### Props Quan Trọng Cần Biết

```jsx
// children prop — nội dung lồng bên trong
function Container({ children }) {
  return <div className="container">{children}</div>;
}
<Container><p>Hello</p></Container>

// Spread props
const btnProps = { type: 'submit', disabled: false };
<button {...btnProps}>Click</button>

// Default props
function Input({ placeholder = 'Enter value...', type = 'text' }) { ... }

// PropTypes (kiểm tra kiểu dữ liệu)
import PropTypes from 'prop-types';
Button.propTypes = {
  label: PropTypes.string.isRequired,
  onClick: PropTypes.func,
  disabled: PropTypes.bool,
};
```

### Props vs State

| | Props | State |
|---|---|---|
| Nguồn | Từ parent | Nội tại component |
| Thay đổi | Không (read-only) | Có thể thay đổi |
| Trigger re-render | Khi parent re-render | Khi setState được gọi |
| Truy cập | Tham số function | Hook useState |

---

## 5. State & useState

**State** — dữ liệu nội tại của component, khi thay đổi → component re-render.

```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);  // [giá_trị, hàm_cập_nhật]

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>+</button>
      <button onClick={() => setCount(count - 1)}>-</button>
      <button onClick={() => setCount(0)}>Reset</button>
    </div>
  );
}
```

### Quy Tắc State Quan Trọng

```jsx
// ✅ 1. Dùng functional update khi state mới phụ thuộc vào state cũ
setCount(prev => prev + 1);  // An toàn hơn setCount(count + 1)

// ✅ 2. Object state — PHẢI spread, không mutate trực tiếp
const [user, setUser] = useState({ name: 'Tuan', age: 25 });
setUser(prev => ({ ...prev, age: 26 }));  // ✅
user.age = 26; setUser(user);             // ❌ KHÔNG làm vậy

// ✅ 3. Array state
const [items, setItems] = useState([]);
setItems(prev => [...prev, newItem]);      // Thêm
setItems(prev => prev.filter(i => i.id !== id)); // Xóa
setItems(prev => prev.map(i => i.id === id ? {...i, done: true} : i)); // Cập nhật

// ✅ 4. State batching (React 18+) — nhiều setState gộp thành 1 re-render
handleClick() {
  setCount(c => c + 1);
  setName('Tuan');
  // React 18: chỉ 1 lần re-render
}
```

### Khi Nào Nên Dùng State?

```
✅ Dùng State:
- Dữ liệu thay đổi theo thời gian (counter, form input, toggle)
- Cần trigger re-render khi thay đổi
- Dữ liệu chỉ dùng trong 1 component (hoặc cây con)

❌ Không cần State:
- Hằng số không thay đổi → dùng biến thường
- Dữ liệu có thể tính từ state/props khác → dùng useMemo
- Ref đến DOM element → dùng useRef
```

---

## 6. Vòng Đời Component (Lifecycle)

### Function Component Lifecycle (qua useEffect)

```
MOUNT (lần đầu render)
  → useEffect(() => { ... }, [])

UPDATE (state/props thay đổi)
  → useEffect(() => { ... }, [dependency])

UNMOUNT (component bị xóa khỏi DOM)
  → useEffect(() => { return () => { cleanup } }, [])
```

### So Sánh Class vs Function

| Class Component | Function Component |
|---|---|
| `componentDidMount` | `useEffect(() => {}, [])` |
| `componentDidUpdate` | `useEffect(() => {}, [dep])` |
| `componentWillUnmount` | `useEffect(() => { return cleanup }, [])` |
| `this.state` | `useState` |
| `this.setState` | `setState` function |

---

## 7. useEffect

Hook để xử lý **side effects**: gọi API, subscribe event, thao tác DOM, timers...

```jsx
import { useEffect } from 'react';

// Pattern 1: Chạy SAU MỖI render
useEffect(() => {
  console.log('Render xong');
});

// Pattern 2: Chạy 1 lần sau mount
useEffect(() => {
  fetchData();
}, []);

// Pattern 3: Chạy khi dependency thay đổi
useEffect(() => {
  document.title = `Count: ${count}`;
}, [count]);

// Pattern 4: Cleanup khi unmount
useEffect(() => {
  const timer = setInterval(() => tick(), 1000);
  return () => clearInterval(timer); // cleanup
}, []);

// Pattern 5: Gọi API đầy đủ
useEffect(() => {
  let cancelled = false;

  async function fetchUser() {
    try {
      const res = await fetch(`/api/users/${id}`);
      const data = await res.json();
      if (!cancelled) setUser(data);
    } catch (err) {
      if (!cancelled) setError(err.message);
    }
  }

  fetchUser();
  return () => { cancelled = true; }; // Chống race condition
}, [id]);
```

### useEffect — Lỗi Hay Gặp

```jsx
// ❌ Thiếu dependency → stale closure (giá trị cũ)
useEffect(() => {
  const id = setInterval(() => {
    setCount(count + 1); // count luôn là 0 (stale)
  }, 1000);
  return () => clearInterval(id);
}, []); // Thiếu [count]

// ✅ Dùng functional update để tránh stale closure
useEffect(() => {
  const id = setInterval(() => {
    setCount(c => c + 1); // Luôn lấy giá trị mới nhất
  }, 1000);
  return () => clearInterval(id);
}, []);

// ❌ Set state vô điều kiện → vòng lặp vô tận
useEffect(() => {
  setData(transform(data)); // data thay đổi → effect chạy → data thay đổi...
}, [data]);
```

---

## 8. useRef

Hook để:
1. **Truy cập DOM element** trực tiếp
2. **Lưu giá trị** không trigger re-render khi thay đổi

```jsx
import { useRef } from 'react';

// Dùng 1: Truy cập DOM
function TextInput() {
  const inputRef = useRef(null);

  function handleFocus() {
    inputRef.current.focus(); // Truy cập DOM trực tiếp
  }

  return (
    <>
      <input ref={inputRef} type="text" />
      <button onClick={handleFocus}>Focus</button>
    </>
  );
}

// Dùng 2: Lưu giá trị không cần re-render
function Timer() {
  const [count, setCount] = useState(0);
  const intervalRef = useRef(null);

  function start() {
    intervalRef.current = setInterval(() => {
      setCount(c => c + 1);
    }, 1000);
  }

  function stop() {
    clearInterval(intervalRef.current); // Không cần state
  }

  return <div>...</div>;
}
```

### useRef vs useState

| | useRef | useState |
|---|---|---|
| Trigger re-render | ❌ Không | ✅ Có |
| Truy cập giá trị | `.current` | Trực tiếp |
| Dùng cho | DOM, timer ID, previous value | UI state |

---

## 9. useContext

Chia sẻ state mà không cần truyền props qua nhiều tầng (tránh **Prop Drilling**).

```jsx
import { createContext, useContext, useState } from 'react';

// 1. Tạo Context
const ThemeContext = createContext('light');

// 2. Provider — bọc các component cần dùng
function App() {
  const [theme, setTheme] = useState('light');

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <Header />
      <Main />
    </ThemeContext.Provider>
  );
}

// 3. Consumer — dùng context ở bất kỳ component con nào
function Header() {
  const { theme, setTheme } = useContext(ThemeContext);
  return (
    <header className={theme}>
      <button onClick={() => setTheme(t => t === 'light' ? 'dark' : 'light')}>
        Toggle Theme
      </button>
    </header>
  );
}
```

### Context Khi Nào Nên Dùng?

```
✅ Dùng Context:
- Theme (dark/light mode)
- Ngôn ngữ (i18n)
- User đã đăng nhập (auth)
- Giỏ hàng (cart)

⚠️ Lưu ý:
- Context thay đổi → TẤT CẢ consumer re-render
- Không phải State Management (dùng Zustand/Redux nếu state phức tạp)
- Dùng nhiều Context riêng biệt thay vì 1 Context khổng lồ
```

---

## 10. useReducer

Thay thế `useState` khi logic state phức tạp, nhiều action.

```jsx
import { useReducer } from 'react';

// Reducer function — pure function
function cartReducer(state, action) {
  switch (action.type) {
    case 'ADD_ITEM':
      return { ...state, items: [...state.items, action.payload] };
    case 'REMOVE_ITEM':
      return { ...state, items: state.items.filter(i => i.id !== action.payload) };
    case 'CLEAR_CART':
      return { ...state, items: [] };
    default:
      throw new Error(`Unknown action: ${action.type}`);
  }
}

const initialState = { items: [], total: 0 };

function Cart() {
  const [state, dispatch] = useReducer(cartReducer, initialState);

  function addItem(item) {
    dispatch({ type: 'ADD_ITEM', payload: item });
  }

  function removeItem(id) {
    dispatch({ type: 'REMOVE_ITEM', payload: id });
  }

  return <div>...</div>;
}
```

### useState vs useReducer

| Tiêu chí | useState | useReducer |
|---|---|---|
| Độ phức tạp | State đơn giản | State phức tạp, nhiều action |
| Logic | Trực tiếp | Tập trung vào reducer |
| Debug | Khó trace | Dễ trace (action có tên rõ) |
| Testing | Khó | Dễ (test pure function) |

---

## 11. useMemo & useCallback

### useMemo — Cache kết quả tính toán

```jsx
import { useMemo } from 'react';

function ProductList({ products, filterText }) {
  // Chỉ tính lại khi products hoặc filterText thay đổi
  const filteredProducts = useMemo(() => {
    return products.filter(p =>
      p.name.toLowerCase().includes(filterText.toLowerCase())
    );
  }, [products, filterText]);

  return <ul>{filteredProducts.map(p => <li key={p.id}>{p.name}</li>)}</ul>;
}
```

### useCallback — Cache reference của function

```jsx
import { useCallback } from 'react';

function Parent() {
  const [count, setCount] = useState(0);

  // Không dùng useCallback → handleClick bị tạo mới mỗi render
  // → Child nhận prop mới → Child re-render dù không cần thiết
  const handleClick = useCallback(() => {
    console.log('clicked');
  }, []); // Dependency rỗng → function không bao giờ tạo mới

  return <Child onClick={handleClick} />;
}

// Child phải dùng React.memo để hưởng lợi
const Child = React.memo(({ onClick }) => {
  console.log('Child render');
  return <button onClick={onClick}>Click</button>;
});
```

### Khi Nào Dùng useMemo / useCallback?

```
✅ useMemo:
- Tính toán nặng (filter/sort list lớn, tính toán phức tạp)
- Tạo object/array làm dependency cho effect khác

✅ useCallback:
- Function truyền xuống child component dùng React.memo
- Function là dependency của useEffect

❌ ĐỪNG lạm dụng — Premature optimization làm code phức tạp hơn
   Chỉ dùng khi đo được vấn đề performance thực sự
```

---

## 12. Custom Hook

Tách logic tái sử dụng ra khỏi component, bắt đầu bằng `use`.

```jsx
// Hook: useFetch
function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    let cancelled = false;
    setLoading(true);

    fetch(url)
      .then(res => res.json())
      .then(data => {
        if (!cancelled) {
          setData(data);
          setLoading(false);
        }
      })
      .catch(err => {
        if (!cancelled) {
          setError(err.message);
          setLoading(false);
        }
      });

    return () => { cancelled = true; };
  }, [url]);

  return { data, loading, error };
}

// Dùng
function UserProfile({ userId }) {
  const { data: user, loading, error } = useFetch(`/api/users/${userId}`);

  if (loading) return <Spinner />;
  if (error) return <p>Error: {error}</p>;
  return <div>{user.name}</div>;
}
```

### Các Custom Hook Thường Dùng

```jsx
// useLocalStorage
function useLocalStorage(key, initialValue) {
  const [value, setValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch { return initialValue; }
  });

  const setStoredValue = (newValue) => {
    setValue(newValue);
    window.localStorage.setItem(key, JSON.stringify(newValue));
  };

  return [value, setStoredValue];
}

// useDebounce
function useDebounce(value, delay) {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const timer = setTimeout(() => setDebouncedValue(value), delay);
    return () => clearTimeout(timer);
  }, [value, delay]);

  return debouncedValue;
}

// useToggle
function useToggle(initialValue = false) {
  const [value, setValue] = useState(initialValue);
  const toggle = useCallback(() => setValue(v => !v), []);
  return [value, toggle];
}
```

---

## 13. React Router

Điều hướng (routing) cho SPA.

```bash
npm install react-router-dom
```

```jsx
import { BrowserRouter, Routes, Route, Link, NavLink,
         useNavigate, useParams, useSearchParams } from 'react-router-dom';

// Setup Router
function App() {
  return (
    <BrowserRouter>
      <nav>
        <NavLink to="/" end>Home</NavLink>
        <NavLink to="/about">About</NavLink>
        <NavLink to="/users">Users</NavLink>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/users" element={<UserList />} />
        <Route path="/users/:id" element={<UserDetail />} />
        <Route path="*" element={<NotFound />} />  {/* 404 */}
      </Routes>
    </BrowserRouter>
  );
}

// useParams — lấy :id từ URL
function UserDetail() {
  const { id } = useParams();
  return <div>User ID: {id}</div>;
}

// useNavigate — chuyển trang bằng code
function LoginForm() {
  const navigate = useNavigate();
  function handleLogin() {
    // ...
    navigate('/dashboard');        // Chuyển trang
    navigate(-1);                  // Quay lại trang trước
    navigate('/login', { replace: true }); // Thay thế history
  }
}

// useSearchParams — đọc query string ?tab=settings
function Settings() {
  const [searchParams, setSearchParams] = useSearchParams();
  const tab = searchParams.get('tab') ?? 'general';
  return <div>Tab: {tab}</div>;
}

// Protected Route
function ProtectedRoute({ children }) {
  const { isAuthenticated } = useAuth();
  return isAuthenticated ? children : <Navigate to="/login" />;
}
```

---

## 14. State Management (Redux / Zustand)

### Zustand (Đơn Giản, Hiện Đại)

```bash
npm install zustand
```

```jsx
import { create } from 'zustand';

// Tạo store
const useCartStore = create((set, get) => ({
  items: [],
  total: 0,

  addItem: (item) => set(state => ({
    items: [...state.items, item],
    total: state.total + item.price,
  })),

  removeItem: (id) => set(state => ({
    items: state.items.filter(i => i.id !== id),
    total: state.total - state.items.find(i => i.id === id)?.price ?? 0,
  })),

  clearCart: () => set({ items: [], total: 0 }),
}));

// Dùng trong component — chỉ subscribe phần cần
function CartButton() {
  const items = useCartStore(state => state.items);
  const addItem = useCartStore(state => state.addItem);
  return <button onClick={() => addItem(product)}>Cart ({items.length})</button>;
}
```

### Redux Toolkit (Dự Án Lớn)

```bash
npm install @reduxjs/toolkit react-redux
```

```jsx
// counterSlice.js
import { createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: { value: 0 },
  reducers: {
    increment: state => { state.value += 1; },   // Immer — mutate trực tiếp OK
    decrement: state => { state.value -= 1; },
    incrementByAmount: (state, action) => { state.value += action.payload; },
  },
});

export const { increment, decrement, incrementByAmount } = counterSlice.actions;
export default counterSlice.reducer;

// store.js
import { configureStore } from '@reduxjs/toolkit';
const store = configureStore({ reducer: { counter: counterReducer } });

// Component
import { useSelector, useDispatch } from 'react-redux';

function Counter() {
  const count = useSelector(state => state.counter.value);
  const dispatch = useDispatch();
  return (
    <div>
      <p>{count}</p>
      <button onClick={() => dispatch(increment())}>+</button>
    </div>
  );
}
```

---

## 15. Gọi API Trong React

### Fetch API

```jsx
function useUsers() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);

  useEffect(() => {
    setLoading(true);
    fetch('/api/users')
      .then(res => {
        if (!res.ok) throw new Error(`HTTP ${res.status}`);
        return res.json();
      })
      .then(data => setUsers(data))
      .catch(err => setError(err.message))
      .finally(() => setLoading(false));
  }, []);

  return { users, loading, error };
}
```

### Axios

```bash
npm install axios
```

```jsx
import axios from 'axios';

const api = axios.create({
  baseURL: 'https://api.example.com',
  timeout: 10000,
  headers: { 'Content-Type': 'application/json' },
});

// Interceptor — tự động thêm token
api.interceptors.request.use(config => {
  const token = localStorage.getItem('token');
  if (token) config.headers.Authorization = `Bearer ${token}`;
  return config;
});

// Dùng
const { data } = await api.get('/users');
const { data: newUser } = await api.post('/users', { name, email });
```

### TanStack Query (React Query) — Khuyến Nghị

```bash
npm install @tanstack/react-query
```

```jsx
import { useQuery, useMutation, useQueryClient } from '@tanstack/react-query';

// Fetch data
function UserList() {
  const { data: users, isLoading, error } = useQuery({
    queryKey: ['users'],
    queryFn: () => fetch('/api/users').then(res => res.json()),
    staleTime: 5 * 60 * 1000, // 5 phút
  });

  if (isLoading) return <Spinner />;
  if (error) return <p>Error: {error.message}</p>;
  return <ul>{users.map(u => <li key={u.id}>{u.name}</li>)}</ul>;
}

// Mutation (POST/PUT/DELETE)
function CreateUser() {
  const queryClient = useQueryClient();
  const mutation = useMutation({
    mutationFn: (newUser) => api.post('/users', newUser),
    onSuccess: () => {
      queryClient.invalidateQueries({ queryKey: ['users'] }); // Refetch
    },
  });

  return (
    <button onClick={() => mutation.mutate({ name: 'Tuan' })}>
      {mutation.isPending ? 'Creating...' : 'Create User'}
    </button>
  );
}
```

---

## 16. Performance Optimization

### React.memo — Tránh Re-render Không Cần Thiết

```jsx
// Component chỉ re-render khi props thực sự thay đổi
const ExpensiveComponent = React.memo(({ data, onUpdate }) => {
  console.log('Render');
  return <div>{data.name}</div>;
});

// So sánh custom
const MyComponent = React.memo(Component, (prevProps, nextProps) => {
  return prevProps.id === nextProps.id; // true = KHÔNG re-render
});
```

### Code Splitting & Lazy Loading

```jsx
import { lazy, Suspense } from 'react';

// Chỉ load khi cần (route-based splitting)
const Dashboard = lazy(() => import('./pages/Dashboard'));
const Settings = lazy(() => import('./pages/Settings'));

function App() {
  return (
    <Suspense fallback={<LoadingSpinner />}>
      <Routes>
        <Route path="/dashboard" element={<Dashboard />} />
        <Route path="/settings" element={<Settings />} />
      </Routes>
    </Suspense>
  );
}
```

### Tối Ưu Render Danh Sách Lớn

```jsx
// React Window — chỉ render item đang hiển thị
import { FixedSizeList } from 'react-window';

function VirtualList({ items }) {
  const Row = ({ index, style }) => (
    <div style={style}>{items[index].name}</div>
  );

  return (
    <FixedSizeList height={400} width="100%" itemCount={items.length} itemSize={50}>
      {Row}
    </FixedSizeList>
  );
}
```

### Checklist Performance

```
✅ Dùng React.memo cho component render nhiều
✅ useCallback cho function truyền vào memo component
✅ useMemo cho tính toán nặng
✅ Code splitting với lazy + Suspense
✅ Dùng react-window cho list > 500 items
✅ Tối ưu ảnh: WebP, lazy loading, srcset
✅ Dùng React DevTools Profiler để đo
```

---

## 17. Error Boundary

Bắt lỗi JavaScript trong cây component con, hiển thị UI fallback.

```jsx
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false, error: null };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true, error };
  }

  componentDidCatch(error, errorInfo) {
    console.error('Error caught:', error, errorInfo);
    // Gửi lên error tracking (Sentry...)
  }

  render() {
    if (this.state.hasError) {
      return this.props.fallback || <h2>Something went wrong.</h2>;
    }
    return this.props.children;
  }
}

// Dùng
<ErrorBoundary fallback={<ErrorPage />}>
  <MyComponent />
</ErrorBoundary>

// Hoặc dùng thư viện react-error-boundary
import { ErrorBoundary } from 'react-error-boundary';
<ErrorBoundary FallbackComponent={ErrorFallback} onError={logError}>
  <MyComponent />
</ErrorBoundary>
```

> ⚠️ Error Boundary **không bắt** được: async errors, event handlers, server-side errors.

---

## 18. Patterns Hay Dùng

### Compound Component

```jsx
// Các component hoạt động cùng nhau, chia sẻ state ẩn qua Context
function Select({ children, value, onChange }) {
  return (
    <SelectContext.Provider value={{ value, onChange }}>
      <div className="select">{children}</div>
    </SelectContext.Provider>
  );
}

Select.Option = function Option({ value, children }) {
  const { value: selected, onChange } = useContext(SelectContext);
  return (
    <div
      className={selected === value ? 'selected' : ''}
      onClick={() => onChange(value)}
    >
      {children}
    </div>
  );
};

// Dùng
<Select value={selected} onChange={setSelected}>
  <Select.Option value="react">React</Select.Option>
  <Select.Option value="vue">Vue</Select.Option>
</Select>
```

### Render Props

```jsx
function MouseTracker({ render }) {
  const [position, setPosition] = useState({ x: 0, y: 0 });

  return (
    <div onMouseMove={e => setPosition({ x: e.clientX, y: e.clientY })}>
      {render(position)}
    </div>
  );
}

// Dùng
<MouseTracker render={({ x, y }) => <p>Mouse: {x}, {y}</p>} />
```

### HOC (Higher-Order Component)

```jsx
// Function nhận Component, trả về Component mới với thêm tính năng
function withAuth(Component) {
  return function AuthenticatedComponent(props) {
    const { isAuthenticated } = useAuth();
    if (!isAuthenticated) return <Navigate to="/login" />;
    return <Component {...props} />;
  };
}

const ProtectedDashboard = withAuth(Dashboard);
```

---

## 19. Testing React

```bash
npm install --save-dev @testing-library/react @testing-library/user-event
```

```jsx
import { render, screen } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import Counter from './Counter';

describe('Counter', () => {
  test('renders initial count', () => {
    render(<Counter />);
    expect(screen.getByText('Count: 0')).toBeInTheDocument();
  });

  test('increments count on button click', async () => {
    const user = userEvent.setup();
    render(<Counter />);

    await user.click(screen.getByRole('button', { name: '+' }));
    expect(screen.getByText('Count: 1')).toBeInTheDocument();
  });

  test('fetches and displays users', async () => {
    // Mock fetch
    global.fetch = jest.fn().mockResolvedValue({
      ok: true,
      json: async () => [{ id: 1, name: 'Tuan' }],
    });

    render(<UserList />);
    expect(await screen.findByText('Tuan')).toBeInTheDocument();
  });
});
```

### Nguyên Tắc Testing React

```
✅ Test theo hành vi user (click, type, navigate)
✅ Query bằng role/label (getByRole, getByLabelText) thay vì class/id
✅ Dùng findBy* cho async (await screen.findByText)
✅ Tránh test implementation details (state, method name)
❌ Không test React internals — test kết quả hiển thị
```

---

## 20. Câu Hỏi Phỏng Vấn Nhanh

**Q: Virtual DOM là gì? Tại sao React dùng nó?**
> Virtual DOM là bản sao nhẹ của DOM thật trong memory. Khi state thay đổi, React tạo Virtual DOM mới, so sánh với cũ (diffing), rồi chỉ cập nhật phần khác biệt vào DOM thật → hiệu quả hơn thao tác DOM trực tiếp.

**Q: Reconciliation là gì?**
> Quá trình React so sánh Virtual DOM mới vs cũ để xác định phần nào cần cập nhật. React dùng key để nhận diện element trong list, tránh re-render không cần thiết.

**Q: useEffect vs useLayoutEffect?**
> `useEffect`: Chạy async sau khi browser paint — không block UI  
> `useLayoutEffect`: Chạy sync sau DOM update nhưng trước khi paint — dùng khi cần đọc/ghi layout (vị trí, kích thước DOM)

**Q: Tại sao không nên set state trực tiếp?**
> `state.count = 1` — React không detect thay đổi → không re-render. Phải dùng `setState` để React biết cần update.

**Q: Prop drilling là gì? Giải quyết thế nào?**
> Truyền props qua nhiều tầng component trung gian không dùng đến. Giải quyết: Context API, Zustand, Redux, hoặc component composition.

**Q: React.memo, useMemo, useCallback khác gì nhau?**
> - `React.memo`: Memoize **component** — tránh re-render khi props không đổi  
> - `useMemo`: Memoize **giá trị** — cache kết quả tính toán  
> - `useCallback`: Memoize **function** — giữ nguyên reference giữa các render

**Q: Strict Mode làm gì?**
> Trong development: mount component 2 lần để phát hiện side effect không thuần khiết. Không ảnh hưởng production.

**Q: Controlled vs Uncontrolled Component?**
> - **Controlled**: Giá trị form được kiểm soát bởi React state (`value={state}`)  
> - **Uncontrolled**: Giá trị form được DOM quản lý, dùng `ref` để đọc

---

<div align="center">

> ⚛️ **"Learn the rules well, so you can break them effectively."**  
> — React không phải magic, hiểu cơ chế → debug dễ như ăn cơm.

---

*📌 Tài liệu được cập nhật liên tục bởi [AnhhTuann](https://github.com/AnhhTuann)*  
*Phiên bản EN: [reactjs_full_notes_en.md](reactjs_full_notes_en.md)*

</div>
