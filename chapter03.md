Variable Scope and Closures
===========================

Binding: Act of assgning a value to a name in javascript via:
  * var assignment
  * function arguments
  * this passing and
  * property assignment


The extent of a scope refers to the lifetime of a variable (i.e. how long a variable hold a certain value).

Global scope: The variable with the longest lifespan-that of the life of the program itself.

Lexical scope: Closest **texual** binding to its use.

```javascript
aVar = "outer";

function aFun() {
  var aVar = "middle";
  
  return _.map([1,2,3], function(val) {
    var aVar = "In";
    
    return [aVar, val].join(' ');
  });
}

aFun();
//=> ["In 1", "In 2", "In 2"]
```

Dynamic scope: Consists of global lookup table of named values. Implemented by stacks.
```javascript
stackBinder('a', 1);
stackBinder('b', 100);

dynamicLookup('a');
//=> 1
globals;
//=> {'a': [1], 'b': [100]}

stackBinder('a', *);
dynamicLookup('a');
//=> *
globals;
//=> {'a': [1, '*'], 'b': [100]}
stackUnbinder('a');
dynamicLookup('a');
//=> 1
```

Javascript's Dynamic Scope: The `this` reference, it can point to different values depending on the context in which it was created. The value of `this` can be directly manipulated by `apply` and `call`.
```javascript
function globalThis() { return this; }

globalThis();
//=> some global object, probably window

globalThis.call('foo');
//=> 'foo'
globalThis.call('bar', []);
//=> 'bar'
```

Summary
=======
