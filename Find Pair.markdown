# Problem

A class of students have a project to work on in pairs. Everyone in the class found a partner, apart from one student. Using the list provided (which details every student in the class represented by the number of their team), find the student with no partner

### Note

The number of teams can represent either: only two students or a single student.

The provided list can have between 3 and 10000 elements.

The team identifier is between 1 and 100000.

• Try to find the most efficient solution!

• Writing Unit Tests is mandatory.


### Example
```
Input

[2,4,5,4,2]

Output

5
```

# Solution

```javascript
function findSingleStudent(studentList) {
  // Create an object to store the frequency of each team number
  const frequency = {};
  
  // Count the frequency of each team number
  for (const student of studentList) {
    if (frequency[student]) {
      frequency[student]++;
    } else {
      frequency[student] = 1;
    }
  }
  
  // Find the team number with a frequency of 1
  for (const student in frequency) {
    if (frequency[student] === 1) {
      return parseInt(student);
    }
  }
}

// Example usage
const studentList = [2, 4, 5, 4, 2];
console.log(findSingleStudent(studentList));  // Output: 5
```

## Unit Tests
```javascript
const { assert } = require('chai');

// The function to be tested
function findSingleStudent(studentList) {
  return studentList.reduce((acc, student) => acc ^ student, 0);
}

// Unit tests
describe("findSingleStudent", function() {
  it("should return the student with no partner for a simple case", function() {
    const input = [2, 4, 5, 4, 2];
    const expectedOutput = 5;
    assert.equal(findSingleStudent(input), expectedOutput);
  });

  it("should return the student with no partner for a different input", function() {
    const input = [1, 1, 2, 3, 3];
    const expectedOutput = 2;
    assert.equal(findSingleStudent(input), expectedOutput);
  });

  it("should handle a large input efficiently", function() {
    const input = Array(9999).fill(1).concat([2]);
    const expectedOutput = 2;
    assert.equal(findSingleStudent(input), expectedOutput);
  });

  it("should return the correct output when there is only one student", function() {
    const input = [1];
    const expectedOutput = 1;
    assert.equal(findSingleStudent(input), expectedOutput);
  });

  it("should return the correct output when the unpaired student is at the end", function() {
    const input = [1, 2, 1, 2, 3];
    const expectedOutput = 3;
    assert.equal(findSingleStudent(input), expectedOutput);
  });

  it("should handle cases where the unpaired student is at the beginning", function() {
    const input = [7, 1, 1, 2, 2];
    const expectedOutput = 7;
    assert.equal(findSingleStudent(input), expectedOutput);
  });

  it("should handle cases with mixed team numbers", function() {
    const input = [5, 6, 5, 6, 7];
    const expectedOutput = 7;
    assert.equal(findSingleStudent(input), expectedOutput);
  });
});
```
