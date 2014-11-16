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

```javascript
var str = "name,age,hair\nMerble,35,red\nBob,64,blonde";

// function bridges the gap between the two worlds of data types.
// function which bridges the gap between the two worlds i.e. strings and arrays.
function lameCSV(str) {
  return _.reduce(str.split("\n"), function(table, row) {
    table.push(_.map(row.split(","), function(item) { return item.trim(); }));
    return table;
  }, []);
}

function second(array) {
  return array.slice(1,2)[0];
}

// selector function
function selectNames(table) {
  return _.rest(_.map(table, _.first));
}

// selector function
function selectAges(table) {
  return _.rest(_.map(table, second));
}

console.log(lameCSV(str));
console.log(selectNames(lameCSV(str)));
console.log(selectAges(lameCSV(str)));
```

On Speed
========

Sometimes functional calls are expensive as compared to the raw code. But due to the optimization compilers like v8 egine many statical checks are done (**inline functions** and **dead code elimination**).

Summary
=======

1. Identify an abstraction and build a function for it.
2. Use existing function / abstraction to build more complex abstractions.
3. Passing existing functions to other functions to build even more complex abstractions.
