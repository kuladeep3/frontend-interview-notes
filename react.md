# React Interview Questions and Answers

### What is React?

**React** is a JavaScript library used to build user interfaces, especially for single-page applications.
It helps developers create reusable UI components and manage the user interface efficiently.

React is:

- **Component-based** – UI is broken into small, reusable pieces.
- **Declarative** – You describe what the UI should look like, and React handles the updates.
- **Fast** – Uses a virtual DOM to update only the parts that change.

It was developed by **Facebook** and is widely used in modern web development.

---

### What are the main features of React?

- **JSX:** Syntax extension allowing HTML with JavaScript.
- **Components:** Independent and reusable pieces of UI.
- **Virtual DOM:** Efficient re-rendering and updates.
- **One-way Data Binding:** Ensures data flows in a single direction.
- **Declarative UI:** Easily describe how the UI should look for any given state.

---

### What is the Virtual DOM in React?

The **virtual DOM** is a lightweight, in-memory copy of the real DOM that React uses to manage UI updates efficiently.

When something changes in a React app (like user input or state updates), React:

1. **Updates the virtual DOM** first.
2. **Compares** the updated virtual DOM with the previous version (this is called _diffing_).
3. **Finds the differences** between the two versions.
4. **Updates only the changed parts** of the real DOM.

This makes React apps faster and smoother because it avoids unnecessary DOM updates, which can be slow in large or complex interfaces.

---

### What is the difference between a class component and a functional component?

- **Class Component:** Uses ES6 classes, can hold state and lifecycle methods.

```
class MyComponent extends React.Component {
  render() {
    return <div>Hello!</div>;
  }
}
```

- **Functional Component:** Uses simple functions, can use hooks for state and lifecycle.

```
function MyComponent() {
  return <div>Hello!</div>;
}
```

---

### What are hooks in React?

Hooks are special functions that enable functional components to use state and other React features. Common hooks include:

- `useState` for state management
- `useEffect` for lifecycle events
- `useContext` for context API
- `useMemo`, `useCallback` for optimizations

---

### What is the difference between state and props?

- **State:** Local to a component, can be changed by the component itself.
- **Props:** Read-only data passed from a parent component.

---

### What is React.Fragment? Why use it?

`<React.Fragment>` or `<> ... </>` allows grouping multiple child elements without adding extra nodes to the DOM.

---

### What are Controlled and Uncontrolled Components?

In React, form elements like `<input>`, `<textarea>`, and `<select>` can be either **controlled** or **uncontrolled**.

#### Controlled Components

- React controls the value of the input.
- The value is stored in the component’s **state**.
- You update the value using a state setter function like `setState` or `useState`.

**Example:**

```jsx
const [name, setName] = useState("");
<input value={name} onChange={(e) => setName(e.target.value)} />;
```

#### Uncontrolled Components

- The input keeps track of its own value (like in plain HTML).
- You use a ref to access the value when needed.

---

### What are HOCs (Higher-Order Components) and What Are Their Use Cases?

A **Higher-Order Component (HOC)** is a **function** that takes a component and returns a new component with added functionality.

It’s a pattern used in React to **reuse component logic**.

#### Example:

```jsx
function withLoading(Component) {
  return function EnhancedComponent({ isLoading, ...props }) {
    if (isLoading) return <p>Loading...</p>;
    return <Component {...props} />;
  };
}
```

You can then wrap any component like this:

`const UserListWithLoading = withLoading(UserList);`

#### Use Cases:

- Adding common functionality (like loading, authentication, logging)
- Code reuse between components
- Wrapping third-party components
- Conditional rendering

---

### What is the `useCallback` Hook?

`useCallback` is a React hook that **memoizes a function** so it doesn’t get recreated on every render.

This is useful when you want to **prevent unnecessary re-renders** of child components that depend on that function.

#### How it works:

- You pass a function and a dependency array to `useCallback`.
- React returns the **same function instance** unless one of the dependencies changes.

#### Example:

```jsx
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]);
```

---

### What is the `useMemo` Hook?

`useMemo` is a React hook that **memoizes the result of a function** so it only recalculates when its dependencies change.

This helps **avoid expensive calculations** on every render.

#### How it works:

- You pass a function and a dependency array to `useMemo`.
- React returns the **cached value** unless one of the dependencies changes.

#### Example:

```jsx
const memoizedValue = useMemo(() => {
  return computeExpensiveValue(a, b);
}, [a, b]);
```

---

## 10. What is Redux and why use it with React?

Redux is a library for managing and centralizing application state. It is useful in large applications with a lot of shared state between components.

---

## 11. Explain the React component lifecycle.

- **Mounting:** `constructor`, `render`, `componentDidMount`
- **Updating:** `shouldComponentUpdate`, `componentDidUpdate`
- **Unmounting:** `componentWillUnmount`
  Functional components use hooks (`useEffect`) for lifecycle management.

---

## 12. What is context in React and when should you use it?

Context allows passing data through the component tree without manually passing props. It is useful for global data like authentication, theme, etc.

---

## 13. How do you optimize performance in React apps?

- Use `React.memo`, `PureComponent`
- Code-splitting with `React.lazy`, `Suspense`
- Proper use of keys in lists
- Memoize expensive functions with `useMemo`, `useCallback`

---

## 14. What is prop drilling and how to avoid it?

Prop drilling is passing data through many layers of components. Avoid it using React Context or state management libraries like Redux.

---

## 15. What are keys in React and why are they important?

Keys help React identify items in a list during DOM updates. They should be unique and help React optimize rendering.

---
