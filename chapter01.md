Functions as unit of abstraction
================================

```javascript
function parseAge(age) {
  if(!_.isString(age)) { throw new Error("Expecting a string")}
  var a;
  
  a = parseInt(age, 10);
  
  if(_.isNan(a)) {
    console.log(["could not parse age: ", age].join(' '));
    a = 0;
  }
  
  return a;
}
```
Becomes

```javascript
function fail(error) {
  throw new Error(error)
}

function warn(warning) {
  console.log(["Warning: ", warning].join(' '));
}

function note(note) {
  console.log(["Note: ", note].join(' '));
}

function parseAge(age) {
  if (!_.isString(age)) fail("Expecting a string");
  var a;
  
  a = parseInt(age, 10);
  
  if(_.isNan(a)) {
    warn(["could not parse age: ", age].join(' '));
    a = 0;
  }
  return a;
}
```

Functions as Units of Behavior
==============================

Data as Abstraction
===================

On Speed
========

Sometimes functional calls are expensive as compared to the raw code. But due to the optimization compilers like v8 egine many statical checks are done (**inline functions** and **dead code elimination**).

Summary
=======

1. Identify an abstraction and build a function for it.
2. Use existing function / abstraction to build more complex abstractions.
3. Passing existing functions to other functions to build even more complex abstractions.
