| Keyword                                                                                       | Scope          | Hoisting | Can Be Reassigned | Can Be Redeclared |
| --------------------------------------------------------------------------------------------- | -------------- | -------- | ----------------- | ----------------- |
| [`var`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)     | Function scope | Yes      | Yes               | Yes               |
| [`let`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)     | Block scope    | No       | Yes               | No                |
| [`const`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const) | Block scope    | No       | No                | No                |


## Constant Declaration

ES6 introduced the `const` keyword, which _cannot_ be redeclared or reassigned, but _is_ mutable.

```js
// ES6
const CONST_IDENTIFIER = 0;  // constants are uppercase by convention
```


## Arrow Functions

The arrow function expression syntax is a shorter way of creating a function expression. Arrow functions do not have their own `this`, do not have prototypes, cannot be used for constructors, and should not be used as object methods.

```js
// ES5
function func(a, b, c) {...};  // function declaration
var func = function(a, b, c) {...};  // function expression
```

```js
// ES6
let func = a => {...};  // parentheses optional with one parameter
let func = (a, b, c) => {...};  // parentheses required with multiple parameters
```


## Concatenation/String Interpolation

Expressions can be embedded in template literal strings.

```js
//ES5
var str = 'Release date: ' + date;
```

```js
//ES6
let str = `Release Date: ${date}`;
```


## Multi-line Strings

Using template literal syntax, a JavaScript string can span multiple lines without the need for concatenation.

```js
//ES5
var str = 'This text ' + 'is on ' + 'multiple lines';
```

```js
//ES6
let str = `This text
            is on
            multiple lines`;
```

**Note:** Whitespace is preserved in multi-line template literals.


## Implicit Returns

The `return` keyword is implied and can be omitted if using arrow functions without a block body.

```js
//ES5
function func(a, b, c) {
  return a + b + c;
}
```

```js
//ES6
let func = (a, b, c) => a + b + c;  // curly brackets must be omitted
```


## Key/Property Shorthand

ES6 introduces a shorter notation for assigning properties to variables of the same name.

```js
//ES5
var obj = {
  a: a,
  b: b,
};
```

```js
//ES6
let obj = {
  a,
  b,
};
```


## Method Definition Shorthand

The `function` keyword can be omitted when assigning methods on an object.

```js
// ES5
var obj = {
  a: function(c, d) {...},
  b: function(e, f) {...},
};
```

```js
// ES6
let obj = {
  a(c, d) {...},
  b(e, f) {...},
};
```

Calling method `a()`
```js
obj.a();  // call method a
```


## Destructuring (object matching)

Use curly brackets to assign properties of an object to their own variable.

```js
var obj = { a: 1, b: 2, c: 3 };
```

```js
//ES5
var a = obj.a;
var b = obj.b;
var c = obj.c;
```

```js
//ES6
let { a, b, c } = obj;
```


## Array iteration (looping)

A more concise syntax has been introduced for iteration through arrays and other iterable objects.

```js
var arr = ['a', 'b', 'c'];
```

```js
//ES5
for (var i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
```

```js
//ES6
for (let i of arr) {
  console.log(i);
}
```


## Default parameters

Functions can be initialized with default parameters, which will be used only if an argument is not invoked through the function.

```js
//ES5
var func = function(a, b) {
  b = b === undefined ? 2 : b;
  return a + b;
}
```

```js
//ES6
let func = (a, b = 2) => {
  return a + b;
}
```

```js
func(10);  // returns 12
func(10, 5);  // returns 15
```


## Spread syntax

Spread syntax can be used to expand an array.

```js
//ES5
let arr1 = [1, 2, 3];
let arr2 = ['a', 'b', 'c'];
let arr3 = [...arr1, ...arr2];

console.log(arr3) // [1, 2, 3, "a", "b", "c"];
```

Spread syntax can be used for function arguments.

```js
//ES6
let arr1 = [1, 2, 3];
let func = (a, b, c) => a + b + c;

console.log(func(...arr1));  // 6
```


## Classes/constructor functions

ES6 introducess the `class` syntax on top of the prototype-based constructor function.


```js
//ES5
function Func(a, b) {
  this.a = a;
  this.b = b;
}

Func.prototype.getSum = function() {
  return this.a + this.b;
}

var x = new Func(3, 4);
```

```js
//ES6
class Func {
  constructor(a, b) {
    this.a = a;
    this.b = b;
  }

  getSum() {
    return this.a + this.b;
  }
}

let x = new Func(3, 4);
```

```js
x.getSum();  // returns 7
```


## Inheritance

The `extends` keyword creates a subclass.

```js
//ES5
function Inheritance(a, b, c) {
  Func.call(this, a, b);

  this.c = c;
}

Inheritance.prototype = Object.create(Func.prototype)
Inheritance.prototype.getProduct = function() {
  return this.a * this.b * this.c;
}

var y = new Inheritance(3, 4, 5);
```

```js
//ES6
class Inheritance extends Func {
  constructor(a, b, c) {
    super(a, b);

    this.c = c;
  }

  getProduct() {
    return this.a * this.b * this.c;
  }
}

let y = new Inheritance(3, 4, 5);
```

```js
y.getProduct();  // 60
```


## Modules - export/import

Modules can be created to export and import code between files.

<div class="filename">index.html</div>

```html
<script src="export.js"></script>
<script type="module" src="import.js"></script>
```

export.js

```js
let func = a => a + a;
let obj = {...};
let x = 0;

export { func, obj, x }
```

<div class="filename">import.js</div>

```js
import { func, obj, x } from './export.js'

console.log(func(3), obj, x);
```


## Promises/Callbacks

Promises represent the completion of an asynchronous function. They can be used as an alternative to chaining functions.

<div class="filename">ES5 callback</div>

```js
function doSecond() {
  console.log('Do second.');
}

function doFirst(callback) {
  setTimeout(function() {
    console.log('Do first.');

    callback();
  }, 500)
}

doFirst(doSecond);
```

<div class="filename">ES6 Promise</div>

```js
let doSecond = () => {
  console.log('Do second.');
};

let doFirst = new Promise((resolve, reject) => {
  setTimeout(() => {
    console.log('Do first.');

    resolve();
  }, 500)
});

doFirst.then(doSecond)
```

An example below using `XMLHttpRequest`, for demonstrative purposes only (Fetch API would be the proper modern API to use).

<div class="filename">ES5 callback</div>

```js
function makeRequest(method, url, callback) {
  var request = new XMLHttpRequest();

  request.open(method, url);
  request.onload = function() {
    callback(null, request.response)
  };
  request.onerror = function() {
    callback(request.response)
  };
  request.send();
}

makeRequest('GET', 'https://url.json', function(err, data) {
  if (err) {
    throw new Error(err);
  } else {
    console.log(data);
  }
})
```

<div class="filename">ES6 Promise</div>

```js
function makeRequest(method, url) {
  return new Promise((resolve, reject) => {
    let request = new XMLHttpRequest();

    request.open(method, url);
    request.onload = resolve;
    request.onerror = reject;
    request.send();
  })
}

makeRequest('GET', 'https://url.json')
  .then(event => {
    console.log(event.target.response);
  })
  .catch(err => {
    throw new Error(err);
  })
```
