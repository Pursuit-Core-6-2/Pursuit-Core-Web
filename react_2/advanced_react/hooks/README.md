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

The only argument to `useState` is the initial state. In the example above, it is 0 because our counter starts from zero. Unlike `this.state`, the state here doesn’t have to be an object — although it can be if you want. The initial state argument is only used during the first render.

## useEffect

The Effect hook `useEffect` adds the ability to add side effects from a function component.

Examples of side effects are data fetching or susbscription.

`useEffect` replaces `componentDidMount`, `componentDidUpdate`, `componentWillMount` in React classes.

```js
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  // Similar to componentDidMount and componentDidUpdate:
  useEffect(() => {
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
  });

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

Effects are declared inside the component so they have access to its props and state. By default, React runs the effect after each render - including the first one. 

In some cases, cleaning up or applying the effect after every render might create a performance problem. In class components, we can solve this by writing an extra comparison with prevProps or prevState inside componentDidUpdate:

```js
componentDidUpdate(prevProps, prevState) {
  if (prevState.count !== this.state.count) {
    document.title = `You clicked ${this.state.count} times`;
  }
}
```

This requirement is common enough that it is built into the `useEffect` Hook API. You can tell React to skip applying an effect if certain values haven’t changed between re-renders. To do so, pass an array as an optional second argument to useEffect. 

```js
useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, []);
```


### More Info
If you want to know why React introduced hooks, [this article](https://reactjs.org/docs/hooks-intro.html) from the official website might be interesting.

A great (but long) article from Dan Abramov, [How Are Function Components Different from Classes?](https://overreacted.io/how-are-function-components-different-from-classes/)

A great crash test that refactors existing class component into functional component with hooks: [React.js Hooks Crash Course](https://www.youtube.com/watch?v=-MlNBTSg_Ww&t=380s)

[5 Ways to Convert React Class Components to Functional Components w/ React Hooks](https://scotch.io/tutorials/5-ways-to-convert-react-class-components-to-functional-components-w-react-hooks/)

