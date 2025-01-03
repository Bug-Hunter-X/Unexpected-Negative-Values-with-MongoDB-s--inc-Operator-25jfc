# MongoDB $inc Operator Unexpected Behavior

This repository demonstrates a potential issue with the `$inc` operator in MongoDB when used without proper safeguards.  The `$inc` operator, while convenient for incrementing or decrementing values, can inadvertently produce negative numbers if the initial value is already zero or if an update is attempted on a non-existent document.  This can lead to data inconsistency and application errors.

The `bug.js` file showcases the problem. The `bugSolution.js` file provides a corrected implementation.

## Bug
The primary issue lies in attempting to decrement a counter without first checking its value. If the counter is already zero, decrementing it results in a negative number.

## Solution
The solution involves using the `$inc` operator within a conditional update operation.  This ensures the counter is only decremented if its value is greater than zero.