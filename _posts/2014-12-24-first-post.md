---
layout: post
title: Patterns for dealing with asynchronous functions in Node.js
---
One of the challenges in learning node. js is learning how to deal with asynchronous functions.  One of the interesting problems that a newcomer to node encounters is how to return data from an asynhronous function.  To see what I mean, let's consider an example

Suppose I want to read a file on my hard drive and store the results in a variable. Using normal synchronous functions that we are used to in javascript, this is straightforward.  As an example, let's see what this looks like using a synchronous function in node.js. The code would look like this. 

```javascript
var fs = require('fs');
var countLines = function(text) {
  return text.split('\n').length - 1;
};

var getNumLines = function(filepath, callback) {
  var contents = fs.readFileSync('test.txt');
  var lines = countLines (contents);
  return lines;
};

var fs = require('fs');
var countLines = function(text) {
  return text.split('\n').length - 1;
};
var getNumLines = function(filepath, callback) {
  var lines = 0;
  fs.readFile('test.txt', function(err, buffer){
    if(err) throw err;
    var results = buffer.toString();
    lines = callback(results); 
  });
  return lines;
};

var lines = getNumLines('test.txt', countLines);
```

