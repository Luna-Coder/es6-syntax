# es6-syntax

| Keyword                                                                                       | Scope          | Hoisting | Can Be Reassigned | Can Be Redeclared |
| --------------------------------------------------------------------------------------------- | -------------- | -------- | ----------------- | ----------------- |
| [`var`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)     | Function scope | Yes      | Yes               | Yes               |
| [`let`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)     | Block scope    | No       | Yes               | No                |
| [`const`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const) | Block scope    | No       | No                | No                |

## Constant declaration

ES6 introduced the `const` keyword, which _cannot_ be redeclared or reassigned, but _is_ mutable.

```js
// ES6
const CONST_IDENTIFIER = 0;  // constants are uppercase by convention
```
## Arrow functions

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

## Method Definition Shorthand

The `function` keyword can be omitted when assigning methods on an object.

ES5
```js
var obj = {
  a: function(c, d) {...},
  b: function(e, f) {...},
}
```

ES6
```js
let obj = {
  a(c, d) {...},
  b(e, f) {...},
}
```

Calling method `a()`
```js
obj.a();  // call method a
```
