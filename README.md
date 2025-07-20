# 🌈 React Learning Journey Notes

Welcome to my React Learning Journey! Here, I document useful tips, shortcuts, and best practices I discover along the way. This section will grow as I learn more. Enjoy the colorful notes and handy examples! 🚀

> 📚 **Official React Docs (Beta):** [https://react.dev/learn](https://react.dev/learn)

---

## 🧩 React Basics: The Essentials

### 🟢 JSX (JavaScript XML)
- JSX lets you write HTML-like code in JavaScript files.
- Babel compiles JSX to `React.createElement` calls.
- [JSX in React Docs](https://react.dev/learn/javascript-in-jsx-with-curly-braces)

**Example:**
```jsx
const element = <h1>Hello, world!</h1>;
```

---

### 🟦 Rendering Components
- Use `ReactDOM.render` (in older apps) or just return components in your app tree.
- [Rendering in React Docs](https://react.dev/learn/rendering-elements)

**Example:**
```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
```

---

### 🟣 Imports & Exports
- **Default export:**
  ```js
  export default App;
  // import App from './App';
  ```
- **Named export:**
  ```js
  export function Header() {}
  // import { Header } from './Header';
  ```
- You can have one default export and many named exports per file.
- [Modules in React Docs](https://react.dev/learn/importing-and-exporting-components)

---

### 🟠 Folder & File Structure
- Organize by feature or component.
- Common structure:
  ```
  src/
    components/
      Header.js
      Footer.js
    App.js
    index.js
    styles/
      App.css
  ```
- Use PascalCase for component files: `MyComponent.js`

---

### 🟡 Comments
- Use `{/* ... */}` for JSX comments.
- Use `//` or `/* ... */` for JS comments.

**Example:**
```jsx
// This is a JS comment
{/* This is a JSX comment */}
```

---

### 🟤 Keys in Lists
- Always add a unique `key` prop when rendering lists.
- [Lists & Keys in React Docs](https://react.dev/learn/rendering-lists)

**Example:**
```jsx
{items.map(item => <li key={item.id}>{item.name}</li>)}
```

---

### ⚪️ Fragments
- Use `<></>` or `<React.Fragment></React.Fragment>` to group elements without adding extra nodes to the DOM.
- [Fragments in React Docs](https://react.dev/learn/rendering-lists#keeping-list-items-in-order-with-key)

**Example:**
```jsx
return (
  <>
    <h1>Title</h1>
    <p>Description</p>
  </>
);
```

---

## ⚡️ React Code Shortcuts

Modern code editors like VS Code support handy shortcuts (snippets) for quickly scaffolding React components. Here are two of the most popular ones:

### ✨ `rfa` — React Function Component with Arrow Function

**What it does:**
- Generates a boilerplate for a React function component using an arrow function.

**Example:**
```jsx
import React from 'react';

const MyComponent = () => {
  return (
    <div>
      MyComponent
    </div>
  );
};

export default MyComponent;
```

**How to use:**
- Type `rfa` in a new `.js` or `.jsx` file and hit `Tab` (if you have the [ES7+ React/Redux/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets) extension installed in VS Code).

---

### ✨ `rafc` — React Arrow Function Component (with export)

**What it does:**
- Generates a React function component using an arrow function and immediately exports it as default.

**Example:**
```jsx
import React from 'react';

const MyComponent = () => {
  return (
    <div>
      MyComponent
    </div>
  );
};

export default MyComponent;
```

**How to use:**
- Type `rafc` and hit `Tab` (with the same extension as above).

---

## 🧠 React State & Hooks

### 🟢 What is State in React?
- **State** is a built-in object that stores property values that belong to a component.
- When state changes, the component re-renders to reflect those changes.
- [State in React Docs](https://react.dev/learn/state-a-components-memory)

**Use Case:**
- Tracking user input, toggling UI elements, counters, form data, etc.

---

### 🟦 What are Hooks?
- **Hooks** are special functions that let you "hook into" React features (like state and lifecycle methods) in function components.
- Introduced in React 16.8, hooks allow you to use state and other React features without writing a class.
- [Hooks in React Docs](https://react.dev/learn/reusing-logic-with-custom-hooks)

**Common Hooks:**
- `useState` — for state management
- `useEffect` — for side effects (like fetching data)
- `useContext` — for context API

---

### 🟣 `useState` — The State Hook

**What it does:**
- Lets you add state to function components.
- [useState in React Docs](https://react.dev/reference/react/useState)

**Syntax:**
```js
const [state, setState] = useState(initialValue);
```

**Example: Counter**
```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Add</button>
      <button onClick={() => setCount(count - 1)}>Subtract</button>
    </div>
  );
}
```

**How it works:**
- `count` is the current state value.
- `setCount` is the function to update the state.
- `useState(0)` sets the initial value to 0.

---

### 🧩 React Components, Props, Children & Prop Drilling

#### What is a Component?
- The building block of any React app. Think of components as reusable, self-contained pieces of UI.
- [Components in React Docs](https://react.dev/learn/your-first-component)

**Example:**
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}

// Usage:
<Welcome name="Alice" />
```

---

#### What are Props?
- **Props** (short for "properties") are how you pass data from a parent component to a child component.
- Props are **read-only** in the child component.
- [Props in React Docs](https://react.dev/learn/passing-props-to-a-component)

**Example:**
```jsx
function Greeting(props) {
  return <p>Welcome, {props.user}!</p>;
}

<Greeting user="Bob" />
```

---

#### Children Prop
- **`children`** is a special prop that allows you to pass elements/components between the opening and closing tags of a component.
- [Children in React Docs](https://react.dev/learn/passing-props-to-a-component#passing-jsx-as-children)

**Example:**
```jsx
function Card(props) {
  return <div className="card">{props.children}</div>;
}

<Card>
  <h2>Title</h2>
  <p>This is inside the card!</p>
</Card>
```

---

#### Prop Drilling
- **Prop Drilling** is the process of passing data from a parent component down to deeply nested child components via props, even if intermediate components don't need the data themselves.
- [Prop Drilling in React Docs](https://react.dev/learn/passing-data-deeply-with-context)

**Example:**
```jsx
function Grandparent() {
  const message = "Hello from Grandparent!";
  return <Parent message={message} />;
}

function Parent(props) {
  return <Child message={props.message} />;
}

function Child(props) {
  return <p>{props.message}</p>;
}
```

---

## 🎨 Styling in React: All the Ways!

Styling is a big part of building beautiful React apps. Here are all the main ways to style your components, with examples and tips!
- [Styling in React Docs](https://react.dev/learn/style-your-components)

### 🌍 Global CSS
- **What:** Traditional CSS files (e.g., `App.css`) imported at the top level.
- **Use Case:** App-wide styles, resets, typography, colors.

**Example:**
```css
/* App.css */
body {
  background: #f0f0f0;
  font-family: 'Segoe UI', sans-serif;
}
```
```js
import './App.css';
```

---

### 🧩 Component-Level CSS
- **What:** Import a CSS file just for one component (e.g., `Button.css`).
- **Use Case:** Styles that only apply to a specific component.

**Example:**
```css
/* Button.css */
.button {
  background: #007bff;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
}
```
```js
import './Button.css';

function Button() {
  return <button className="button">Click me</button>;
}
```

---

### 🟦 Inline Styles
- **What:** Pass a `style` prop with a JS object.
- **Use Case:** Quick, dynamic, or one-off styles.

**Example:**
```jsx
function Box() {
  return <div style={{ background: 'yellow', padding: 20 }}>Inline styled!</div>;
}
```

---

### 🟣 Dynamic Styles
- **What:** Change styles based on state or props.
- **Use Case:** Highlight active items, show/hide, change color, etc.

**Example:**
```jsx
function Toggle({ isActive }) {
  return (
    <button
      style={{
        background: isActive ? 'green' : 'gray',
        color: 'white',
      }}
    >
      {isActive ? 'Active' : 'Inactive'}
    </button>
  );
}
```

---

### 🟢 CSS Modules
- **What:** Locally scoped CSS files (e.g., `Button.module.css`).
- **Use Case:** Avoids class name collisions, great for large apps.

**Example:**
```css
/* Button.module.css */
.special {
  color: orange;
  font-weight: bold;
}
```
```js
import styles from './Button.module.css';

function Button() {
  return <button className={styles.special}>Module Button</button>;
}
```

---

### 🟠 Styled Components & CSS-in-JS
- **What:** Use libraries (like `styled-components`, `emotion`) to write CSS in JS files.
- **Use Case:** Dynamic, themeable, and scoped styles with JS power.

**Example (styled-components):**
```jsx
import styled from 'styled-components';

const FancyButton = styled.button`
  background: hotpink;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 8px;
`;

function App() {
  return <FancyButton>Styled!</FancyButton>;
}
```

---

### 🧑‍🎨 Best Practices
- Use **CSS Modules** or **CSS-in-JS** for large projects to avoid conflicts.
- Use **global CSS** for resets and base styles only.
- Use **inline/dynamic styles** for quick, state-based changes.
- Keep style logic close to the component it affects.
- Use **BEM** or similar naming for global classes.

---

## 📝 Summary
- **Global CSS:** App-wide, imported once.
- **Component CSS:** Imported per component.
- **Inline/Dynamic:** For quick or state-based styles.
- **CSS Modules:** Scoped, avoids conflicts.
- **Styled Components:** Powerful, dynamic, and themeable.

> _Mix and match these techniques for beautiful, maintainable React apps!_ 🎨✨

---

## 📡 JSON & JSON Server

### 📄 What is JSON?
- **JSON** (JavaScript Object Notation) is a lightweight data format for storing and transporting data.
- It's easy for humans to read and write, and easy for machines to parse and generate.

**Example:**
```json
{
  "name": "John Doe",
  "age": 30,
  "city": "New York",
  "hobbies": ["reading", "swimming"]
}
```

---

### 🚀 What is JSON Server?
- **JSON Server** is a full fake REST API that you can use for prototyping and mocking.
- It creates a REST API from a JSON file with zero configuration.
- Perfect for frontend development when you don't have a backend yet!

**GitHub:** [github.com/typicode/json-server](https://github.com/typicode/json-server)

---

### 🛠️ Installation & Setup

**Install globally:**
```bash
npm install -g json-server
```

**Or install locally:**
```bash
npm install json-server --save-dev
```

**Create a `db.json` file:**
```json
{
  "posts": [
    { "id": 1, "title": "First Post", "author": "John" },
    { "id": 2, "title": "Second Post", "author": "Jane" }
  ],
  "comments": [
    { "id": 1, "body": "Great post!", "postId": 1 },
    { "id": 2, "body": "Nice work!", "postId": 2 }
  ],
  "profile": {
    "name": "John Doe"
  }
}
```

**Start the server:**
```bash
json-server --watch db.json --port 3001
```

---

### 🔗 Available Endpoints

JSON Server automatically creates REST endpoints:

- `GET    /posts` - Get all posts
- `GET    /posts/1` - Get post with id 1
- `POST   /posts` - Create a new post
- `PUT    /posts/1` - Update post with id 1
- `PATCH  /posts/1` - Partially update post with id 1
- `DELETE /posts/1` - Delete post with id 1

**Additional features:**
- `GET /posts?_limit=10` - Limit results
- `GET /posts?_sort=title&_order=asc` - Sort results
- `GET /posts?title_like=react` - Search (case-insensitive)
- `GET /posts?_embed=comments` - Include related data

---

### 🧩 Using with React

**Example: Fetching data**
```jsx
import { useState, useEffect } from 'react';

function Posts() {
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    fetch('http://localhost:3001/posts')
      .then(response => response.json())
      .then(data => setPosts(data));
  }, []);

  return (
    <div>
      {posts.map(post => (
        <div key={post.id}>
          <h3>{post.title}</h3>
          <p>By: {post.author}</p>
        </div>
      ))}
    </div>
  );
}
```

**Example: Creating data**
```jsx
function CreatePost() {
  const [title, setTitle] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    
    fetch('http://localhost:3001/posts', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        title: title,
        author: 'Anonymous'
      })
    })
    .then(response => response.json())
    .then(data => console.log('Created:', data));
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        value={title}
        onChange={(e) => setTitle(e.target.value)}
        placeholder="Post title"
      />
      <button type="submit">Create Post</button>
    </form>
  );
}
```

---

### ⚙️ Advanced Configuration

**Custom port and host:**
```bash
json-server --watch db.json --port 3001 --host 0.0.0.0
```

**Add to package.json scripts:**
```json
{
  "scripts": {
    "server": "json-server --watch db.json --port 3001"
  }
}
```

**Then run:**
```bash
npm run server
```

---

### 🎯 Use Cases
- **Prototyping:** Quick API for frontend development
- **Testing:** Mock data for testing components
- **Learning:** Practice API calls without backend setup
- **Demo:** Showcase apps with realistic data

---

## 📝 Summary
- **JSON** is a data format for storing and transporting data.
- **JSON Server** creates a full REST API from a JSON file.
- Perfect for frontend development and prototyping.
- Supports all CRUD operations and advanced queries.

> _JSON Server makes frontend development a breeze!_ 🚀✨

---

## 🔄 useEffect Hook

### 🟢 What is useEffect?
- **`useEffect`** is a React Hook that lets you perform side effects in function components.
- Side effects are operations like data fetching, subscriptions, or manually changing the DOM.
- [useEffect in React Docs](https://react.dev/learn/synchronizing-with-effects)

**When to use:**
- API calls, timers, subscriptions, DOM manipulation, etc.

---

### 🟦 Basic Syntax
```jsx
useEffect(() => {
  // Side effect code here
}, [dependencies]);
```

**Parts:**
- **Effect function**: The code that runs
- **Dependency array**: Controls when the effect runs

---

### 🟣 Common Use Cases & Examples

#### 1️⃣ Run Once (Component Mount)
```jsx
import { useEffect } from 'react';

function UserProfile() {
  useEffect(() => {
    console.log('Component mounted!');
    // Fetch user data, set up subscriptions, etc.
  }, []); // Empty array = run only once

  return <div>User Profile</div>;
}
```

#### 2️⃣ Run on Every Render
```jsx
function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log('Count changed:', count);
    // This runs every time count changes
  }); // No dependency array = run every render

  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

#### 3️⃣ Run When Dependencies Change
```jsx
function UserPosts({ userId }) {
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    fetch(`/api/users/${userId}/posts`)
      .then(response => response.json())
      .then(data => setPosts(data));
  }, [userId]); // Runs when userId changes

  return <div>{posts.map(post => <div key={post.id}>{post.title}</div>)}</div>;
}
```

---

### 🟠 Cleanup Function
- **Cleanup** prevents memory leaks by cleaning up subscriptions, timers, etc.

**Example: Timer with Cleanup**
```jsx
function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setSeconds(prev => prev + 1);
    }, 1000);

    // Cleanup function
    return () => {
      clearInterval(interval);
    };
  }, []); // Empty array = run once

  return <div>Seconds: {seconds}</div>;
}
```

**Example: API Subscription**
```jsx
function ChatRoom({ roomId }) {
  useEffect(() => {
    const subscription = subscribeToRoom(roomId);

    return () => {
      subscription.unsubscribe(); // Cleanup subscription
    };
  }, [roomId]);

  return <div>Chat Room {roomId}</div>;
}
```

---

### 🟡 Dependency Array Rules

#### ✅ Empty Array `[]`
- Effect runs only once (on mount)
- Use for: Initial setup, one-time API calls

#### ✅ No Array
- Effect runs after every render
- Use carefully (can cause infinite loops)

#### ✅ With Dependencies `[dep1, dep2]`
- Effect runs when dependencies change
- Include all values from component scope that the effect uses

**Example:**
```jsx
function SearchResults({ query, filters }) {
  useEffect(() => {
    searchAPI(query, filters);
  }, [query, filters]); // Runs when query OR filters change
}
```

---

### 🟢 Common Patterns

#### Data Fetching
```jsx
function UserList() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    setLoading(true);
    fetch('/api/users')
      .then(response => response.json())
      .then(data => {
        setUsers(data);
        setLoading(false);
      })
      .catch(error => {
        console.error('Error:', error);
        setLoading(false);
      });
  }, []);

  if (loading) return <div>Loading...</div>;
  return <div>{users.map(user => <div key={user.id}>{user.name}</div>)}</div>;
}
```

#### Event Listeners
```jsx
function WindowSize() {
  const [size, setSize] = useState({ width: 0, height: 0 });

  useEffect(() => {
    const handleResize = () => {
      setSize({ width: window.innerWidth, height: window.innerHeight });
    };

    window.addEventListener('resize', handleResize);
    handleResize(); // Set initial size

    return () => {
      window.removeEventListener('resize', handleResize);
    };
  }, []);

  return <div>Window size: {size.width} x {size.height}</div>;
}
```

---

### 🧑‍💻 Best Practices
- **Always include dependencies** that the effect uses
- **Use cleanup functions** for subscriptions, timers, event listeners
- **Split effects** by purpose (don't put unrelated logic in one effect)
- **Use multiple effects** instead of one complex effect
- **Be careful with objects/arrays** in dependencies (use useCallback/useMemo if needed)

---

### 🚨 Common Mistakes
```jsx
// ❌ Missing dependency
useEffect(() => {
  setCount(count + 1);
}, []); // Should include 'count'

// ❌ Infinite loop
useEffect(() => {
  setCount(count + 1);
}, [count]); // Creates infinite loop

// ✅ Correct way
useEffect(() => {
  setCount(prev => prev + 1);
}, []); // Use functional update
```

---

## 📝 Summary
- **useEffect** handles side effects in function components
- **Dependency array** controls when the effect runs
- **Cleanup functions** prevent memory leaks
- **Use for**: API calls, subscriptions, timers, DOM manipulation

> _Master useEffect to handle side effects like a pro!_ 🔄✨

---

## 🌀 Multiple useEffects (useEffects)
- You can use `useEffect` as many times as you want in a component.
- Split effects by purpose: one for data fetching, one for subscriptions, etc.

**Example:**
```jsx
useEffect(() => {
  // Fetch data
}, []);

useEffect(() => {
  // Set up event listener
  return () => {
    // Cleanup
  };
}, []);
```

---

## 🚦 React Router: Routing in React Apps

### 🗺️ What is React Router?
- <span style="color:#007acc">**React Router**</span> is a popular library for handling navigation and routing in React applications. It allows you to display different components based on the URL, create navigation menus, and manage browser history.
- <span style="color:#228B22">React Router v6 is the latest major version (as of 2024).</span>

---

### 🛣️ Defining Routes
- <span style="color:#228B22">Routes determine which component is rendered for a given URL path.</span>
- <span style="color:#228B22">You use the <code>&lt;Routes&gt;</code> and <code>&lt;Route&gt;</code> components from <code>react-router-dom</code>.</span>

**Example:**
```jsx
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import Home from './Home';
import About from './About';
import Contact from './Contact';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </BrowserRouter>
  );
}
```
- <span style="color:#228B22">The <code>path</code> prop sets the URL, and <code>element</code> is the component to render.</span>

---

### 🔗 Navigation with Link
- <span style="color:#228B22">Use the <code>&lt;Link&gt;</code> component to navigate between routes without reloading the page (SPA behavior).</span>

**Example:**
```jsx
import { Link } from 'react-router-dom';

function Navbar() {
  return (
    <nav>
      <Link to="/">Home</Link>
      <Link to="/about">About</Link>
      <Link to="/contact">Contact</Link>
    </nav>
  );
}
```
- <span style="color:#228B22">The <code>to</code> prop sets the destination path. Clicking a <code>Link</code> updates the URL and renders the corresponding component.</span>

---

### 🧭 navLink: Active Navigation Styling
- <span style="color:#228B22">Use <code>&lt;NavLink&gt;</code> for navigation links that need to show an "active" style when the link matches the current URL.</span>

**Example:**
```jsx
import { NavLink } from 'react-router-dom';

function Navbar() {
  return (
    <nav>
      <NavLink to="/" style={({ isActive }) => ({ fontWeight: isActive ? 'bold' : 'normal' })}>
        Home
      </NavLink>
      <NavLink to="/about" className={({ isActive }) => isActive ? 'active-link' : undefined}>
        About
      </NavLink>
      <NavLink to="/contact">
        Contact
      </NavLink>
    </nav>
  );
}
```
- <span style="color:#228B22">You can use the <code>style</code> or <code>className</code> prop to apply styles when the link is active.</span>
- <span style="color:#228B22">The <code>isActive</code> argument tells you if the link matches the current route.</span>

---

### 🧑‍💻 Full Example: Simple React Router App

```jsx
// App.js
import { BrowserRouter, Routes, Route, Link, NavLink } from 'react-router-dom';

function Home() {
  return <h2>Home Page</h2>;
}
function About() {
  return <h2>About Page</h2>;
}
function Contact() {
  return <h2>Contact Page</h2>;
}

function Navbar() {
  return (
    <nav>
      <NavLink to="/" end style={({ isActive }) => ({ color: isActive ? 'red' : 'black' })}>
        Home
      </NavLink>
      {' | '}
      <NavLink to="/about" style={({ isActive }) => ({ color: isActive ? 'red' : 'black' })}>
        About
      </NavLink>
      {' | '}
      <NavLink to="/contact" style={({ isActive }) => ({ color: isActive ? 'red' : 'black' })}>
        Contact
      </NavLink>
    </nav>
  );
}

function App() {
  return (
    <BrowserRouter>
      <Navbar />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

### 🧭 useNavigate: Programmatic Navigation in React Router

- <span style="color:#007acc">**useNavigate**</span> is a React Router hook that lets you navigate to different routes in your app using JavaScript code (not just by clicking links).
- <span style="color:#228B22">This is useful for redirecting after a form submission, button click, or as a result of some logic.</span>

#### 📌 Basic Usage
```jsx
import { useNavigate } from 'react-router-dom';

function MyComponent() {
  const navigate = useNavigate();

  function handleClick() {
    navigate('/about'); // Go to the /about page
  }

  return <button onClick={handleClick}>Go to About</button>;
}
```
- <span style="color:#228B22">Calling <code>navigate('/about')</code> changes the URL and renders the corresponding route.</span>

#### 📌 Navigating with Options
- <span style="color:#228B22">You can pass options to <code>navigate</code>:</span>
  - <code>replace: true</code> replaces the current entry in the history stack (like a redirect).
  - <code>navigate(-1)</code> goes back one page (like browser back button).

**Example:**
```jsx
navigate('/login', { replace: true }); // Redirect to /login, replacing current page
navigate(-1); // Go back
```

#### 📌 Example: Redirect After Form Submit
```jsx
import { useNavigate } from 'react-router-dom';

function LoginForm() {
  const navigate = useNavigate();

  function handleSubmit(e) {
    e.preventDefault();
    // ... authentication logic ...
    navigate('/dashboard'); // Redirect to dashboard after login
  }

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" placeholder="Username" />
      <button type="submit">Login</button>
    </form>
  );
}
```

---

### 🏷️ Route Parameters (Params) in React Router

- <span style="color:#007acc">**Route parameters**</span> (params) let you capture dynamic values from the URL and use them in your components. They are useful for things like user profiles, product pages, etc.

#### 📌 Defining Route Parameters
- <span style="color:#228B22">Use a colon (<code>:</code>) in the <code>path</code> to define a param.</span>

**Example:**
```jsx
<Routes>
  <Route path="/users/:userId" element={<UserProfile />} />
</Routes>
```
- <span style="color:#228B22">Here, <code>:userId</code> is a route parameter. URLs like <code>/users/42</code> or <code>/users/alice</code> will match.</span>

#### 📌 Accessing Params with useParams
- <span style="color:#228B22">Use the <code>useParams</code> hook from <code>react-router-dom</code> to access params inside your component.</span>

**Example:**
```jsx
import { useParams } from 'react-router-dom';

function UserProfile() {
  const { userId } = useParams();
  return <h2>User ID: {userId}</h2>;
}
```
- <span style="color:#228B22">The <code>useParams</code> hook returns an object with all route params as strings.</span>

#### 📌 Multiple Params
```jsx
<Route path="/posts/:postId/comments/:commentId" element={<Comment />} />

// In Comment component:
const { postId, commentId } = useParams();
```

#### 📌 Optional Params
- <span style="color:#228B22">Add a <code>?</code> to make a param optional (React Router v6+):</span>
```jsx
<Route path="/users/:userId?" element={<UserProfile />} />
```

---

### 🔍 URL Search Params (Query Strings)
- <span style="color:#228B22">For query strings like <code>?sort=asc&page=2</code>, use the <code>useSearchParams</code> hook.</span>

**Example:**
```jsx
import { useSearchParams } from 'react-router-dom';

function Products() {
  const [searchParams, setSearchParams] = useSearchParams();
  const sort = searchParams.get('sort');
  const page = searchParams.get('page');

  return <div>Sort: {sort}, Page: {page}</div>;
}
```
- <span style="color:#228B22">You can also update search params with <code>setSearchParams</code>.</span>

---

### 🧑‍💻 Full Example: Params and Search Params
```jsx
import { BrowserRouter, Routes, Route, useParams, useSearchParams } from 'react-router-dom';

function UserProfile() {
  const { userId } = useParams();
  return <h2>User ID: {userId}</h2>;
}

function Products() {
  const [searchParams] = useSearchParams();
  const sort = searchParams.get('sort') || 'none';
  return <h2>Sort order: {sort}</h2>;
}

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/users/:userId" element={<UserProfile />} />
        <Route path="/products" element={<Products />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

### 📚 More Resources
- [React Router: useParams](https://reactrouter.com/en/main/hooks/use-params)
- [React Router: useSearchParams](https://reactrouter.com/en/main/hooks/use-search-params)

---

### ⚠️ Notes and Best Practices
- <span style="color:#228B22">Always wrap your app in <code>&lt;BrowserRouter&gt;</code> (or <code>HashRouter</code> for static hosting).</span>
- <span style="color:#228B22">Use <code>&lt;Routes&gt;</code> and <code>&lt;Route&gt;</code> for route definitions (v6+).</span>
- <span style="color:#228B22">Use <code>&lt;Link&gt;</code> or <code>&lt;NavLink&gt;</code> for navigation instead of <code>&lt;a&gt;</code> tags to avoid full page reloads.</span>
- <span style="color:#228B22">The <code>end</code> prop on <code>NavLink</code> ensures exact matching for the root path.</span>

---

### 📚 More Resources
- [React Router Docs](https://reactrouter.com/en/main)
- [React Router Tutorial](https://reactrouter.com/en/main/start/tutorial)
- [MDN: Client-side routing](https://developer.mozilla.org/en-US/docs/Glossary/Client-side_routing)

---

### 🚫 No Route Found (404 Not Found) in React Router

- <span style="color:#007acc">**Handling unknown routes**</span> is important for user experience. In React Router, you can show a custom 404 page when no route matches the current URL.

#### 📌 Basic 404 Route (React Router v6+)
- <span style="color:#228B22">Use a <code>path="*"</code> route as the last <code>&lt;Route&gt;</code> to catch all unmatched URLs.</span>

**Example:**
```jsx
import { BrowserRouter, Routes, Route } from 'react-router-dom';

function NotFound() {
  return <h2>404 - Page Not Found</h2>;
}

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="*" element={<NotFound />} />
      </Routes>
    </BrowserRouter>
  );
}
```
- <span style="color:#228B22">The <code>path="*"</code> route will match any URL that doesn't match a previous route, displaying the <code>NotFound</code> component.</span>

#### 📌 Customizing the 404 Page
- <span style="color:#228B22">You can add navigation links, images, or custom styles to your 404 page.</span>

**Example:**
```jsx
function NotFound() {
  return (
    <div style={{ textAlign: 'center', marginTop: '2rem' }}>
      <h1>404</h1>
      <p>Sorry, the page you are looking for does not exist.</p>
      <Link to="/">Go Home</Link>
    </div>
  );
}
```

---

### 📚 More Resources
- [React Router: Route Matching](https://reactrouter.com/en/main/route/matching)
- [React Router: 404 Not Found Example](https://reactrouter.com/en/main/start/tutorial#handling-not-found-errors)

---

### 🗂️ Nested Routes in React Router

- <span style="color:#007acc">**Nested routes**</span> let you render child components inside parent components based on the URL structure. This is useful for layouts, dashboards, and sections with sub-pages.

#### 📌 Defining Nested Routes
- <span style="color:#228B22">Use a parent <code>&lt;Route&gt;</code> with child <code>&lt;Route&gt;</code>s inside. The parent component should render an <code>&lt;Outlet /&gt;</code> where child routes will appear.</span>

**Example:**
```jsx
import { BrowserRouter, Routes, Route, Outlet, Link } from 'react-router-dom';

function Dashboard() {
  return (
    <div>
      <h2>Dashboard</h2>
      <nav>
        <Link to="profile">Profile</Link> | <Link to="settings">Settings</Link>
      </nav>
      <Outlet /> {/* Child routes render here */}
    </div>
  );
}

function Profile() {
  return <h3>Profile Page</h3>;
}
function Settings() {
  return <h3>Settings Page</h3>;
}

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/dashboard" element={<Dashboard />}>
          <Route index element={<DashboardHome />} />
          <Route path="profile" element={<Profile />} />
          <Route path="settings" element={<Settings />} />
        </Route>
        <Route path="/" element={<Home />} />
      </Routes>
    </BrowserRouter>
  );
}
```
- <span style="color:#228B22">Visiting <code>/dashboard/profile</code> or <code>/dashboard/settings</code> will render the corresponding child component inside <code>Dashboard</code>.</span>

#### 📌 Index Routes
- <span style="color:#228B22">Use <code>index</code> to render a default child route when the parent path is matched exactly.</span>

**Example:**
```jsx
<Route path="/dashboard" element={<Dashboard />}>
  <Route index element={<DashboardHome />} />
  <Route path="profile" element={<Profile />} />
</Route>
```
- <span style="color:#228B22">Now <code>/dashboard</code> shows <code>DashboardHome</code> by default.</span>

#### 📌 Nested Navigation
- <span style="color:#228B22">Use relative paths in <code>Link</code> (e.g., <code>to="profile"</code>) for child routes.</span>

---

### 🧑‍💻 Full Example: Nested Routes
```jsx
import { BrowserRouter, Routes, Route, Outlet, Link } from 'react-router-dom';

function Dashboard() {
  return (
    <div>
      <h2>Dashboard</h2>
      <nav>
        <Link to="profile">Profile</Link> | <Link to="settings">Settings</Link>
      </nav>
      <Outlet />
    </div>
  );
}

function DashboardHome() {
  return <h3>Welcome to your dashboard!</h3>;
}
function Profile() {
  return <h3>Profile Page</h3>;
}
function Settings() {
  return <h3>Settings Page</h3>;
}

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/dashboard" element={<Dashboard />}>
          <Route index element={<DashboardHome />} />
          <Route path="profile" element={<Profile />} />
          <Route path="settings" element={<Settings />} />
        </Route>
        <Route path="/" element={<h2>Home</h2>} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

### 📚 More Resources
- [React Router: Nested Routes](https://reactrouter.com/en/main/route/nesting)
- [React Router: Outlet](https://reactrouter.com/en/main/components/outlet)

---

## 🧠 useCallback Hook
- `useCallback` memoizes a function so it only changes if its dependencies change.
- Useful for optimizing performance, especially when passing callbacks to child components.

**Example:**
```jsx
import { useCallback, useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  const increment = useCallback(() => {
    setCount(c => c + 1);
  }, []);

  return <button onClick={increment}>Count: {count}</button>;
}
```

---

## 🖱️ onClick and Other Events
- React supports all common DOM events: `onClick`, `onChange`, `onSubmit`, `onMouseOver`, etc.
- Event handlers are camelCase and receive an event object.

**onClick Example:**
```jsx
function Button() {
  const handleClick = () => {
    alert('Button clicked!');
  };
  return <button onClick={handleClick}>Click me</button>;
}
```

**onChange Example:**
```jsx
function Input() {
  const [value, setValue] = useState('');
  return (
    <input value={value} onChange={e => setValue(e.target.value)} />
  );
}
```

**onSubmit Example:**
```jsx
function Form() {
  const handleSubmit = e => {
    e.preventDefault();
    // Do something
  };
  return (
    <form onSubmit={handleSubmit}>
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

## 📝 Summary
- Use multiple `useEffect`s for different side effects.
- Handle errors and loading for a better user experience.
- Custom hooks help you reuse logic.
- `useCallback` optimizes performance for callbacks.
- React events are camelCase and easy to use.

> _Master these patterns for robust, maintainable React apps!_ 🏆

---

### 📍 useLocation: Accessing the Current Location in React Router

- <span style="color:#007acc">**useLocation**</span> is a React Router hook that lets you access information about the current URL/location in your app.
- <span style="color:#228B22">This is useful for reading the current path, search params, hash, or state passed during navigation.</span>

#### 📌 Basic Usage
```jsx
import { useLocation } from 'react-router-dom';

function ShowLocation() {
  const location = useLocation();
  return (
    <div>
      <p>Current pathname: {location.pathname}</p>
      <p>Search string: {location.search}</p>
      <p>Hash: {location.hash}</p>
      <p>State: {JSON.stringify(location.state)}</p>
    </div>
  );
}
```
- <span style="color:#228B22">The <code>location</code> object contains:</span>
  - <code>pathname</code>: The current path (e.g., <code>"/about"</code>)
  - <code>search</code>: The query string (e.g., <code>"?sort=asc"</code>)
  - <code>hash</code>: The hash fragment (e.g., <code>"#section1"</code>)
  - <code>state</code>: Any state passed with navigation
  - <code>key</code>: Unique location key

#### 📌 Example: Using useLocation to Highlight Active Section
```jsx
import { useLocation } from 'react-router-dom';

function SectionNav() {
  const location = useLocation();
  return (
    <nav>
      <a href="#section1" style={{ fontWeight: location.hash === '#section1' ? 'bold' : 'normal' }}>Section 1</a>
      <a href="#section2" style={{ fontWeight: location.hash === '#section2' ? 'bold' : 'normal' }}>Section 2</a>
    </nav>
  );
}
```

#### 📌 Example: Reading State Passed with Navigation
```jsx
import { useLocation, useNavigate } from 'react-router-dom';

function Sender() {
  const navigate = useNavigate();
  return <button onClick={() => navigate('/target', { state: { from: 'Sender' } })}>Go</button>;
}

function Target() {
  const location = useLocation();
  return <div>Arrived from: {location.state?.from}</div>;
}
```

---

### 📚 More Resources
- [React Router: useLocation](https://reactrouter.com/en/main/hooks/use-location)

---

## 📁 Restructuring and Re-exporting with index.js

### 🗂️ Why Use an index.js File?
- <span style="color:#007acc">**index.js**</span> files are commonly used in folders to centralize and simplify imports/exports.
- <span style="color:#228B22">They allow you to re-export multiple modules from a single entry point, making imports cleaner and more maintainable.</span>

---

### 📦 Example: Exporting from index.js

Suppose you have a folder structure like this:
```
/components
  |-- Button.js
  |-- Card.js
  |-- Navbar.js
  |-- index.js
```

**Button.js**
```js
export default function Button() { /* ... */ }
```
**Card.js**
```js
export default function Card() { /* ... */ }
```
**Navbar.js**
```js
export default function Navbar() { /* ... */ }
```

**index.js** (re-exporting all components)
```js
export { default as Button } from './Button';
export { default as Card } from './Card';
export { default as Navbar } from './Navbar';
```

---

### 📥 Importing from the Folder
- <span style="color:#228B22">Now you can import all components from the folder, not individual files:</span>

```js
import { Button, Card, Navbar } from './components';
```
- <span style="color:#228B22">This is much cleaner, especially as your project grows.</span>

---

### 🧩 Re-exporting Named Exports
- <span style="color:#228B22">You can also re-export named exports from multiple files:</span>

**utils/math.js**
```js
export function add(a, b) { return a + b; }
export function subtract(a, b) { return a - b; }
```
**utils/string.js**
```js
export function capitalize(str) { /* ... */ }
export function toLower(str) { /* ... */ }
```
**utils/index.js**
```js
export * from './math';
export * from './string';
```

Now you can do:
```js
import { add, subtract, capitalize } from './utils';
```

---

### ⚠️ Notes and Best Practices
- <span style="color:#228B22">index.js is automatically resolved by import statements targeting the folder.</span>
- <span style="color:#228B22">You can use <code>index.ts</code> for TypeScript projects.</span>
- <span style="color:#228B22">This pattern is great for organizing components, hooks, utilities, and contexts.</span>
- <span style="color:#228B22">Avoid circular dependencies when re-exporting from multiple files.</span>

---

### 📚 More Resources
- [MDN: import - Re-exporting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import#re-exporting)
- [MDN: export](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export)

---

## 🗂️ Centralized Routes Folder Setup in React

### 📁 Why Use a Routes Folder?
- <span style="color:#007acc">**Centralizing your routes**</span> in a dedicated folder makes your app easier to maintain, scale, and organize, especially for larger projects.
- <span style="color:#228B22">You can define all your route components and route definitions in one place, then import them into your main <code>App.js</code> or <code>main.jsx</code>.</span>

---

### 📦 Example Folder Structure
```
/src
  /components
  /pages
  /routes
    |-- AppRoutes.js
    |-- index.js
  App.js
```

---

### 📝 Defining Routes in a Central File

**routes/AppRoutes.js**
```jsx
import { Routes, Route } from 'react-router-dom';
import Home from '../pages/Home';
import About from '../pages/About';
import Dashboard from '../pages/Dashboard';
import NotFound from '../pages/NotFound';

function AppRoutes() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
      <Route path="/dashboard/*" element={<Dashboard />} />
      <Route path="*" element={<NotFound />} />
    </Routes>
  );
}

export default AppRoutes;
```

---

### 📥 Re-exporting from index.js

**routes/index.js**
```js
export { default as AppRoutes } from './AppRoutes';
```

---

### 🧩 Using Centralized Routes in App.js

**App.js**
```jsx
import { BrowserRouter } from 'react-router-dom';
import { AppRoutes } from './routes';

function App() {
  return (
    <BrowserRouter>
      <AppRoutes />
    </BrowserRouter>
  );
}

export default App;
```

---

### ⚡ Benefits
- <span style="color:#228B22">Keeps your main <code>App.js</code> clean and focused.</span>
- <span style="color:#228B22">Makes it easy to add, remove, or update routes in one place.</span>
- <span style="color:#228B22">Encourages separation of concerns and better project structure.</span>

---

### 📚 More Resources
- [React Router: Organizing Routes](https://reactrouter.com/en/main/start/tutorial#organizing-routes)
