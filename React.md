# A short guide to React.js

## Introduction

React.js is a javascript library which uses a virtual DOM (document object model) which is much more efficient than the traditional DOM.

```js
import React from 'react';
import ReactDOM from 'react-dom';

function Hello() {
  return <h1>Hello, world!</h1>;
}

const root = ReactDOM.createRoot(document.getElementById('root'));

root.render(<Hello />);
```

## Intro to JSX

It is a syntax extension for JS that lets you write HTML-like markup inside a JS file.

```js
const Class = (
  <a href="https://www.internfair.com">
    <h1>
      Sign Up!
    </h1>
  </a>
);
```

### HTML Elements

 This React component "Header" renders an header element with an h1 for the website title and a nav containing links.

```js
function Header() {
  return (
    <header>
      <h1>My Awesome Website</h1>
      <nav>
        <a href="#">Home</a>
        <a href="#">About</a>
      </nav>
    </header>
  );
}
```

### Self-Closing Tags

Self-closing tags provide a concise way to write JSX for void elements.

```js
<img>, <input>, <hr> <br>
```

```js
function Image() {
  return <img src="logo.png" alt="Company Logo" />;
}
```

### JSX conditionals

JSX doesn't directly accommodate if/else syntax within embedded JavaScript. Instead, there are three alternative methods to implement conditionals with JSX elements:

1. Employ a ternary expression enclosed within curly braces directly in JSX.
2. Utilize an if statement outside JSX elements.
3. Leverage the logical AND (`&&`) operator for conditional rendering.

```js
const isUserLoggedIn = true;

return (
  <div>
    {isUserLoggedIn ? (
      <p>Welcome, User!</p>
    ) : (
      <p>Please log in to continue.</p>
    )}
  </div>
);
```

```js
// If Statement outside JSX
const isLoggedIn = false;
let greeting;

if (isLoggedIn) {
  greeting = <p>Welcome back!</p>;
} else {
  greeting = <p>Please log in to continue.</p>;
}

return <div>{greeting}</div>;
```

```js
// Logical AND (&&) Operator:
const isDataAvailable = true;
const data = ["apple", "banana", "orange"];

return (
  <div>
    {isDataAvailable && (
 <ul>
 {data.map((item, index) => (
<li key={index}>{item}</li>
  ))}
  </ul>
    )}
  </div>
);
```

### Fragments

React fragments allow you to group multiple JSX elements together without introducing an extra DOM node. This keeps your component structure clean and avoids unnecessary elements in the HTML output.

```js
function ListItem() {
  const title = "Default Title";
  const description = "This is a default description.";

  return (
    <>
      <span>{title}</span> - {description}
    </>
  );
}
```

### JSX .map() method

If you want to create a list of JSX elements from a given array, then map() over each element in the array, returning a list item for each one.

```js
const items = ['Home', 'Shop', 'About Me'];

const listItems = items.map(string => <li>{string}</li>);

<ul>{listItems}</ul>
```

### JSX key attribute

In JSX elements in a list, the key attribute is used to uniquely identify individual elements.

```js
<ul>
  <li key="key1">One</li>
  <li key="key2">Two</li>
  <li key="key3">Three</li>
  <li key="key4">Four</li>
</ul>
```

## Components

Components are independent bits of code which server purpose as JS functions but return HTML.

### Class Components

Class components in React are blueprints for creating reusable UI elements with state management and lifecycle methods.

```js
class Car extends React.Component {
  render() {
    return <h2>Hi, I am a Car!</h2>;
  }
}
```

### Functional Components

A functional component in React is a simple JavaScript function that takes props (optional) and returns JSX to define what gets rendered.

```js
function MyComponent() {
  return <h1>Hello from MyComponent!</h1>;
}
```

## Props

Props, short for properties, serve as arguments passed into React components.
Components receive props through HTML attributes.
The term "props" is derived from properties.

```js
// String Prop:
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

// Usage:
<Greeting name="John" />
```

```js
// Number Prop:
function Age(props) {
  return <p>Your age is {props.age}.</p>;
}

// Usage:
<Age age={25} />
```

```js
// Boolean Prop:
function ToggleButton(props) {
  return <button>{props.isActive ? 'Active' : 'Inactive'}</button>;
}

// Usage:
<ToggleButton isActive={true} />
```

```js
// Array Prop:
function List(props) {
  const listItems = props.items.map((item, index) => <li key={index}>{item}</li>);
  return <ul>{listItems}</ul>;
}

// Usage:
<List items={['Apple', 'Banana', 'Orange']} />
```

```js
// Object Prop:
function UserInfo(props) {
  return (
    <div>
      <p>Name: {props.user.name}</p>
      <p>Age: {props.user.age}</p>
    </div>
  );
}

// Usage:
<UserInfo user={{ name: 'Alice', age: 30 }} />
```

## React Events

Similar to HTML DOM events, React can execute actions in response to user interactions.
React supports equivalent events to HTML, such as click, change, mouseover, and more.

### Handling click events

This code sets up a button that responds when clicked. It defines a function called handleClick that logs a message to the console when the button is clicked. Then, it attaches this function to the button's onClick event handler. So, whenever someone clicks the button, the message "Button clicked!" will be logged to the console.

```js
function handleClick() {
  console.log('Button clicked!');
}

return (
  <button onClick={handleClick}>Click me</button>
);
```

### Handling Form Input Changes

This code creates an input field where users can type text. It sets up a function called handleInputChange that logs the value of the input field whenever it changes. This function is attached to the input field's onChange event handler. So, whenever someone types something into the input field, the message "Input changed:" followed by the value they typed will be logged to the console.

```js
function handleInputChange(event) {
  console.log('Input changed:', event.target.value);
}

return (
  <input type="text" onChange={handleInputChange} />
);
```

### Handling Form Submission

This code creates a form with a submit button. It sets up a function called handleSubmit that prevents the default form submission behavior (which would reload the page) and logs a message to the console when the form is submitted. This function is attached to the form's onSubmit event handler. So, when someone clicks the submit button, the message "Form submitted!" will be logged to the console, and any custom form submission logic can be performed.

```js
function handleSubmit(event) {
  event.preventDefault();
  console.log('Form submitted!');
  // Perform form submission logic
}

return (
  <form onSubmit={handleSubmit}>
    <button type="submit">Submit</button>
  </form>
);
```

### Handling Hover Events

This code sets up a <div> element that responds when the mouse hovers over it. It defines a function called handleMouseOver that logs a message to the console when the mouse hovers over the element. Then, it attaches this function to the <div> element's onMouseOver event handler. So, whenever someone hovers the mouse over the <div>, the message "Mouse over the element!" will be logged to the console.

```js
function handleMouseOver() {
  console.log('Mouse over the element!');
}

return (
  <div onMouseOver={handleMouseOver}>Hover over me</div>
);
```

### Conditional Rendering based on Events

This code creates a button that toggles the visibility of a paragraph of text. It uses React's useState hook to manage a state variable called isVisible, which determines whether the paragraph should be visible or not. It defines a function called toggleVisibility that toggles the value of isVisible when the button is clicked. Then, it attaches this function to the button's onClick event handler. Finally, it conditionally renders the paragraph based on the value of isVisible. If isVisible is true, the paragraph will be rendered; otherwise, it won't be rendered. So, when someone clicks the "Toggle Visibility" button, the paragraph will appear or disappear accordingly.

```js
function App() {
  const [isVisible, setIsVisible] = useState(false);

  function toggleVisibility() {
    setIsVisible(!isVisible);
  }

  return (
    <div>
      <button onClick={toggleVisibility}>Toggle Visibility</button>
      {isVisible && <p>This text is visible!</p>}
    </div>
  );
}
```
