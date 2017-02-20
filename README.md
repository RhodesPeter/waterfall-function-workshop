# Morning challenge: implement a waterfall function
This workshop has been inspired by @besarthoxhaj and his legendary waterfall function workshop given to FAC9.

You may have seen the compose function before. It allows you to take some functions and compose them into a single function! What do you do if the functions are asynchronous? Implement the waterfall function. 

The waterfall function takes three arguments:

1) an initial argument, this is passed into the first async function in the waterfall.

2) the second argument is an array of functions, each function takes two arguments. The the first one it uses to find a result, the second is a callback function. These functions will get called one after the other by waterfall.

3) a final callback is the third argument. This is called when waterfall has called the last function.

```
function asyncAddOne(x, cb) {
  setTimeout(function() {
    if (typeof x !== 'number'){ return cb(new Error('need a number!')) }
    else { return cb(null, x + 1) }
  }, 200)
}

function asyncDouble(x, cb) {
  setTimeout(function() {
    if (typeof x !== 'number') { return cb(new Error('need a number!')) }
    else { return cb(null, x * 2) }
  }, 200)
}

function asyncTimesTen(x, cb) {
  setTimeout(function() {
    if (typeof x !== 'number') { return cb(new Error('need a number!')) }
    else { return cb(null, x * 10) }
  }, 200)
}

// Implement this function!
var waterfall = function(arg, tasks, cb) {
  cb(new Error('waterfall function not implemented'))
}

waterfall(3, [
  asyncAddOne,
  asyncDouble,
  asyncTimesTen
], function(error, result) {
  console.log('Test 1');
  if (error) {
    console.log('test failed, ' + error)
  }
  else if (result !== 80) {
    console.log('test failed, expected 3 but got', result)
  }
  else {
    console.log('Test 1 passed!')
  }
})
```
