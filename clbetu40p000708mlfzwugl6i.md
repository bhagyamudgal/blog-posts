# What is Cross-Origin Resource Sharing (CORS)

CORS is a critical security feature in web development that controls how different web applications can access resources from other origins. Without CORS, a web page from one origin would be unable to access resources from another origin, even if the resources are publicly available.

CORS works by adding HTTP headers to server responses that specify which origins are allowed to access the resources. The browser then checks these headers and only allows the request to proceed if the origin is allowed.

For example, if a web page from `https://example.com` tries to access a resource from `https://api.example.com`, the server at `https://api.example.com` would need to include the following header in its response:


```javascript
Access-Control-Allow-Origin: https://example.com
``` 

This tells the browser that the web page can access the resource at `https://example.com`. If the server does not include this header, the browser will block the request, and the web page will not be able to access the resource.

CORS is a critical security feature that helps to prevent cross-site scripting (XSS) attacks. It allows web developers to specify which origins are allowed to access their resources, which helps to prevent unauthorized access and potential security vulnerabilities.

Thank you for reading! See you again soon.

Please feel free to reach out to me on [Twitter](https://twitter.com/BhagyaMudgal).

You can visit my [Portfolio](https://www.bhagyamudgal.com) to check out the projects I have worked on.


