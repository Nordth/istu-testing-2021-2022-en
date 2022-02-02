# Task 2

For the following functions:
1) Create [control flow graph](https://en.wikipedia.org/wiki/Control-flow_graph) of function
2) Write test datasets which needed to visit all nodes in graphs

--------------------

1) [Fibonacci Number](https://github.com/trekhleb/javascript-algorithms/blob/master/src/algorithms/math/fibonacci/README.md)

```
function fibonacci(n) {
  const fibSequence = [1];                             // 1

  let currentValue = 1;                                // 2
  let previousValue = 0;                               // 3

  if (n === 1) {                                       // 4
    return fibSequence;                                // 5
  }

  let iterationsCounter = n - 1;                       // 6

  while (iterationsCounter) {                          // 7
    currentValue += previousValue;                     // 8
    previousValue = currentValue - previousValue;      // 9

    fibSequence.push(currentValue);                    // 10

    iterationsCounter -= 1;                            // 11
  }

  return fibSequence;                                  // 12
}
```

--------------------

2) [Hamming Distance](https://github.com/trekhleb/javascript-algorithms/blob/master/src/algorithms/string/hamming-distance/README.md)


```
function hammingDistance(a, b) {
  if (a.length !== b.length) {                                // 1
    throw new Error('Strings must be of the same length');    // 2
  }

  let distance = 0;                                           // 3

  for (
      let i = 0;                                              // 4
      i < a.length;                                           // 5
      i += 1                                                  // 6
   ) {                     
    if (a[i] !== b[i]) {                                      // 7
      distance += 1;                                          // 8
    }
  }

  return distance;                                            // 9
}
```
  
--------------------

3) [Binary Search](https://github.com/trekhleb/javascript-algorithms/blob/master/src/algorithms/search/binary-search/README.md)

```
function binarySearch(sortedArray, seekElement) {

  // These two indices will contain current array (sub-array) boundaries.
  let startIndex = 0;                                                           // 1
  let endIndex = sortedArray.length - 1;                                        // 2

  // Let's continue to split array until boundaries are collapsed
  // and there is nothing to split anymore.
  while (startIndex <= endIndex) {                                              // 3
    // Let's calculate the index of the middle element.
    const middleIndex = startIndex + Math.floor((endIndex - startIndex) / 2);   // 4

    // If we've found the element just return its position.
    if (sortedArray[middleIndex] == seekElement) {                              // 5
      return middleIndex;                                                       // 6
    }

    // Decide which half to choose for seeking next: left or right one.
    if (sortedArray[middleIndex] < seekElement) {                               // 7
      // Go to the right half of the array.
      startIndex = middleIndex + 1;                                             // 8
    } else {
      // Go to the left half of the array.
      endIndex = middleIndex - 1;                                               // 9
    }
  }

  // Return -1 if we have not found anything.
  return -1;                                                                    // 10
}
``` 
 
 
  
--------------------

4) [Bubble Sort](https://github.com/trekhleb/javascript-algorithms/blob/master/src/algorithms/sorting/bubble-sort/README.md)

```
function sort(originalArray) {
    // Flag that holds info about whether the swap has occur or not.
    let swapped = false;                                                        // 1
    // Clone original array to prevent its modification.
    const array = [...originalArray];                                           // 2
 
    for (
      let i = 1;                                                                // 3
      i < array.length;                                                         // 4
      i += 1                                                                    // 5
    ) { 
      swapped = false;                                                          // 6

      for (
         let j = 0;                                                             // 7
         j < array.length - i;                                                  // 8
         j += 1                                                                 // 9
       ) {
      
        // Swap elements if they are in wrong order.
        if (array[j + 1] < array[j]) {                                          // 10
          // Do the swap
          [array[j], array[j + 1]] = [array[j + 1], array[j]];                  // 11

          // Register the swap.
          swapped = true;                                                       // 12
        }
      }

      // If there were no swaps then array is already sorted and there is
      // no need to proceed.
      if (!swapped) {                                                           // 13
        return array;                                                           // 14
      }
    }

    return array;                                                               // 15
  }

```


Additional tasks
=================

**Additional task 1**
```
function reverseBits(input, bitsCount) {
  let reversedBits = 0;                                                          // 1

  for (let bitIndex = 0;                                                         // 2
           bitIndex < bitsCount;                                                 // 3 
           bitIndex += 1                                                         // 4
 ) {
    reversedBits *= 2;                                                           // 5

    if (Math.floor(input / (1 << bitIndex)) % 2 === 1) {                         // 6
      reversedBits += 1;                                                         // 7
    }
  }

  return reversedBits;                                                           // 8
}
```


