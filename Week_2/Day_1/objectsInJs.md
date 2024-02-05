# Primitive Types
* JavaScript has 7 primitive types:
  * Boolean
  * Null
  * Undefined
  * Number
  * BigInt
  * String
  * Symbol

``` Javascript
const bool = false;
const nul = null;
const undef = undefined;
const num = 5;
const bigint = 9007199254740991n;
const str = 'This is a string';
const sym = Symbol('symbol'); 
```

* Primitive types are immutable; this means that they cannot be modified after they are created

``` Javascript
const myString = 'hello world';
const secondString = myString.replace('hello', 'goodbye'); // doesn't change myString
console.log(myString); // 'hello world' 
```

# Objects!
* Objects are data structures that allow us to store related data and functionality together
* Objects are made up of key/value pairs
* The key in an object is always a string
* The value can be any valid JavaScript value (primitive, array, object, or function)
* In arrays, you use the index to access a value:

``` Javascript
const arr = [1, 2, 3];
console.log(arr[1]); // 2
```

* With objects, you use the key to access the value:

``` Javascript
const myObj = {
  firstName: 'Lorem',
  lastName: 'Ipsum'
};

// we have two options for accessing values
// dot syntax
console.log(myObj.firstName); // Lorem

// square bracket syntax
console.log(myObj['lastName']); // Ipsum
```

* If you know the name of the property, use dot notation
* If the name of the property is dynamic (eg. stored in a variable), use square bracket syntax
# Passing Values to Functions
* Primitive types are passed to functions by value. This means that a copy is made and used by the function. The original value is unchanged.

``` Javascript
const name = 'Murray';
const changeName = function (name) {
  name = 'Jane';
  console.log(name); // Jane
};

changeName(name);
console.log(name); // Murray
```

* Objects are passed to functions by reference. This means that the internal values of the object can be changed by the function, but the object itself cannot be reassigned.

``` Javascript
const myObj = {
  firstName: 'Lorem',
  lastName: 'Ipsum'
};

const changeKey = function (obj) {
  obj.firstName = 'Jane'; // this does change the value of the firstName key
}

changeKey(myObj);
console.log(myObj.firstName); // Jane

const replaceObj = function (obj) {
  obj = {}; // this won't work
}

replaceObj(myObj);
console.log(myObj); // { firstName: 'Jane', lastName: 'Ipsum' }
```

# Functions Inside Objects
* Since objects are key/value pairs, and functions are values, we can store functions inside of an object

``` Javascript
const myObj = {
  firstName: 'Lorem',
  sayHello: function () {
    console.log('hello');
  }
};

myObj.sayHello(); // hello
console.log(myObj); // { firstName: 'Lorem', sayHello: [Function: sayHello] }
```

* We can make reference to the other properties in an object by using this to refer to the object itself

``` Javascript
const myObj = {
  firstName: 'Lorem',
  lastName: 'Ipsum',
  sayFullName: function () {
    console.log(`My full name is ${this.firstName} ${this.lastName}`);
  }
};

myObj.sayFullName(); // My full name is Lorem Ipsum
```

* A function inside an object is often referred to as a method
* Object iteration with for..in
* JavaScript gives us an easy way to iterate through an object's keys: the for..in loop
* NOTE: We cannot use for..of to iterate through an object; it will result in an error

``` Javascript
const obj = { a: 1, b: 2, c: 3 };

for (const key in obj) {
  // we can use the key to access the value
  const value = obj[key];
}
```

# Useful Links
* [MDN: Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)
* [Dot Notation vs Square Brackets](https://codeburst.io/javascript-quickie-dot-notation-vs-bracket-notation-333641c0f781)
* [Python Tutor](https://pythontutor.com/javascript.html#mode=edit)

# Credits
Above readme.md Notes are adapted from Andy Lindsay (LHL Instructor) and previous LHL instruction material