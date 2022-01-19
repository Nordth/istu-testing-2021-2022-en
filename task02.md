# Task 2

For the following functions:
1) Create [control flow graph](https://en.wikipedia.org/wiki/Control-flow_graph) of function
2) Write test datasets which needed to visit all nodes in graphs

--------------------

1) [Fibonacci Number](https://github.com/trekhleb/javascript-algorithms/blob/master/src/algorithms/math/fibonacci/README.md)

```
function fibonacci(n) {
  const fibSequence = [1];

  let currentValue = 1;
  let previousValue = 0;

  if (n === 1) {
    return fibSequence;
  }

  let iterationsCounter = n - 1;

  while (iterationsCounter) {
    currentValue += previousValue;
    previousValue = currentValue - previousValue;

    fibSequence.push(currentValue);

    iterationsCounter -= 1;
  }

  return fibSequence;
}
```

--------------------

2) [Hamming Distance](https://github.com/trekhleb/javascript-algorithms/blob/master/src/algorithms/string/hamming-distance/README.md)


```
function hammingDistance(a, b) {
  if (a.length !== b.length) {
    throw new Error('Strings must be of the same length');
  }

  let distance = 0;

  for (let i = 0; i < a.length; i += 1) {
    if (a[i] !== b[i]) {
      distance += 1;
    }
  }

  return distance;
}
```
  
--------------------

3) [Binary Search](https://github.com/trekhleb/javascript-algorithms/blob/master/src/algorithms/search/binary-search/README.md)

```
function binarySearch(sortedArray, seekElement) {

  // These two indices will contain current array (sub-array) boundaries.
  let startIndex = 0;
  let endIndex = sortedArray.length - 1;

  // Let's continue to split array until boundaries are collapsed
  // and there is nothing to split anymore.
  while (startIndex <= endIndex) {
    // Let's calculate the index of the middle element.
    const middleIndex = startIndex + Math.floor((endIndex - startIndex) / 2);

    // If we've found the element just return its position.
    if (sortedArray[middleIndex] == seekElement) {
      return middleIndex;
    }

    // Decide which half to choose for seeking next: left or right one.
    if (sortedArray[middleIndex] < seekElement) {
      // Go to the right half of the array.
      startIndex = middleIndex + 1;
    } else {
      // Go to the left half of the array.
      endIndex = middleIndex - 1;
    }
  }

  // Return -1 if we have not found anything.
  return -1;
}
``` 
 
 
  
--------------------

4) [Bubble Sort](https://github.com/trekhleb/javascript-algorithms/blob/master/src/algorithms/sorting/bubble-sort/README.md)

```
function sort(originalArray) {
    // Flag that holds info about whether the swap has occur or not.
    let swapped = false;
    // Clone original array to prevent its modification.
    const array = [...originalArray];

    for (let i = 1; i < array.length; i += 1) {
      swapped = false;

      for (let j = 0; j < array.length - i; j += 1) {
      
        // Swap elements if they are in wrong order.
        if (array[j + 1] < array[j]) {
          // Do the swap
          [array[j], array[j + 1]] = [array[j + 1], array[j]];

          // Register the swap.
          swapped = true;
        }
      }

      // If there were no swaps then array is already sorted and there is
      // no need to proceed.
      if (!swapped) {
        return array;
      }
    }

    return array;
  }

```
