# JavaScript Assignment Operators

Assignment operators assign values to JavaScript variables.

| Operator | Example   | Same As      |
| -------- | --------- | ------------ |
| `=`      | x = y     | x = y        |
| `+=`     | x += y    | x = x + y    |
| `-=`     | x -= y    | x = x - y    |
| `*=`     | x \_= y   | x = x \* y   |
| `/=`     | x /= y    | x = x / y    |
| `%=`     | x %= y    | x = x % y    |
| `**=`    | x \*\*= y | x = x \*\* y |

```javascript
let num1, num2;
num1 = 15;
num2 = 10;
num1 = num1 * num2 + 50; // result => 200
num1 *= num2 + 50; // result => 900
console.log(num1);
// *= এর ক্ষেত্রে শুধু ২টা variable use করা উচিত।
```
