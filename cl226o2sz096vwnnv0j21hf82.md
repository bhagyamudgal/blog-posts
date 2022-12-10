# How to make Custom Loading Screen in Next.js Project

![Next.js](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/q540t4ekp91jht2hwflk.png)

## Introduction

Next.js is an open-source development framework built on top of Node.js enabling React based web applications functionalities such as server-side rendering and generating static websites.

I was trying to build a custom loading screen for my project in Next.js so I try to google how we can implement it and after hours of searching, I was not able to find a solution that suits my need. There was a solution I came across on the Internet that was using a library called "nprogress" to do so but it does not provide a loading screen that I want to implement so after going through Next.js documentation and this "nprogress" solution, I was able to figure out my solution for the problem. It took me lots of time so I created this blog to help anyone who wants to implement a custom loading screen in Next.js easily in less time.

## Making Custom Loading Screen Component

This part solely depends on you and how you want your loading screen component to look like. For Example below is my Loading component:

```javascript
import React from "react";
import styles from "./Loading.module.css";

function Loading(props) {
  return (
    <div className={props.loading ? styles.body_loading : styles.none}>
      <div
        className={styles.lds_ellipsis}
      >
        <div></div>
        <div></div>
        <div></div>
        <div></div>
      </div>
    </div>
  );
}

export default Loading;
```
Styles (CSS) for the Loading component:

```css
.body_loading {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
.none {
  display: none;
}
.lds_ellipsis {
  display: inline-block;
  position: relative;
  width: 80px;
  height: 80px;
}
.lds_ellipsis div {
  position: absolute;
  top: 33px;
  width: 15px;
  height: 15px;
  border-radius: 50%;
  background: var(--orange);
  animation-timing-function: cubic-bezier(0, 1, 1, 0);
}
.lds_ellipsis div:nth-child(1) {
  left: 8px;
  animation: lds_ellipsis1 0.6s infinite;
}
.lds_ellipsis div:nth-child(2) {
  left: 8px;
  animation: lds_ellipsis2 0.6s infinite;
}
.lds_ellipsis div:nth-child(3) {
  left: 32px;
  animation: lds_ellipsis2 0.6s infinite;
}
.lds_ellipsis div:nth-child(4) {
  left: 56px;
  animation: lds_ellipsis3 0.6s infinite;
}
@keyframes lds_ellipsis1 {
  0% {
    transform: scale(0);
  }
  100% {
    transform: scale(1);
  }
}
@keyframes lds_ellipsis3 {
  0% {
    transform: scale(1);
  }
  100% {
    transform: scale(0);
  }
}
@keyframes lds_ellipsis2 {
  0% {
    transform: translate(0, 0);
  }
  100% {
    transform: translate(24px, 0);
  }
}
```
So you have successfully build your loading screen component with custom styling now its time to render it on web application every time a route changes.

For doing that we will take help of Next.js router events, You can listen to different events happening inside the Next.js Router.

Here's a list of supported events:

```
routeChangeStart(url, { shallow }) - Fires when a route starts to change

routeChangeComplete(url, { shallow }) - Fires when a route changed completely

routeChangeError(err, url, { shallow }) - Fires when there's an error when changing routes, or a route load is cancelled

err.cancelled - Indicates if the navigation was cancelled

beforeHistoryChange(url, { shallow }) - Fires before changing the browser's history

hashChangeStart(url, { shallow }) - Fires when the hash will change but not the page

hashChangeComplete(url, { shallow }) - Fires when the hash has changed but not the page
```
For more details about these events and other router methods you can visit [Next.js official documentation](https://nextjs.org/docs/api-reference/next/router)

By help of these events you can add your loading screen component to app.js see how:

First import `{useState, useEffect}` from `"react"`, `{useRouter}` from `"next/router"` and your `Loading` component.

```javascript
import { useState, useEffect } from "react";
import { useRouter } from "next/router";
import Loading from "../components/Loading";
```

Now we will declare `loading` variable using `useState` hook and initialize it with `false` and we will set it to `true` when route changes and revert it back to false once route change completes.

We will put that logic inside `useEffect` hook and set `router` as its dependency. It means everytime `router` changes logic inside `useEffect` hook will get executed.

```javascript
function MyApp({ Component, pageProps }) {
const router = useRouter();
const [loading, setLoading] = useState(false);

useEffect(() => {
    const handleStart = (url) => {
      url !== router.pathname ? setLoading(true) : setLoading(false);
    };
    const handleComplete = (url) => setLoading(false);

    router.events.on("routeChangeStart", handleStart);
    router.events.on("routeChangeComplete", handleComplete);
    router.events.on("routeChangeError", handleComplete);
  }, [router]);

  return (
    <>
          <Loading loading={loading} />  
          <Component {...pageProps} />
    </>
  );
}

export default MyApp;
}
```
We will pass `loading` variable as a prop to our `Loading` component so that whenever `loading` is `true` `Loading` component will have `class` having `display: block` and when it is `false` it will have `class` having `display: none`.

## Conclusion

This is how you can make a custom loading screen in Next.js. I hope this blog help you and save your time and efforts.

Thank you for reading! See you again soon.

Feel free to connect with me on [LinkedIn](https://bit.ly/3AgR0MT).

You can follow me on [Instagram](https://bit.ly/2YZxZRq).

To know more about me and my projects visit my [Portfolio](https://bit.ly/3zOlSUS).

If you enjoyed this post, you can support me and [Buy Me A Coffee](https://bit.ly/3nyg52d). It encourages me to write more informational and useful content in the future.  

Any doubt, put that below. 


 

