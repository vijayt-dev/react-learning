# React JS

## What is React?

A react is a javascript library for building user interface.

React was created by Jordan Walke, who was a software engineer at Facebook.


## Setting up a React Environment

If you have npx and Node.js installed, you can create a React application by using create-react-app.

Run this command to create a React application named my-react-app:

```bash
npx create-react-app my-react-app
```

## Run the React Application

```bash
cd my-react-app
```

Run this command to run the React application my-react-app:

```bash
npm start
```

A new browser window will pop up with your newly created React App! If not, open your browser and type localhost:3000 in the address bar.

## React Render

### The Render Function

The ReactDOM.render() function takes two arguments, HTML code and an HTML element.

The purpose of the function is to display the specified HTML code inside the specified HTML element.

```javascript
ReactDOM.render(<p>Hello</p>, document.getElementById('root'));
```

## What is JSX?

JSX stands for JavaScript XML.

JSX allows us to write HTML in React.

JSX makes it easier to write and add HTML in React.

JSX converts HTML tags into react elements.

**With JSX**
```javascript
const myElement = <h1>I Love JSX!</h1>;

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(myElement);
```

**Without JSX**

```javascript
const myElement = React.createElement('h1', {}, 'I do not use JSX!');

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(myElement);
```

## Expressions in JSX

With JSX you can write expressions inside curly braces { }.

The expression can be a React variable, or property, or any other valid JavaScript expression. JSX will execute the expression and return the result.

```javascript
const userName = "John";
const myElement = <h1>React is {userName} times better with JSX</h1>;
```

JSX will throw an error if the HTML is not correct, or if the HTML misses a parent element.

you can use a "fragment" to wrap multiple lines. This will prevent unnecessarily adding extra nodes to the DOM.

A fragment looks like an empty HTML tag: <></>

```javascript
const myElement = (
  <>
    <p>I am a paragraph.</p>
    <p>I am a paragraph too.</p>
  </>
);
```
JSX will throw an error if the HTML is not properly closed.

## Attribute class = className

The class attribute is a much used attribute in HTML, but since JSX is rendered as JavaScript, and the class keyword is a reserved word in JavaScript, you are not allowed to use it in JSX. Use attribute className instead. When JSX is rendered, it translates className attributes into class attributes.

## React Components
Components are like functions that return HTML elements.

Components are independent and reusable bits of code.

Components are two types:
1.	Class components 
2.	Function components

### Class Component

A class component must include the extends React.Component statement. This statement creates an inheritance to React.Component, and gives your component access to React.Component's functions.

The component also requires a render() method, this method returns HTML.

```javascript
class FirstComponent extends React.Component {
  render() {
    return <h2>Hi, I am a FirstComponent!</h2>;
  }
}
```

### Function Component

A Function component also returns HTML, and behaves much the same way as a Class component, but Function components can be written using much less code, are easier to understand.

```javascript
function FirstComponent() {
  return <h2>Hi, I am a FirstComponent!</h2>;
}
```

## Props

Components can be passed as props, which stands for properties.

Props are like function arguments, and you send them into the component as attributes.


```javascript
function Car(props) {
  return <h2>I am a {props.color} Car!</h2>;
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Car color="red"/>);
```

## React Events

React can perform actions based on user events.

React has the same events as HTML: click, change, mouseover etc.

```javascript
function Click() {
  const click = () => {
    alert("Clicked");
  }

  return (
    <button onClick={click}>Click Me</button>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Click  />);
```

## React Lists
you will render lists with some type of loop.

The JavaScript map() array method is generally the preferred method.

```javascript
function Car(props) {
  return <li>I am a { props.brand }</li>;
}

function Garage() {
  const cars = ['Ford', 'BMW', 'Audi'];
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <ul>
        {cars.map((car) => <Car brand={car} />)}
      </ul>
    </>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Garage />);

```

### Keys

Keys allow React to keep track of elements. This way, if an item is updated or removed, only that item will be re-rendered instead of the entire list.

Keys need to be unique to each sibling. But they can be duplicated globally.

## React useState Hook

The React useState Hook allows us to track state in a function component.

State generally refers to data or properties that need to be tracking in an application

### Import useState
To use the useState Hook, we first need to import it into our component.

At the top of your component, import the useState Hook.

```javascript
import { useState } from "react";
```

### Initialize useState
We initialize our state by calling useState in our function component.

useState accepts an initial state and returns two values:

1. The current state.
2. A function that updates the state.

**Example**
```javascript
import { useState } from "react";
import ReactDOM from "react-dom/client";

function FavoriteColor() {
  const [color, setColor] = useState("red");

  return (
    <>
      <h1>My favorite color is {color}!</h1>
      <button
        type="button"
        onClick={() => setColor("blue")}
      >Blue</button>
    </>
  )
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<FavoriteColor />);
```
