# Morning challenge: implement a waterfall function
This workshop has been inspired by [Besart Hoxhaj](https://github.com/besarthoxhaj) and his legendary waterfall function workshop given to FAC9.

You may have seen the compose function before, it allows you to take some functions and compose them into a single function! 

What do you do if the functions are asynchronous? You implement the waterfall function. 

Like the compose function, the waterfall runs an array of functions in series, each passing their result to the next function in the array. Crucially, the waterfall function will not invoke the next function in the array until it has completed its own computation. 

The waterfall function takes three arguments:

1) an initial argument, this is passed into the first async function in the waterfall.

2) the second argument is an array of functions, each function takes two arguments. The the first one it uses to find a result, the second is a callback function. These functions will get called one after the other by waterfall.

3) a final callback is the third argument. This is called when waterfall has called the last function.

### Workshop: 

1) Copy the code below and paste it into [Repl](https://repl.it/languages/javascript).

2) Create the waterfall function to pass the test. 

3) For bonus points, create some additional tests for the waterfall function.

```
function asyncAddOne(x, cb) {
  setTimeout(function() {
    if (typeof x !== 'number'){ return cb(new Error('need a number!')) }
    else { return cb(null, x + 1) }
  }, 200);
}

function asyncDouble(x, cb) {
  setTimeout(function() {
    if (typeof x !== 'number') { return cb(new Error('need a number!')) }
    else { return cb(null, x * 2) }
  }, 200);
}

function asyncTimesTen(x, cb) {
  setTimeout(function() {
    if (typeof x !== 'number') { return cb(new Error('need a number!')) }
    else { return cb(null, x * 10) }
  }, 200);
}

// Implement this function!
function waterfall(arg, tasks, cb) {
  cb(new Error('waterfall function not implemented'));
}

waterfall(3, [
  asyncAddOne,
  asyncDouble,
  asyncTimesTen
], function(error, result) {
     console.log('Test 1');
     if (error) {
       console.log('test failed, ' + error);
     }
     else if (result !== 80) {
       console.log('test failed, expected 80 but got', result);
     }
     else {
       console.log('Test 1 passed!');
     }
});
```

### Glossary:
- [Error-first callbacks](http://fredkschott.com/post/2014/03/understanding-error-first-callbacks-in-node-js/)
- [Compose function](http://blakeembrey.com/articles/2014/01/compose-functions-javascript/)
- [Synchronous vs. Asynchronous](http://rowanmanning.com/posts/javascript-for-beginners-async/)
