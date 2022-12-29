# What is useContext hook in React?

The `useContext` hook in React is a way for a functional component to access the context of a parent component, without the need to pass the context down through props at every level of the component tree. This can be particularly useful in cases where you have a deeply nested component structure and you want to avoid prop drilling, which is the process of passing props down through multiple levels of components just to access them in a lower-level component.

To use the `useContext` hook, you first need to create a context object using the `React.createContext` function. This function takes in an optional default value for the context, which will be used if the context has not been set by a parent component. Here's an example of how to create a context object:

```javascript
const MyContext = React.createContext();
```

Next, you'll need to wrap a parent component with the `MyContext.Provider` component, which allows you to pass a value prop to the context object. This value prop will be the context value that will be made available to all child components that are wrapped in the `MyContext.Consumer` component or that use the `useContext` hook. Here's an example of how to use the `MyContext.Provider` component:

```javascript
<MyContext.Provider value={someValue}>
  <MyParentComponent />
</MyContext.Provider>
```

To access the context value in a child component, you can either use the `useContext` hook or wrap the child component with the `MyContext.Consumer` component. Here's an example of how to use the `useContext` hook:

```javascript
import { useContext } from 'react';

function MyChildComponent() {
  const contextValue = useContext(MyContext);
  return <div>{contextValue}</div>;
}
```

Here's an example of how to use the `MyContext.Consumer` component:

```javascript
import { MyContext } from './MyContext';

function MyChildComponent() {
  return (
    <MyContext.Consumer>
      {contextValue => <div>{contextValue}</div>}
    </MyContext.Consumer>
  );
}
```

It's important to note that the `useContext` hook only works with functional components, and it's not possible to use it with class-based components.

In summary, the `useContext` hook is a useful tool in React for allowing functional components to access the context of a parent component without the need for prop drilling. It's a simple and convenient way to share state and data throughout your component tree, and it can help make your code more organized and maintainable.

Thank you for reading! See you again soon.

Please feel free to reach out to me on [**Twitter**](https://twitter.com/BhagyaMudgal).

You can visit my [**Portfolio**](https://www.bhagyamudgal.com/) to check out the projects I have worked on.