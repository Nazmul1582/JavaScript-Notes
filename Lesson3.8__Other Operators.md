### Table of content

-[typeof](#typeof)

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
