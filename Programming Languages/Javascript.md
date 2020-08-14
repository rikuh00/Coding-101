# Javascript
## 1. Introduction

* Hello World
```js
alert('Hello World!');
```

* Comments
```js
// Single-Line Comment

/* Multi-Line
    Comment */
```

## 2. Variables
* Declaration and assignment
    ```js
    let message;
    message = 'Hello'
    alert(message); //prints Hello
    ```
* Constants
    ```js
    const pageLoadTime = 35 //calculated constant
    const COLOR_RED = '#F00' //constant known before loading
    ```

## 3. Primitive Data Types
* Variables are not bound to a data type (unlike Java or C)

### Number
* Represents integers and floats
* Special numeric values
    * `Infinity` and `-Infinity`
        ``` js
        alert(1/0); //Infinity
        alert(-Infinity); //-Infinity
        ```
    * `NaN` represents a computational error
        ``` js
        alert('Hello'/2); //NaN
        ```
* Doing impossible operations (e.g. division by zero) will never "kill" the program
    * The program will return NaN at worst
* Numeric conversion happens automatically unless it looks like a string concat
    ``` js
    alert('2' * '3'); //6
    ```
    * Manual conversion: `Number(x)`

### BigInt
* Used for large integers (<code>|x| > 2<sup>53</sup>-1</code>)
* Appending `n` at the end of the integer indicates BigInt type
    ``` js
    const bigInt = 1234567890123456789012345678901234567890n;
    ```

### String
* Simple quotes
    ``` js
    let str = 'Hello';
    let str2 = "Hello";
    ```
* Backticks allows for embedded variables/expressions
    ``` js
    let name = 'John';
    alert(`Hello ${name}!`); //Hello John!
    alert(`1 + 2 = ${1+2}`) //1+2=3
    ```
* There is no `char` type in JavaScript
* Converting to string: `String(x)`
* "Forcing" numbers into string form: `'+num'`
    * e.g. '+49' remains as text instead of being converted to a number

### Boolean
* `true` or `false`
* Converting to boolean: `Boolean(x)`
    * 0, `null`, `undefined`, and `NaN` return `false`
    * Other values return `true`

### Null and Undefined
* `null` represents "value unknown"
    * Does not represent "null pointer"
    ``` js
    let age = null;
    ```
* `undefined` represents "value unassigned"
    ``` js
    let age;
    alert(age); //"undefined"
    ```
* `undefined` is reserved as the default initial value
    ``` js
    let age = undefined; //bad practice
    let age = null; //good practice
    ```

### Object and Symbol
* `object`: used for objects and `null` (for backward compatibility)
* `symbol`: used to create unique identifiers for objects
    ``` js
    let id = Symbol('Hello')
    ```

### `typeof` Operator
* Syntax: `typeof x` (operator) or `typeof(x)` (function)
    * Operator and function work the same way
* Returns a string with the type name
    ``` js
    typeof 0; //number
    typeof 10n; //bigInt
    typeof null; //object - error in JS (not actually an object)
    typeof alert; //function
    ```

## 4. Browser Interactions
### `alert`
* Shows a message and waits for the user to press "OK"
    ```js
    alert('Hello World!');
    ```

### `prompt`
* Prompts the user to type in a value
* Syntax: `result = prompt(title, [default])`
    * `result`: user input (string)
    * `title`: prompt text (string)
    * `default`: default value for result if nothing is supplied (string, number, etc.)

### `confirm`
* Shows a window with a question and OK/Cancel buttons
* Syntax: `result = confirm(question)`
    * `result`: true for OK, false for Cancel (boolean)
    * `question`: prompt text (string)

## 5. Basic Operators
### Maths
* Basic operation
    * Addition: `+`
    * Subtraction: `-`
    * Multiplication: `*`
    * Division: `/`
    * Remainder: `%`
    * Exponentiation: `**`
* Modifying in place: `+=` etc. are supported
* Increments
    * `x++` \ `x--` increases\decreases 'x' by 1 and returns the old value
    * `++x` \ `--x` increases\decreases 'x' by 1 and returns the new value

### String Concat
``` js
let s = 'my' + 'string'; //s = mystring
```
* Concatenating numbers and strings
    ``` js
    alert('1' + 2); //12 (not 3)
    alert(2 + 2 + '1'); //41 (not 221) - calculates 2+2 first
    ```
* String multiplication is not supported (returns `NaN`)

## 6. Comparisons and Logical Operators
* Generally works the same way as other languages
* Strict equality check: checks for equality without automatic type conversion
    * Syntax: `x === y`
    * e.g. `0 === false` returns `false` because types are different
* Logical operators
    * Or: `||`
    * And: `&&`
    * Not: `!`
* Nullish coalescing finds the first defined value
    * Syntax: ` x = (val1 ?? val2 ?? ... ?? valn)`
    * Returns the first value that is defined 

## 7. Conditional Processing
* If statement
    ```js
    if (condition) {
        //code if true;
        //[code if false];
    }

    else if (condition2) {
        //code if true;
    }

    else {
        //code if false;
    }
    ```

* Single-line if statement
    ```js
    if (condition) /*code if true*/ else /*code if false*/;
    ```

* Conditional operator
    ```js
    let x = (condition1) ? value_if_true :
        (condition2) ? value_if_true :
        value_if_false;
    alert(x); //value depending on the condition
    ```

* Switch statement
    ```js
    switch(x) {
        case val1: //if x == val1
            //code
            break;

        case val2:
            //code
            break;

        case val3:
        case val4:
            //code (for both val3 and val4)
            break;
        default:
            //code
            break;
    }
    ```
    * Equality check is always strict(`===`) for switch cases

## 8. Loops
### While Loop
* While loop
    ```js
    while (condition) {
        //code
    }
    ```
* Do while loop
    ```js
    do {
        //code
    } while (condition);
    ```
### For Loop
```js
for (begin; condition; step) {
    //code
}
```
* Example
    ```js
    for (let i = 0; i < 3; i++) {
        alert(i);
    } //runs 3 times
    ```
## 9. Functions
### Function Declaration
```js
function name([parameters]) {
    //code
    return [val];
} 
```
* Functions can be used before they are declared
* Function declarations have a block scope
### Function Expression
```js
let func1 = function([parameters]) {
    //code
    return [val];
} ;
```
* JavaScript deals with function as a value
* Example
    ```js
    let sayHi = function() {
        alert('Hi!')
    } ;
    let func = sayHi; //copies the function

    func(); //prints 'Hi!'
    sayHi(); //prints 'Hi!'
    ```
* Function expressions can only be used after declaration
* Function expressions have a global scope

### Callback functions
* Functions can be passed into another function and "called back" as needed
* Example
    ```js
    function ask(question, yes, no) {
        if (confirm(question)) yes()
        else no();
    }

    let yes = function(){alert('You said OK')};
    let no = function(){alert('You said Cancel')};

    ask('Please confirm', yes, no) //prints "You said OK" or "You said Cancel" depending on user response
    ```

### Arrow Functions
* Single-line arrow functions
    ```js
    let func = (arg1, arg2, ..., argn) => expression;
    ```
    * `func`: function that accepts arguments, and returns the result of `expression`
    * Example
        ```js
        let sum = (a, b) => a + b;
        alert(sum(1,2)); //3
        ```
* Multi-line arrow functions
    ```js
    let func = (arg1, arg2, ..., argn) => {
        //code
        return val;
    }
    ```

## 10. Objects
### Creating an object
```js
let objName = {
    prop1: val1,
    'prop 2': val2,
    ...,
    propN: valN,
};
```
### Properties
```js
let x = objName.prop1; //x = val1
let y = objName['prop 2']; //accessing multi-word properties

objName.propA = valA; //adding a new property
delete objName.prop1; //deleting a property
```

* The square bracket can also be used when obtaining property names from an expression
    * Example
        ```js
        let key = 'propN';
        alert(objName[key]); //works fine
        alert(objName.key); //undefined
        ```
* Computed properties
    ```js
    let x = prompt("Enter a value", "default");

    let obj = {
        [x]: val,
    };

    alert(obj.x); //prints obj.default if x == "default"
    ```

### Property Value Shorthand
```js
function makeObj(val1,val2) {
    return {
        prop1,
        prop2,
    };
}
```
* Shorthand is equivalent to below code:
```js
    function makeObj(val1, val2) {
        return {
            prop1: val1,
            prop2: val2,
        };
    }
```
### `in` Operator
* Syntax
    ```js
    let x = "key" in object; //returns true or false
    ```
* Example
    ```js
    let user = {name: 'John'};
    alert('name' in user); //true
    alert('age' in user); //false

    let key = 'name'
    alert(key in user); //true (user.name exists)
    ```
* Looping through properties
    ```js
    for (let key in object) {
        //code
    }
    ```
    * Integer properties are sorted in order
    * Other properties appear in creation order



