Chaining
========

```javascript
function createFunction() {
  var firstName = '';
  var lastName = '';
  var age = 0;
  
  return {
    setFirstName: function(name) {
      firstName = name;
      return this;     // Returning the same host object.
    },
    
    setLastName: function(name) {
      lastName = name;
      return this;
    },
    
    setAge: function(ag) {
      age = ag;
      return this;
    },
    
    toString: function() {
      return [firstName, lastName, age].join(' ');
    }
  }
}

createPerson()
  .setFirstName('Foo')
  .setLastName('Bar')
  .setAge(26)
  .toString()
```
