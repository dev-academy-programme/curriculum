# A very brief cross-origin survival guide

When you are first getting to grips with APIs, you may strike errors related to CORS, or which might have mentioned "cross-origin" or told you localhost wasn't allowed to make that request. This would have happened in particular if you're writing an assignment that makes a request to an API without using one of the online editors like [CodePen](https://codepen.io), [JSBin](https://jsbin.com) or [JSFiddle](https://jsfiddle.net).

The main problem is this: most modern web sites don't like it when you use JavaScript to make requests from _outside_ that site, because it's a security risk. You can read more about it at [Same-origin policy](https://en.wikipedia.org/wiki/Same-origin_policy) if you're curious. A web API is a service that specifically allows requests from outside its own domain, but often has other security measures like requiring accounts or tokens.

However, the _browsers_ that we tend to use to detect JavaScript also have features which disallow cross-origin requests, say from your own computer ('localhost') to a quote site ('theysaidso.com'). So you'll get an error if you try to run them locally using only the browser. There's a way to get around it using a local web server which you'll learn at bootcamp, but for now using online services like CodePen or using a CORS proxy service like [crossorigin.me](https://crossorigin.me) is easier.


# Resources

 - https://crossorigin.me
