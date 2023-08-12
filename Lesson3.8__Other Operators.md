### Table of content

-[typeof](#typeof) -[instanceof](#instanceof) -[delete](#delete) -[in](#in)

# Few Important JavaScript Operators

| Operator                 | Description                                               |
| ------------------------ | --------------------------------------------------------- |
| `typeof`                 | A keyword to return the data type of the operand.         |
| `instanceof`             | Used to check the type of operator at runtime.            |
| `delete`                 | Used to delete JavaScript object properties.              |
| `in`                     | Keyword used to check if a property exists or not.        |
| `comma(,)`               | Used to separate operands.                                |
| `Grouping`               | Used to override normal operator precedence.              |
| `Unary(+_) `             | Converts the type of variable to the number.              |
| `Short circuiting`       | Used for evaluating an expression.                        |
| `Nullish Coalescing(??)` | Used to return a value if the value is undefined or null. |

## typeof

```javascript
let str = "Hello";
typeof str; // string

let str2 = new String("10");
typeof str2; // object

let num = 25;
typeof num; // number

let num2 = new Number("20");
typeof num2; // object

let isActive = true;
typeof isActive; // boolean

let a = undefined;
typeof a; // undefined

let b = null;
typeof b; // object

let obj = { name: "Nazmul", age: 25 };
typeof obj; // object

let arr = [2, 4, 6];
typeof arr; // object

let func = new Function(3 + 5);
typeof func; // function
```

## instanceof

The instanceof operator returns true if the specified object is of the specified object type. The syntax is:

```javascript
objectName instanceof objectType;
```

where objectName is the name of the object to compare to objectType, and objectType is an object type, such as Date or Array.

```javascript
let a = ["Apple", "Banana"];
console.log(a instanceof Array); // true
console.log(a instanceof Object); // true
console.log(a instanceof Number); // false

let b = { name: "Nazmul", age: 25 };
console.log(b instanceof Object); // true
console.log(b instanceof Array); // false

let c = new Function(3 + 5);
console.log(c instanceof Function); // true

let str = new String(20);
console.log(str instanceof String); // true

let num = new Number("10");
console.log(num instanceof Number); // false
```

## delete

The delete operator deletes an object's property. The syntax is:

```javascript
delete object.property;
delete object[propertyKey];
delete objectName[index];
```

```javascript
delete Math.PI; // returns false (cannot delete non-configurable properties)

const myObj = { h: 4 };
delete myObj.h; // returns true (can delete user-defined properties)
```

```javascript
const person = { name: "Sakib", age: 35 };
delete person.age; // true
console.log(person); // {name: "Sakib"}
```

the delete operator doesn’t work for variables or function, it returns false and the actual variables and functions remain untouched.

```javascript
let num = 5;
console.log(delete num); //false

let sum = (a, b) => {
  return a + b;
};
console.log(delete sum); //false
```

Exception: Global variables can be removed using the delete operator. Because the global variables are properties of the window object and as delete works on objects, it’ll delete the variable.

```javascript
Example: toDelete = 5;

// true
console.log(delete toDelete);

// toDelete is not defined
console.log(toDelete);
```

## in

The in operator returns true if the specified property is in the specified object. The syntax is:

```javascript
propNameOrNumber in objectName;
```

- true: The value true is returned if the specified property is found in an object.
- false: The value false is returned if the specified property is not found in an object.

```javascript
const fruits = ["Apple", "Banana", "Mango"];
// you must specify the index number, not the value at that index

// Output of the indexed number
console.log(2 in fruits); // true

// Output of the Value
console.log("Banana" in fruits); // false;

// output of the Array property
console.log("length" in fruits); // true
```

```javascript
// built-in objects
"PI" in Math; // returns true

const str = new String("Hello");
"length" in str; // true
```

```javascript
// Custom object
const player = { name: "Sakib", age: 35 };
"name" in player; // true
"profession" in player; // false
```
