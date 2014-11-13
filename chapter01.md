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
