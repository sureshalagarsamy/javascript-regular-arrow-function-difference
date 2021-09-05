### Difference between Regular functions and Arrow functions

Differences below:

* Syntax
* Arguments binding
* Use of `this` keyword
* Using a `new` Keyword

#### Syntax

```js
// Regular Function
var myFunction = function() { console.log('SURESH') }

// Arrow function ES6
let myFunction = () => { console.log('SURESH'); }
```

#### Arguments binding

```js
// Regular Function
let myObject = {
   showArg: function() {
        console.log(arguments);
   }
}
myObject.showArg(1,2,3)  // {0:1,1:2,2:3}

// Arrow Function
let myObject = {
   showArg: () => {
        console.log(arguments);
   }
}
myObject.showArg(1,2,3) // arguments is not defined

// You can easily access the arguments by using rest parameter ...args
let myObject = {
   showArg: (...args) => {
        console.log(args);
   }
}
myObject.showArg(1,2,3) // {0:1,1:2,2:3}
```

#### Use of `this` keyword

```js
let name = {
    fullName: 'suresh',
    regular: function() {
        console.log(`my name is ${this.fullName}`);
    },
    arrow: () => {
        console.log(`my name is ${this.fullName}`);
    }
}
name.regular(); // my name is suresh
name.arrow(); // my name is undefined
```

No matter how or where being executed, `this` value inside of an arrow function always equals `this` value from the outer function.

```js
let myObject = {
    myMethod: function(param) {
        console.log(this); // logs myObject 
        const callback = () => {
            console.log(this); // this takes value from myMethod(outer func)
        }
        param.forEach(callback);
    }
}
myObject.myMethod([1,2,3]);
```

### Use of `new` Keyword

```js
// regular Function
function car(color) {
    this.color = color
}
let myCar = new car('Red');
console.log(myCar instanceof car);

// Arrow Function
let car = (color) => {
    this.color = color;
}
let myCar = new car('red'); // Uncaught TypeError: car is not a constructor
```
