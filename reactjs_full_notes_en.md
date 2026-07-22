# ⚛️ ReactJS Full Notes – Complete & Concise (English)

> **For:** Developers who know basic JS and want to master React  
> **Version:** React 18+  
> **Vietnamese version:** [reactjs_full_notes_vi.md](reactjs_full_notes_vi.md)

---

## Table of Contents

1. [What is React & Why Use It](#1-what-is-react--why-use-it)
2. [JSX](#2-jsx)
3. [Components](#3-components)
4. [Props](#4-props)
5. [State & useState](#5-state--usestate)
6. [Component Lifecycle](#6-component-lifecycle)
7. [useEffect](#7-useeffect)
8. [useRef](#8-useref)
9. [useContext](#9-usecontext)
10. [useReducer](#10-usereducer)
11. [useMemo & useCallback](#11-usememo--usecallback)
12. [Custom Hooks](#12-custom-hooks)
13. [React Router](#13-react-router)
14. [State Management (Redux / Zustand)](#14-state-management-redux--zustand)
15. [Fetching Data in React](#15-fetching-data-in-react)
16. [Performance Optimization](#16-performance-optimization)
17. [Error Boundaries](#17-error-boundaries)
18. [Common Patterns](#18-common-patterns)
19. [Testing React](#19-testing-react)
20. [Quick Interview Q&A](#20-quick-interview-qa)

---

## 1. What is React & Why Use It

**React** is a JavaScript library built by Meta for creating UIs, especially Single Page Applications (SPAs).

### React vs Angular vs Vue

| Criteria | React | Angular | Vue |
|---|---|---|---|
| Type | Library | Full Framework | Lightweight Framework |
| Language | JSX (JS + HTML) | TypeScript | Template syntax |
| Learning curve | Medium | High | Low |
| Virtual DOM | ✅ | ❌ | ✅ |
| Backed by | Meta | Google | Community |
| Best for | SPA, complex apps | Enterprise | Flexible/small apps |

### Why React is Popular

- **Component-based:** Break UI into small, reusable pieces
- **Virtual DOM:** Efficient DOM updates — only re-renders what changed
- **Unidirectional data flow:** Data flows one way → easier to debug
- **Huge ecosystem:** React Router, Redux, Next.js, React Query...
- **React Native:** Same knowledge → build mobile apps

### How Virtual DOM Works

```
1. State/Props change
2. React creates a new Virtual DOM (lightweight JS copy of real DOM)
3. Diffing: Compares new vs old Virtual DOM (Reconciliation)
4. Only updates the changed parts in the real DOM (Commit phase)
```

> **Why faster?** Operating on JS objects (Virtual DOM) is much faster than direct DOM manipulation.

---

## 2. JSX

**JSX (JavaScript XML)** — a syntax extension for JS that lets you write HTML-like code inside JS files.

```jsx
// JSX
const element = <h1 className="title">Hello, World!</h1>;

// What Babel compiles it to:
const element = React.createElement('h1', { className: 'title' }, 'Hello, World!');
```

### Key JSX Rules

```jsx
// ✅ 1. Must have a single root element (or use Fragment)
return (
  <>
    <h1>Title</h1>
    <p>Content</p>
  </>
);

// ✅ 2. class → className, for → htmlFor
<div className="container">
<label htmlFor="email">Email</label>

// ✅ 3. Self-closing tags must have /
<img src="photo.jpg" alt="photo" />
<input type="text" />
<br />

// ✅ 4. JavaScript expressions inside {}
const name = "Tuan";
<h1>Hello, {name}!</h1>
<p>{2 + 2}</p>
<p>{isLoggedIn ? "Welcome!" : "Please login"}</p>

// ✅ 5. Style is an object, not a string
<div style={{ color: 'red', fontSize: '16px' }}>Text</div>

// ❌ WRONG — style as string (plain HTML way)
<div style="color: red">Text</div>
```

### Conditional Rendering

```jsx
// Method 1: Ternary
{isLoggedIn ? <UserPanel /> : <LoginForm />}

// Method 2: && (short-circuit)
{isAdmin && <AdminPanel />}

// Method 3: if/else (inside function body, not directly in JSX)
function Button({ isLoading }) {
  if (isLoading) return <Spinner />;
  return <button>Submit</button>;
}
```

### Rendering Lists

```jsx
const fruits = ['Apple', 'Banana', 'Orange'];

// ✅ Always provide a unique key
<ul>
  {fruits.map((fruit) => (
    <li key={fruit}>{fruit}</li>  // Use unique value, not index if possible
  ))}
</ul>

// ⚠️ Avoid using array index as key if the list can reorder
```

---

## 3. Components

### Function Components (Current Standard)

```jsx
// Arrow function
const Greeting = ({ name }) => {
  return <h1>Hello, {name}!</h1>;
};

// Regular function
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

// Usage
<Greeting name="Tuan" />
```

### Component Rules

```
✅ Component names MUST start with uppercase: <MyComponent />
❌ Lowercase names are treated as HTML tags: <myComponent />

✅ Components must return JSX or null
✅ Components are pure functions — no side effects during render
✅ Never mutate props (read-only)
```

### Composition over Inheritance

React strongly favors **Composition** over class inheritance:

```jsx
// ✅ Composition — nesting components inside each other
function Card({ children, title }) {
  return (
    <div className="card">
      <h2>{title}</h2>
      <div className="card-body">{children}</div>
    </div>
  );
}

// Usage
<Card title="Profile">
  <Avatar />
  <UserInfo />
</Card>
```

---

## 4. Props

**Props (Properties)** — data passed from a parent to a child component.

```jsx
// Parent passes props
<Button label="Submit" onClick={handleSubmit} disabled={false} />

// Child receives props (destructured)
function Button({ label, onClick, disabled = false }) {
  return (
    <button onClick={onClick} disabled={disabled}>
      {label}
    </button>
  );
}
```

### Important Props Patterns

```jsx
// children prop — nested content
function Container({ children }) {
  return <div className="container">{children}</div>;
}
<Container><p>Hello</p></Container>

// Spread props
const btnProps = { type: 'submit', disabled: false };
<button {...btnProps}>Click</button>

// Default props
function Input({ placeholder = 'Enter value...', type = 'text' }) { ... }

// PropTypes (runtime type checking)
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
| Source | From parent | Internal to component |
| Mutable | No (read-only) | Yes (via setState) |
| Triggers re-render | When parent re-renders | When setState is called |
| Access | Function parameter | useState hook |

---

## 5. State & useState

**State** — internal component data that, when changed, triggers a re-render.

```jsx
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);  // [value, updater]

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

### Key State Rules

```jsx
// ✅ 1. Use functional update when new state depends on old state
setCount(prev => prev + 1);  // Safer than setCount(count + 1)

// ✅ 2. Object state — MUST spread, never mutate directly
const [user, setUser] = useState({ name: 'Tuan', age: 25 });
setUser(prev => ({ ...prev, age: 26 }));  // ✅ Correct
user.age = 26; setUser(user);             // ❌ Wrong — same reference, no re-render

// ✅ 3. Array state
const [items, setItems] = useState([]);
setItems(prev => [...prev, newItem]);                          // Add
setItems(prev => prev.filter(i => i.id !== id));              // Remove
setItems(prev => prev.map(i => i.id === id ? {...i, done: true} : i)); // Update

// ✅ 4. State batching (React 18+) — multiple setStates = one re-render
handleClick() {
  setCount(c => c + 1);
  setName('Tuan');
  // React 18: only 1 re-render total
}
```

### When to Use State?

```
✅ Use State:
- Data that changes over time (counter, form input, toggle)
- Need to trigger a re-render when it changes
- Data only used within the component (or its subtree)

❌ Don't need State:
- Constants that never change → use a regular variable
- Values derivable from existing state/props → use useMemo
- Reference to a DOM element → use useRef
```

---

## 6. Component Lifecycle

### Function Component Lifecycle (via useEffect)

```
MOUNT (first render)
  → useEffect(() => { ... }, [])

UPDATE (state/props change)
  → useEffect(() => { ... }, [dependency])

UNMOUNT (component removed from DOM)
  → useEffect(() => { return () => { cleanup } }, [])
```

### Class vs Function Component Equivalents

| Class Component | Function Component |
|---|---|
| `componentDidMount` | `useEffect(() => {}, [])` |
| `componentDidUpdate` | `useEffect(() => {}, [dep])` |
| `componentWillUnmount` | `useEffect(() => { return cleanup }, [])` |
| `this.state` | `useState` |
| `this.setState` | the `setState` function |

---

## 7. useEffect

Hook for handling **side effects**: API calls, event subscriptions, DOM manipulation, timers...

```jsx
import { useEffect } from 'react';

// Pattern 1: Run after EVERY render
useEffect(() => {
  console.log('Rendered');
});

// Pattern 2: Run once after mount
useEffect(() => {
  fetchData();
}, []);

// Pattern 3: Run when a dependency changes
useEffect(() => {
  document.title = `Count: ${count}`;
}, [count]);

// Pattern 4: Cleanup on unmount
useEffect(() => {
  const timer = setInterval(() => tick(), 1000);
  return () => clearInterval(timer); // cleanup function
}, []);

// Pattern 5: Full API fetch with cleanup
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
  return () => { cancelled = true; }; // Prevents race conditions
}, [id]);
```

### Common useEffect Mistakes

```jsx
// ❌ Missing dependency → stale closure (old value captured)
useEffect(() => {
  const id = setInterval(() => {
    setCount(count + 1); // count is always 0 (stale)
  }, 1000);
  return () => clearInterval(id);
}, []); // Missing [count]

// ✅ Use functional update to avoid stale closure
useEffect(() => {
  const id = setInterval(() => {
    setCount(c => c + 1); // Always uses latest value
  }, 1000);
  return () => clearInterval(id);
}, []);

// ❌ Unconditional setState → infinite loop
useEffect(() => {
  setData(transform(data)); // data changes → effect runs → data changes...
}, [data]);
```

---

## 8. useRef

Hook for:
1. **Accessing DOM elements** directly
2. **Storing values** that don't trigger a re-render when changed

```jsx
import { useRef } from 'react';

// Use 1: Accessing DOM
function TextInput() {
  const inputRef = useRef(null);

  function handleFocus() {
    inputRef.current.focus(); // Direct DOM access
  }

  return (
    <>
      <input ref={inputRef} type="text" />
      <button onClick={handleFocus}>Focus Input</button>
    </>
  );
}

// Use 2: Storing a value without triggering re-render
function Timer() {
  const [count, setCount] = useState(0);
  const intervalRef = useRef(null);

  function start() {
    intervalRef.current = setInterval(() => {
      setCount(c => c + 1);
    }, 1000);
  }

  function stop() {
    clearInterval(intervalRef.current); // No state needed
  }

  return <div>...</div>;
}
```

### useRef vs useState

| | useRef | useState |
|---|---|---|
| Triggers re-render | ❌ No | ✅ Yes |
| Access value | Via `.current` | Directly |
| Best for | DOM refs, timer IDs, previous value | UI state |

---

## 9. useContext

Share state across components without passing props through every level (solves **Prop Drilling**).

```jsx
import { createContext, useContext, useState } from 'react';

// 1. Create Context
const ThemeContext = createContext('light');

// 2. Provider — wrap components that need this data
function App() {
  const [theme, setTheme] = useState('light');

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <Header />
      <Main />
    </ThemeContext.Provider>
  );
}

// 3. Consumer — use context in any nested component
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

### When to Use Context?

```
✅ Good use cases for Context:
- Theme (dark/light mode)
- Language / i18n
- Authenticated user data
- Shopping cart

⚠️ Caveats:
- Context changes cause ALL consumers to re-render
- Not a state management replacement (use Zustand/Redux for complex state)
- Prefer multiple small Contexts over one giant Context
```

---

## 10. useReducer

Replace `useState` when state logic is complex or involves multiple actions.

```jsx
import { useReducer } from 'react';

// Reducer — must be a pure function
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

  return (
    <div>
      <button onClick={() => dispatch({ type: 'ADD_ITEM', payload: product })}>
        Add to Cart
      </button>
      <button onClick={() => dispatch({ type: 'CLEAR_CART' })}>
        Clear
      </button>
    </div>
  );
}
```

### useState vs useReducer

| Criteria | useState | useReducer |
|---|---|---|
| Complexity | Simple state | Complex state, many actions |
| Logic location | Inline in handlers | Centralized in reducer |
| Debugging | Harder to trace | Easy to trace (named actions) |
| Testing | Harder | Easy (pure function) |

---

## 11. useMemo & useCallback

### useMemo — Cache Computed Values

```jsx
import { useMemo } from 'react';

function ProductList({ products, filterText }) {
  // Only recalculates when products or filterText changes
  const filteredProducts = useMemo(() => {
    return products.filter(p =>
      p.name.toLowerCase().includes(filterText.toLowerCase())
    );
  }, [products, filterText]);

  return <ul>{filteredProducts.map(p => <li key={p.id}>{p.name}</li>)}</ul>;
}
```

### useCallback — Cache Function References

```jsx
import { useCallback } from 'react';

function Parent() {
  const [count, setCount] = useState(0);

  // Without useCallback → handleClick is recreated every render
  // → Child receives a new prop → Child re-renders unnecessarily
  const handleClick = useCallback(() => {
    console.log('clicked');
  }, []); // Empty deps → function is never recreated

  return <Child onClick={handleClick} />;
}

// Child must use React.memo to benefit from useCallback
const Child = React.memo(({ onClick }) => {
  console.log('Child rendered');
  return <button onClick={onClick}>Click</button>;
});
```

### When to Use useMemo / useCallback?

```
✅ useMemo:
- Heavy computations (filtering/sorting large lists)
- Creating objects/arrays used as dependencies in another effect

✅ useCallback:
- Functions passed to child components wrapped in React.memo
- Functions used as dependencies in useEffect

❌ DON'T overuse — premature optimization makes code harder to read.
   Only use when you've measured an actual performance problem.
```

---

## 12. Custom Hooks

Extract reusable logic from components into functions that start with `use`.

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

// Usage
function UserProfile({ userId }) {
  const { data: user, loading, error } = useFetch(`/api/users/${userId}`);

  if (loading) return <Spinner />;
  if (error) return <p>Error: {error}</p>;
  return <div>{user.name}</div>;
}
```

### Common Custom Hooks

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

Client-side routing for SPAs.

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

// useParams — get :id from URL
function UserDetail() {
  const { id } = useParams();
  return <div>User ID: {id}</div>;
}

// useNavigate — programmatic navigation
function LoginForm() {
  const navigate = useNavigate();
  function handleLogin() {
    navigate('/dashboard');              // Navigate to route
    navigate(-1);                        // Go back
    navigate('/login', { replace: true }); // Replace history entry
  }
}

// useSearchParams — read query string ?tab=settings
function Settings() {
  const [searchParams, setSearchParams] = useSearchParams();
  const tab = searchParams.get('tab') ?? 'general';
  return <div>Active tab: {tab}</div>;
}

// Protected Route
function ProtectedRoute({ children }) {
  const { isAuthenticated } = useAuth();
  return isAuthenticated ? children : <Navigate to="/login" />;
}
```

---

## 14. State Management (Redux / Zustand)

### Zustand (Simple & Modern)

```bash
npm install zustand
```

```jsx
import { create } from 'zustand';

// Create a store
const useCartStore = create((set, get) => ({
  items: [],
  total: 0,

  addItem: (item) => set(state => ({
    items: [...state.items, item],
    total: state.total + item.price,
  })),

  removeItem: (id) => set(state => ({
    items: state.items.filter(i => i.id !== id),
    total: state.total - (state.items.find(i => i.id === id)?.price ?? 0),
  })),

  clearCart: () => set({ items: [], total: 0 }),
}));

// Subscribe to only what you need — avoids unnecessary re-renders
function CartButton() {
  const items = useCartStore(state => state.items);
  const addItem = useCartStore(state => state.addItem);
  return <button onClick={() => addItem(product)}>Cart ({items.length})</button>;
}
```

### Redux Toolkit (Large-scale Apps)

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
    increment: state => { state.value += 1; },   // Immer lets you "mutate"
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

## 15. Fetching Data in React

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

// Interceptor — automatically attach auth token
api.interceptors.request.use(config => {
  const token = localStorage.getItem('token');
  if (token) config.headers.Authorization = `Bearer ${token}`;
  return config;
});

// Usage
const { data } = await api.get('/users');
const { data: newUser } = await api.post('/users', { name, email });
```

### TanStack Query (React Query) — Recommended

```bash
npm install @tanstack/react-query
```

```jsx
import { useQuery, useMutation, useQueryClient } from '@tanstack/react-query';

// Fetching data
function UserList() {
  const { data: users, isLoading, error } = useQuery({
    queryKey: ['users'],
    queryFn: () => fetch('/api/users').then(res => res.json()),
    staleTime: 5 * 60 * 1000, // 5 minutes cache
  });

  if (isLoading) return <Spinner />;
  if (error) return <p>Error: {error.message}</p>;
  return <ul>{users.map(u => <li key={u.id}>{u.name}</li>)}</ul>;
}

// Mutations (POST/PUT/DELETE)
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

### React.memo — Prevent Unnecessary Re-renders

```jsx
// Component only re-renders when props actually change
const ExpensiveComponent = React.memo(({ data, onUpdate }) => {
  console.log('Rendered');
  return <div>{data.name}</div>;
});

// Custom comparison function
const MyComponent = React.memo(Component, (prevProps, nextProps) => {
  return prevProps.id === nextProps.id; // true = DON'T re-render
});
```

### Code Splitting & Lazy Loading

```jsx
import { lazy, Suspense } from 'react';

// Only load when needed (route-based splitting)
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

### Virtualize Large Lists

```jsx
// React Window — only renders visible items
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

### Performance Checklist

```
✅ Use React.memo for frequently rendered components
✅ useCallback for functions passed to memo components
✅ useMemo for expensive computations
✅ Code split with lazy + Suspense
✅ Use react-window for lists > 500 items
✅ Optimize images: WebP, lazy loading, srcset
✅ Use React DevTools Profiler to measure
```

---

## 17. Error Boundaries

Catch JavaScript errors in a component subtree and display a fallback UI.

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
    // Send to error tracking (Sentry, etc.)
  }

  render() {
    if (this.state.hasError) {
      return this.props.fallback || <h2>Something went wrong.</h2>;
    }
    return this.props.children;
  }
}

// Usage
<ErrorBoundary fallback={<ErrorPage />}>
  <MyComponent />
</ErrorBoundary>

// Or use react-error-boundary library
import { ErrorBoundary } from 'react-error-boundary';
<ErrorBoundary FallbackComponent={ErrorFallback} onError={logError}>
  <MyComponent />
</ErrorBoundary>
```

> ⚠️ Error Boundaries do **NOT** catch: async errors, event handler errors, server-side errors.

---

## 18. Common Patterns

### Compound Components

```jsx
// Components that work together, sharing hidden state via Context
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

// Usage
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

// Usage
<MouseTracker render={({ x, y }) => <p>Mouse: {x}, {y}</p>} />
```

### HOC (Higher-Order Component)

```jsx
// Takes a Component, returns a new Component with extra behavior
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

### React Testing Principles

```
✅ Test user behavior (clicks, typing, navigation)
✅ Query by role/label (getByRole, getByLabelText) over class/id
✅ Use findBy* for async (await screen.findByText)
✅ Avoid testing implementation details (state names, method names)
❌ Don't test React internals — test what the user sees
```

---

## 20. Quick Interview Q&A

**Q: What is the Virtual DOM? Why does React use it?**
> The Virtual DOM is a lightweight in-memory copy of the real DOM. When state changes, React creates a new Virtual DOM, diffs it against the old one (reconciliation), then only updates the changed parts in the real DOM — more efficient than direct DOM manipulation.

**Q: What is Reconciliation?**
> The process React uses to compare the new vs old Virtual DOM to determine what needs updating. React uses `key` props to identify elements in lists and avoid unnecessary re-renders.

**Q: useEffect vs useLayoutEffect?**
> `useEffect`: Runs asynchronously after the browser paints — doesn't block the UI.  
> `useLayoutEffect`: Runs synchronously after DOM updates but before the browser paints — use when you need to read/write layout (positions, dimensions).

**Q: Why shouldn't you set state directly?**
> `state.count = 1` — React doesn't detect the change → no re-render. You must use the `setState` function so React knows to update.

**Q: What is Prop Drilling? How do you fix it?**
> Passing props through many intermediate components that don't need them. Solutions: Context API, Zustand, Redux, or component composition.

**Q: What's the difference between React.memo, useMemo, and useCallback?**
> - `React.memo`: Memoizes a **component** — prevents re-render if props didn't change  
> - `useMemo`: Memoizes a **value** — caches an expensive computation result  
> - `useCallback`: Memoizes a **function** — keeps the same function reference across renders

**Q: What does Strict Mode do?**
> In development: mounts components twice to detect impure side effects. Has no impact on production.

**Q: Controlled vs Uncontrolled Components?**
> - **Controlled**: Form value managed by React state (`value={state}`)  
> - **Uncontrolled**: Form value managed by the DOM, read via `ref`

**Q: When would you use useReducer over useState?**
> When the state logic is complex, involves multiple sub-values, or the next state depends on the previous one in a non-trivial way. Also when you want centralized, testable, and named state transitions.

**Q: What is the key prop and why is it important?**
> A unique identifier for elements in a list. Helps React identify which items have changed, been added, or removed during reconciliation — preventing unnecessary DOM recreation.

---

<div align="center">

> ⚛️ **"Learn the rules well, so you can break them effectively."**  
> React isn't magic — understand the mechanics → debug like a pro.

---

*📌 Continuously updated by [AnhhTuann](https://github.com/AnhhTuann)*  
*Vietnamese version: [reactjs_full_notes_vi.md](reactjs_full_notes_vi.md)*

</div>
