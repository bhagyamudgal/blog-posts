# What is useState hook in React?

The `useState` hook is a powerful feature in React that allows you to add state to functional components. Prior to the introduction of hooks, states could only be managed in class-based components. With the `useState` hook, you can add state to functional components and manage it just like you would in a class-based component.

Here's an example of how to use the `useState` hook in a functional component:

```javascript
import { useState } from 'react';

function CounterExample() {
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

In this example, we're using the `useState` hook to create a new state variable called `count`. The `useState` hook takes a single argument, which is the initial value for the state variable. In this case, we're setting the initial value to `0`.

The `useState` hook returns an array with two elements. The first element is the current value of the state variable (in this case, `count`), and the second element is a function that allows us to update the value of the state variable (in this case, `setCount`).

We can use the `setCount` function to update the value of the `count` state variable by calling it and passing in the new value. In the example above, we're using an arrow function to increment the `count` variable by one every time the button is clicked.

The `useState` hook is a very useful tool for managing state in functional components, and it's a powerful addition to the React library. I hope this helps clarify what the `useState` hook is and how it can be used in React!

Thank you for reading! See you again soon.

Please feel free to reach out to me on [**Twitter**](https://twitter.com/BhagyaMudgal).

You can visit my [**Portfolio**](https://www.bhagyamudgal.com/) to check out the projects I have worked on.