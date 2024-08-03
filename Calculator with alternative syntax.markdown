# Problem

We'd like you to write a calculator to perform basic arithmetic, but use an alternative syntax for writing the expressions.
In this alternative notation, the operators precede the operands. For example, while in traditional notation we might write 3 + 4, instead we would write + 3 4.

The main advantage of this format is that it does not require parentheses for any ambiguous expression.

Traditional notation
3+4 | 3-(4*5) | (3+4)*5

Alternative notation
+34 | -3*45 | *+345

In the code provided, the app/calculator.js file exports a calculate function. This function is expected to take an alternative expression as a string and output the numerical solution.
We have included some tests to check this function works as expected.

### Install dependencies 
```
npm install
```

### Run the code
```
npm start
```

### Run test
```
npm test
```

# Solution
```javascript
exports.calculate = function calculate(expression){
  if(!expression) return 0;
  const token = expression.split(" ").reverse();
  const stack = [];

  for(const n of token){
    if(isNaN(n)){
      let result;
      switch(n){
        case '+':
          result = Number(stack.pop()) + Number(stack.pop());
          break;
        case '-':
          result = Number(stack.pop()) - Number(stack.pop());
          break;
        case '*':
          result = Number(stack.pop()) * Number(stack.pop());
          break;
        case '/':
          result = Number(stack.pop()) / Number(stack.pop());
          break;
      }
      stack.push(result);
    } 
    else stack.push(n);
  }
  return stack.pop();
}
```

# Unit Tests
```javascript
const assert = require('assert');
const calculator = require('./app/calculator');

it("calculates addition", function() {
    let result = calculator.calculate("+ 3 4");
    assert.equal(result, 7); // Expected result
});

it("calculates subtraction and multiplication", function() {
    let result = calculator.calculate("- 3 * 4 5");
    assert.equal(result, -17); // Expected result
});

it("calculates expression with negative numbers", function() {
    let result = calculator.calculate("* -2 + 3 4");
    assert.equal(result, -14); // Expected result
});
```
