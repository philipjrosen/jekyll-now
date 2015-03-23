---
layout: post
title: Returning Data From Asynchronous Functions In Node.js
---

One of the challenges in learning Node.js is learning how to deal with asynchronous functions.  One of the interesting problems that a newcomer to Node encounters is how to return data from an asynhronous function.  To see what I mean, let's consider an example

```javascript
var fs = require('fs');
var countLines = function(text) {
  return text.split('\n').length - 1;
};
```
