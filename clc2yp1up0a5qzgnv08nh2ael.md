# What is useEffect hook in React?

The `useEffect` hook is a powerful feature in React that allows you to perform side effects in functional components. Side effects are actions that are not related to the rendering of the component, such as making an HTTP request or setting up a subscription.

Prior to the introduction of hooks, side effects could only be performed in class-based components through lifecycle methods like `componentDidMount` and `componentDidUpdate`. With the `useEffect` hook, you can perform side effects in functional components and have more control over when they are executed.

Here's an example of how to use the `useEffect` hook in a functional component:

```javascript
import { useEffect } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  // Use the useEffect hook to perform a side effect
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

In this example, we're using the `useEffect` hook to update the document title every time the `count` state variable changes. The `useEffect` hook takes a function as an argument, which is the side effect that we want to perform.

The `useEffect` hook will execute the side effect function every time the component re-renders, which includes the initial render. If you only want the side effect to be executed on certain conditions, you can pass an array of dependencies as a second argument to the `useEffect` hook. The side effect will only be executed if one of the dependencies has changed.

For example, we can update the previous example to only update the document title when the `count` variable is even:

```javascript
useEffect(() => {
  document.title = `You clicked ${count} times`;
}, [count]);
```

In this case, the side effect function will only be executed if the `count` variable changes.

The `useEffect` hook is a very useful tool for performing side effects in functional components, and it's a powerful addition to the React library. I hope this helps clarify what the `useEffect` hook is and how it can be used in React!

Thank you for reading! See you again soon.

Please feel free to reach out to me on [**Twitter**](https://twitter.com/BhagyaMudgal).

You can visit my [**Portfolio**](https://www.bhagyamudgal.com/) to check out the projects I have worked on.