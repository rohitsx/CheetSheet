# Introduction to React Component

## [Source](https://react.dev/learn/your-first-component)

### Component:

React applications are constructed using isolated pieces of UI called components. A React component is a JavaScript function that you can enhance with markup.

### Exporting a Component:

To export a component, use the following syntax:

```jsx
export default function Profile() {
  return (
    <img
      src="https://i.imgur.com/MK3eW3Am.jpg"
      alt="Katherine Johnson"
    />
  );
}
