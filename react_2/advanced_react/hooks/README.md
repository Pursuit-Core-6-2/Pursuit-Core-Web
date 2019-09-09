# React Hooks

Hooks are a new addition in React 16.8. They let you use state and other React features without writing a class.

Hooks are functions that let you "hook into" React state and lifecycle feature from function components. Hooks let you use React without classes and don't work inside classes.

At the moment the two main hooks are:
- useState
- useEffect

## UseState

`useState` is a hook used in a functional component to add some local state to it. `useState` returns a pair, the current state value and a function that let's you update the state. 

The fonction can be called from an event handler such as `onClick`. It is similar to `this.setState` in a class component but it doesn't merge the old and new state together.

Let's create a counter with `useState`

```js
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```



### More Info
[Introducing Hooks](https://reactjs.org/docs/hooks-intro.html)