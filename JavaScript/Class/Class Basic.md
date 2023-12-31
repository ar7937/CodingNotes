# Class
+ a class is a kind of function <br/>
<pre>
  class MyClass {
  // class methods
  constructor() { ... }
  method1() { ... }
  method2() { ... }
  method3() { ... }
  ...
}
ex:-
class User {
  constructor(name) {
    this.name = name;
  }
  sayHi() {
    alert(this.name);
  }
}
// Usage:
let user = new User("John");
user.sayHi();
When new User("John") is called:
A new object is created.
The constructor runs with the given argument and assigns it to this.name
</pre>
alert(typeof User); // function 
+ C reates a function named User, that becomes the result of the class declaration. The function code is taken from the constructor method (assumed empty if we don’t write such method).<br/>
+ Stores class methods, such as sayHi, in User.prototype<br/>
<pre>
  class User {
  constructor(name) { this.name = name; }
  sayHi() { alert(this.name); }
}

// class is a function
alert(typeof User); // function

// ...or, more precisely, the constructor method
alert(User === User.prototype.constructor); // true

// The methods are in User.prototype, e.g:
alert(User.prototype.sayHi); // the code of the sayHi method

// there are exactly two methods in the prototype
alert(Object.getOwnPropertyNames(User.prototype)); // constructor, sayHi
</pre>
 ## important differences between class and function 
 + First, a function created by class is labelled by a special internal property [[IsClassConstructor]]: true. So it’s not entirely the same as creating it manually.<br/>
 + Class methods are non-enumerable. A class definition sets enumerable flag to false for all methods in the "prototype".
 + Classes always use strict. All code inside the class construct is automatically in strict mode.
 ## Getters/setters
 <pre>
   class User {
  constructor(name) {
    // invokes the setter
    this.name = name;
  }
  get name() {
    return this._name;
  }
  set name(value) {
    if (value.length < 4) {
      alert("Name is too short.");
      return;
    }
    this._name = value;
  }

}
let user = new User("John");
alert(user.name); // John
user = new User("");
 </pre>
