Task 05: Unit testing using Mocha
=======================

For following specifications:
- write JS function that implements it
- define at least 5 test cases (input data and expected output)
- write unit tests using Mocha

Specifications:
---------------

**Specification 1.** 

Function receives three numbers and returns minimum value. If any of input values are not numbers, throw error "Wrong arguments"

**Specification 2.** 

Function receives array of strings and return the longest string from the array. If input array is empty, it should return `null`. 

Every non-string values in the input array should be converted to string (using `.toString()` function)

**Specification 3.** 

Function receives two arrays of numbers: `a` (a1, a2, a3 ... an) and `b` (b1, b2, b3 ... bn). 

It should returns array `c`, which defined as: c1 = a1 + b1, c2 = a2 + b2, c3 = a3 + b3 ... cn = an + bn

If input arrays have different number of elements, throw error "Input arrays should have same size"

Any non-number in input arrays should be interpreted as value 0 `(a: [1, 2], b: [3, 'a'] => c: [4, 2])`
