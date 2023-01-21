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
```jsx
const myElement = <h1>I Love JSX!</h1>;

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(myElement);
```

**Without JSX**

```jsx
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

props stands for properties.


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



## State

### props vs state

| props  | state  |
| ------------ | ------------ |
| props get passed to the component  | state is managed within the component  |
| Function parameters   | Variables declared in the function body   |
| props,this.props  | useState Hook, this.state   |

## setState

**Do's and Don't**

1) Always make use of setState and never modify the state directly
2) Code has to be executed after the state has been updated? Place that code in the call back fucntion which is the second argument to the setState method.
3) When you have to update state based on the previous state value, pass in a function as an argument instead of the regular object.
4) React may group multiple setState calls into a single update for better performance and set state calls are done in one single go and the updated value does not carry over between the different calls.


## Binding Event Handlers

Event handlers are not work this keyword it return undefined

1) use bind()

onClick={this.clickHandler.bind(this)}
2) use arrow function
onClick={() => this.clickHandler()}
3) binding from constructor
this.clickHandler = this.clickHandler.bind(this); (Prefer)
4) binding from arrow function
clickHandler = () => {
	this.setState({
		message: "Hello"
	})
}

## List and Keys

1.  A "key" is a special string attribute you need to include when creating lists of elements.

2. Keys give the elements a stable identity

3. Keys help React identity which items have changes, are added or are removed.

4. Help in efficient update of the user interface.


## Index as Key

### When to use index as a key?

1. The items i your list do not have a unique id.
2. The list is a static list and will not change
3. The list will never be reordered or filtered

## React Hooks

### useState Hook

The React useState Hook allows us to track state in a function component.

useState accepts an initial state and returns two values:
-  The current state.
- A function that updates the state.

**Syntax**

`useState(initialState);`

**Example**
```javascript
import { useState } from "react";
import ReactDOM from "react-dom/client";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <>
      <h1>Count {count}</h1>
      <button
        type="button"
        onClick={() => setCount(count + 1)}
      >Increment</button>
    </>
  )
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Counter />);
```

The useState Hook can be used to keep track of strings, numbers, booleans, arrays, objects, and any combination of these.

The setCount function recieves the previous value.

**Example**

```javascript
setCount(prevCount => prevCount + 1)
```

### useEffect Hook

The useEffect Hook allows you to perform side effects in your components.

Some examples of side effects are: fetching data,and timers.

useEffect accepts two arguments. The second argument is optional.

**Syntax**

`useEffect(<function>,<dependency>)`

We should always include the second parameter which accepts an array. We can optionally pass dependencies to useEffect in this array.

1. No dependency passed

`useEffect(() => {
  //Runs on every render
});`

2. An empty array:

`useEffect(() => {
  //Runs only on the first render
}, []);`

3. Props or state values:

`useEffect(() => {
  //Runs only on the first render
}, []);`

**Syntax**
`useContext(MyContext)`

**Example**

```javascript
import React,{useState,useEffect} from 'react';
import axios from 'axios';
function Data() {
    const [posts,setPosts] = useState({})
    const [id,setId] = useState(1)
    const [idBtn,setIdbtn] = useState(1)
    const handClick = () =>{
        setIdbtn(id)
    }
    useEffect(() => {
        axios.get(`https://jsonplaceholder.typicode.com/posts/${id}`)
        .then(res => {
           setPosts(res.data)
            console.log(res)
        })
        .catch(err => {
            console.log(err)
        })
    },[idBtn])
  return (
    <div>
        <input type="text" value={id} onChange={(e) => { setId(e.target.value)}} />
        <button onClick={handClick}>Click Me</button>
        <ul>
            {
               <li key={posts.id}>{posts.title}</li>
            }
        </ul>
    </div>
  )
}

export default Data;
```

### useContext Hook

The React Context API provides a way to share states or data throughout the React component tree.

The API makes data sharing between components easy while eliminating prop drilling.

first create a context using React.createContext and this context can then be passed to the hook.



**Example**

```javascript
import { useState, createContext } from "react";
import Component1 from "./Component1";
import Component2 from "./Component2";

import ReactDOM from "react-dom/client";

export const CounterContext = createContext()

function App() {
  const [count, setCount] = useState(0);

  return (
    <div className="App">
	<h1>{count}</h1>
	<CounterContext.Provider value={{count,setCount}}>
     <Component1 />
	 <Component2 />
</CounterContext.Provider>	 
    </div>
  );
}

export default App;
```

```javascript
import React, { useContext } from 'react'
import { CounterContext } from './App';

function Component2() {
  const countContext = useContext(CounterContext);
  return (
    <div>
       <h1>Count2 {countContext.count}</h1>
        <button onClick={() => countContext.setCount(countContext.count +1)}>Increment</button>
    </div>
  )
}

export default Component2;
```

### useRef Hook

The useRef Hook allows you to persist values between renders.

It can be used to store a mutable value that does not cause a re-render when updated.

It can be used to access a DOM element directly.

**Syntax**
`useRef(initialValue);`

**Example**

#### Does Not Cause Re-renders

Use useRef to track application renders.

```javascript
import { useState, useEffect, useRef } from "react";
import ReactDOM from "react-dom/client";

function App() {
  const [inputValue, setInputValue] = useState("");
  const count = useRef(0);

  useEffect(() => {
    count.current = count.current + 1;
  });

  return (
    <>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <h1>Render Count: {count.current}</h1>
    </>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
```

useRef() only returns one item. It returns an Object called current.

#### Accessing DOM Elements

we can add a ref attribute to an element to access it directly in the DOM.

```javascript
import { useRef } from "react";
import ReactDOM from "react-dom/client";

function App() {
  const inputElement = useRef();

  const width = () => {
    inputElement.current.style.width = "300px";
  };

  return (
    <>
      <input type="text" ref={inputElement} />
      <button onClick={width}>Cick</button>
    </>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
```

### useReducer Hook

The useReducer Hook is similar to the useState Hook.

It keeping track of multiple pieces of state that rely on complex logic, useReducer may be useful.

**Syntax**

`useReducer(<reducer>, <initialState>)`

The reducer function contains your custom state logic and the initialState can be a simple value but generally will contain an object.

The useReducer Hook returns the current stateand a dispatch method.

**Example**

```javascript
import React, { useReducer } from "react";

function CounterOne() {
  const initialState = { counter: 0 };
  function reducer(state, action) {
    switch (action.type) {
      case "increment":
        console.log(state, action);
        return {counter: state.counter + action.value};
      case "decrement":
        return {counter: state.counter - action.value};
      case "reset":
        return {counter: 0};
      default:
        return {counter: state.counter};
    }
  }
  const [count, dispatch] = useReducer(reducer, initialState);
  return (
    <div>
      <div>
        <h1>Count1 {count.counter}</h1>
        <button onClick={() => dispatch({type:"increment",value: 1})}>Increment</button>
        <button onClick={() => dispatch({type: "decrement",value: 1})}>Decrement</button>
        <button onClick={() => dispatch({type:"increment",value:2})}>Increment 2</button>
        <button onClick={() => dispatch({type: "decrement",value:2})}>Decrement 2</button>
        <button onClick={() => dispatch({type: "reset"})}>Reset</button>
      </div>
    </div>
  );
}

export default CounterOne;

```

### useCallback Hook

The React useCallback Hook returns a memoized callback function.

Think of memoization as caching a value so that it does not need to be recalculated.

The useCallback Hook only runs when one of its dependencies update.

The useCallback and useMemo Hooks are similar. The main difference is that useMemo returns a memoized value and useCallback returns a memoized function.

**Syntax**
`useCallback(
  () => {
    doSomething(a, b);
  },
  [a, b],
);`

**Example**

```javascript
import React, {useState,useCallback, useEffect } from 'react'

function Callback() {
const [number,setNumber] = useState(1)
const [dark,setDark] = useState(false)

const getItems = useCallback(() => {
    return [number, number + 1, number + 2]
},[number])
const theme = {
    backgroundColor: dark ? "#333" : "#fff",
    color: dark ? "#fff" : "#333"
}
useEffect(() => {
    console.log("Update")
},[getItems])
  return (
    <div style={theme}>
        <input type="number" value={number} onChange={e => setNumber(e.target.value)} />
        <button onClick={() => setDark(prevDark => ! prevDark)}>
            Toggle Theme
        </button>

        <div>
            {
                getItems().map(item => <div key={item}>{item}</div>)
            }
        </div>
    </div>
  )
}

export default Callback
```

### useMemo Hook

The React useMemo Hook returns a memoized value.

The useMemo Hook only runs when one of its dependencies update.

This can improve performance.

**Syntax**

`useMemo(() => computeExpensiveValue(a, b), [a, b]);`

**Example**

```javascript
import React, { useCallback, useMemo, useState } from 'react'

function CounterMemo() {
    const [countOne,setCountOne] = useState(0)
    const [countTwo,setCountTwo] = useState(0)
    const [toggle,setToggle] = useState(false)
    const incrementOne = () => {
        setCountOne(countOne+ 1)
    }
    const incrementTwo = () => {
        setCountTwo(countTwo + 1)
    }
     const isEven = useMemo( () => {
         while(i < 9000000000) i++
         console.log("Render")
        return countOne % 2 === 0
     },[countOne])
  return (
    <div>
        <h1>Count1 {countOne}</h1>
        <button onClick={() => {incrementOne()}}>Increment</button>
        {isEvenCall ?  "Even" : "Odd"}
        <h1>Count2 {countTwo}</h1>
        <button onClick={() => incrementTwo()}>Increment</button>
        <button onClick={() => setToggle(!toggle)}>Toggle</button>
        {toggle && <p>Toggle</p>}

    </div>
  )
}

export default CounterMemo
```

### Custom Hooks

Hooks are reusable functions.

Custom Hooks start with "use". Example: useFetch.

**Example**

useFetch.js

```javascript
import { useState, useEffect } from "react";

const useFetch = (url) => {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(url)
      .then((res) => res.json())
      .then((data) => setData(data));
  }, [url]);

  return [data];
};

export default useFetch;
```

index.js

```javascript
import ReactDOM from "react-dom/client";
import useFetch from "./useFetch";

const Home = () => {
  const [data] = useFetch("https://jsonplaceholder.typicode.com/todos");

  return (
    <>
      {data &&
        data.map((item) => {
          return <p key={item.id}>{item.title}</p>;
        })}
    </>
  );
};

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Home />);
```

### useId Hook

useId is a hook for generating unique IDs.

**Syntax**
`const id = useId();`

```javascript
function NameFields() {
  const id = useId();
  return (
    <div>
      <label htmlFor={id + '-firstName'}>First Name</label>
      <div>
        <input id={id + '-firstName'} type="text" />
      </div>
      <label htmlFor={id + '-lastName'}>Last Name</label>
      <div>
        <input id={id + '-lastName'} type="text" />
      </div>
    </div>
  );
}
```

## React Router

### What is React Router?

- It is a fully-featured client and server-side routing library for React.
- Helps create and navigate between different URLs that make up your web application.
- Provides unique URLs for differenet components in the app and makes the UI easily shareable with other users.

### Configuring Routes

- Connect the url in the browser with our react application through a component called browser router.
- Routes for each component and where and which component they will render when the path matches with the base URL entered or clicked by the user.
-  Route is the conditionally shown component that renders some UI when its path matches the current URL.

**Example**

index.js

```javascript
import React from "react";
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";
import { BrowserRouter } from "react-router-dom";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>
);
```

App.js

```javascript
import {Routes,Route} from "react-router-dom"
import Admin from "./Admin";
import Featured from "./Component/Featured";
import Home from "./Component/Home";
import NavBar from "./Component/NavBar";
import New from "./Component/New";
import NoMatch from "./Component/NoMatch";
import Order from "./Component/Order";
import OrderSummary from "./Component/OrderSummary";
import Product from "./Component/Product";
import UserDetails from "./UserDetails";
import Users from "./Users";
function App() {

  return (
    <div className="App">
      <NavBar />
      <Order />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="product" element={<Product />}>
          <Route index element={<Featured />} />
          <Route path="featured" element={<Featured />} />
          <Route path="new" element={<New />} />
        </Route>
        <Route path="user" element={<Users />}>
        <Route path=":userID" element={<UserDetails />} />
        <Route path="admin" element={<Admin />} />
        </Route>

        <Route path="order-summary" element={<OrderSummary />} />
        <Route path="*" element={<NoMatch />} />
      </Routes>
    </div>
  );
}

export default App;
```

### Links

- To navigate between the routes react provides the link component.

**Example**
NavBar.js

```javascript
import React from 'react'
import { Link } from 'react-router-dom'

function NavBar() {
  return (
    <div>
        <nav>
            <Link to="/">Home </Link>
            <Link to="/about">About </Link>
            <Link to="/product">Product</Link>
        </nav>
    </div>
  )
}

export default NavBar
```

### Active Links

- NavLink component provides which knows whether or not it is the active link.
- NavLink componet have a set property isActive, isPending.

```javascript
import React from 'react'
import { NavLink } from 'react-router-dom'

function NavBar() {
    const navLinkStyle = ({isActive}) => {
        return {
            fontWeight: isActive ? "bold" : "normal",
            color: isActive ? "#eee" : "#123"
        }
    }
  return (
    <div>
        <nav>
            <NavLink style={navLinkStyle} to="/">Home </NavLink>
            <NavLink style={navLinkStyle} to="/about">About </NavLink>
            <NavLink style={navLinkStyle} to="/product">Product</NavLink>

        </nav>
    </div>
  )
}

export default NavBar
```

### Navigating Programmatically

- To navigate programmatically react router provides the useNavigate hook.
**Example**

Order.js

```javascript
import React from 'react'
import { useNavigate } from 'react-router-dom'

function Order() {
    const navigate = useNavigate();
  return (
    <div>
        <button onClick={() => navigate("order-summary")}>Order</button>
    </div>
  )
}
export default Order
```

### No Match Route

1. Inform the user that the url does not exist

App.js

```javascript
import {Routes,Route} from "react-router-dom"
import NoMatch from "./Component/NoMatch";
function App() {

  return (
    <div className="App">
      <Routes>
        <Route path="*" element={<NoMatch />} />
      </Routes>
    </div>
  );
}

export default App;
```

### Nested Route

- The parent route have nested child route.
- The react router forms the full path to the children routes.
- Routes to render the child components within the parent component.
- Where to render the child component for that react router provides the Outlet component.
- An Outlet should be used in parent route elements to render their child route elements. This allows nested UI to show up when child routes are rendered.

**Example**

Product.js

```javascript
import React from 'react'
import { NavLink, Outlet } from 'react-router-dom'

function Product() {
  return (
    <div>
        <input type="search" placeholder="Search products" />
        <nav>
            <NavLink to="featured">Featured</NavLink>
            <NavLink to="new">New</NavLink>
        </nav>
        <Outlet />
    </div>
  )
}

export default Product
```

### Index Route

- Nested routes want a route to be rendered at the parent url make use of an index route.
- Index route will now share the path of the parent route.

App.js

```javascript
import {Routes,Route} from "react-router-dom"
import Product from "./Component/Product";
import Featured from "./Component/Featured";
import New from "./Component/New";

function App() {

  return (
    <div className="App">
      <Routes>
        <Route path="product" element={<Product />}>
          <Route index element={<Featured />} />
          <Route path="featured" element={<Featured />} />
          <Route path="new" element={<New />} />
        </Route>
      </Routes>
    </div>
  );
}

export default App;
```

### Dynamic Route

- When dealing with a list detail pattern or if the route parameter can vary in value make use of dynamic routes specify the url param denoted by a colon prefix in the path.
- React router try to match the route that is more specific before trying to match a dynamic route.

**Example**
App.js

```javascript
import {Routes,Route} from "react-router-dom"
import UserDetails from "./UserDetails";
import Users from "./Users";
import Admin from "./Admin";


function App() {

  return (
    <div className="App">
      <Routes>
        <Route path="user" element={<Users />}>
        <Route path=":userID" element={<UserDetails />} />
        <Route path="admin" element={<Admin />} />
        </Route>
        </Route>
      </Routes>
    </div>
  );
}

export default App;
```


### URL Params

- The useParams hook returns an object of key value pairs.
- The object contains key value pairs of the dynamic params from the current url.

**Example**

UserDetails.js

```javascript
import React from 'react'
import { useParams } from 'react-router-dom'
function UserDetails() {
    const params = useParams()
    console.log(params)
  return (
    <div>UserDetails {params.userID}</div>
  )
}
export default UserDetails
```

## Search Params

- useSearchParams hook behaves similar to the use state hook it is stored in the url.
- Search params object to get any value present in the url.

**Example**

Users.js

```javascript
import React from 'react'
import { Outlet, useSearchParams } from 'react-router-dom'

function Users() {
    const [urlparams,setUrlparams] = useSearchParams();
    const isActive = urlparams.get("filter")
    console.log(isActive)
  return (
    <div>
        <h2>User 1</h2>
        <h2>User 2</h2>
        <h2>User 3</h2>
        <Outlet />

        <div>
            <button onClick={() => setUrlparams({filter:"active"})}>Active Users</button>
            <button onClick={() => setUrlparams({})}>Reset Filter</button>   
        </div>
        {isActive === "active" ? "Showing active users" : "Showing all users"}
    </div>
  )
}

export default Users
```

### Relative Links

- Relative paths or relative links don't start with a forward slash and inherit the closest route in which they are rendered.

### Lazy Loading

- Lazy loading is a technique where components not required on the home page can be split into separate code bundles and downloaded only when the user navigates to that page.
- It helps reduce initial load time thereby improving performance.
- Using lazy load we use dynamic imports and react suspense. 
- React lazy function argument contain another function this arugument calls a dynamic import so import.

**Example**

App.js

```javascript
import {Routes,Route} from "react-router-dom"
import Admin from "./Admin";
import Featured from "./Component/Featured";
import Home from "./Component/Home";
import NavBar from "./Component/NavBar";
import New from "./Component/New";
import NoMatch from "./Component/NoMatch";
import Order from "./Component/Order";
import OrderSummary from "./Component/OrderSummary";
import Product from "./Component/Product";
import UserDetails from "./UserDetails";
import Users from "./Users";
import React from 'react'
const LazyAbout =  React.lazy(() => import("./Component/About"))
function App() {

  return (
    <div className="App">
      <NavBar />
      <Order />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="about" element={
        <React.Suspense fallback="Loading...">
        <LazyAbout />
        </React.Suspense>
        } />
        <Route path="product" element={<Product />}>
          <Route index element={<Featured />} />
          <Route path="featured" element={<Featured />} />
          <Route path="new" element={<New />} />
        </Route>
        <Route path="user" element={<Users />}>
        <Route path=":userID" element={<UserDetails />} />
        <Route path="admin" element={<Admin />} />
        </Route>
        <Route path="order-summary" element={<OrderSummary />} />
        <Route path="*" element={<NoMatch />} />
      </Routes>
    </div>
  );
}

export default App;

```
