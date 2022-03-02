Test 1
=======

**1) Draw control flow graphs for the functions**

| Variant   | Function 1             | Function 2             |
|-----------|------------------------|------------------------|
| 1         | hsvToRgb               | combSort               |
| 2         | RailwayTimeConversion  | bucketSort             |
| 3         | isPalindrome           | flashSort              |
| 4         | rgbToHsv               | cocktailShakerSort     | 
| 5         | decimalToOctal         | cycleSort              |


**isPalindrome**
```javascript
export default function isPalindrome(string) {
  let left = 0;                            // 1
  let right = string.length - 1;           // 2

  while (left < right) {                   // 3
    if (string[left] !== string[right]) {  // 4
      return false;                        // 5
    }
    left += 1;                             // 6
    right -= 1;                            // 7
  }

  return true;                             // 8
}
```

**decimalToOctal**
```javascript
function decimalToOctal (num) {
  let oct = 0                              // 1
  let c = 0                                // 2
  while (num > 0) {                        // 3
    const r = num % 8                      // 4
    oct = oct + (r * Math.pow(10, c++))    // 5
    num = Math.floor(num / 8)              // 6
  }
  return oct                               // 7
}
```

**RailwayTimeConversion**
```javascript
function RailwayTimeConversion(timeString) {
  // firstly, check that input is a string or not.
  if (typeof timeString !== 'string') {                                            // 1
    return new TypeError('Argument is not a string.')                              // 2
  }
  // split the string by ':' character.
  const [hour, minute, scondWithShift] = timeString.split(':')                     // 3
  // split second and shift value.
  const [second, shift] = [scondWithShift.substr(0, 2), scondWithShift.substr(2)]  // 4 
  // convert shifted time to not-shift time(Railway time) by using the above explanation.
  if (shift === 'PM') {                                                            // 5
   if (parseInt(hour) === 12) {                                                    // 6
    	return `${hour}:${minute}:${second}`                                       // 7
   } else { 
        return `${parseInt(hour) + 12}:${minute}:${second}`                        // 8
   }
  } else {
    if (parseInt(hour) === 12) {                                                   // 9
        return `00:${minute}:${second}`                                            // 10
    } else { 
        return `${hour}:${minute}:${second}`                                       // 11
    }
  }
}
```

**rgbToHsv**
```javascript
export function rgbToHsv (red, green, blue) {

  const dRed = red / 255                                                 // 1
  const dGreen = green / 255                                             // 2
  const dBlue = blue / 255                                               // 3
  const value = Math.max(Math.max(dRed, dGreen), dBlue)                  // 4
  const chroma = value - Math.min(Math.min(dRed, dGreen), dBlue)         // 5
  const saturation = value === 0 ? 0 : chroma / value                    // 6
  let hue

  if (chroma === 0) {                                                    // 7
    hue = 0                                                              // 8
  } else if (value === dRed) {                                           // 9
    hue = 60 * ((dGreen - dBlue) / chroma)                               // 10
  } else if (value === dGreen) {                                         // 11
    hue = 60 * (2 + (dBlue - dRed) / chroma)                             // 12
  } else {                                             
    hue = 60 * (4 + (dRed - dGreen) / chroma)                            // 13
  }
 
  hue = (hue + 360) % 360                                                // 14

  return [hue, saturation, value]                                        // 15
}
```


**hsvToRgb**
```javascript
export function hsvToRgb (hue, saturation, value) {
  if (hue < 0 || hue > 360) {                                                   // 1
    throw new Error('hue should be between 0 and 360')                          // 2
  }

  if (saturation < 0 || saturation > 1) {                                       // 3
    throw new Error('saturation should be between 0 and 1')                     // 4
  }

  if (value < 0 || value > 1) {                                                 // 5
    throw new Error('value should be between 0 and 1')                          // 6
  }

  const chroma = value * saturation                                             // 7
  const hueSection = hue / 60                                                   // 8
  const secondLargestComponent = chroma * (1 - Math.abs(hueSection % 2 - 1))    // 9
  const matchValue = value - chroma                                             // 10

  return getRgbBySection(hueSection, chroma, matchValue, secondLargestComponent) // 11
}
```


**bucketSort**
```javascript
export function bucketSort (list, size) {
  if (undefined === size) {                                     // 1
    size = 5                                                    // 2
  }
  if (list.length === 0) {                                      // 3
    return list                                                 // 4
  }
  let min = findMin(list)                                       // 5
  let max = findMax(list)                                       // 6
  // how many buckets we need
  const count = Math.floor((max - min) / size) + 1              // 7

  // create buckets
  const buckets = []                                            // 8
  for (
    let iCount = 0;                                             // 9
    iCount < count;                                             // 10
    iCount++                                                    // 11
  ) {
    buckets.push([])                                            // 12
  }

  // bucket fill
  for (
    let iBucket = 0;                                            // 13
    iBucket < list.length;                                      // 14
    iBucket++                                                   // 15
  ) {
    const key = Math.floor((list[iBucket] - min) / size)        // 16
    buckets[key].push(list[iBucket])                            // 17
  }
  let sorted = []                                               // 18
  // now sort every bucket and merge it to the sorted list
  for (
  	let iBucket = 0;                                            // 19
  	iBucket < buckets.length;                                   // 20
  	iBucket++                                                   // 21
  ) {
    const arr = buckets[iBucket].sort((a, b) => a - b)          // 22
    sorted = [...sorted, ...arr]                                // 23
  }
  return sorted                                                 // 24
}
```



**cycleSort**
```javascript
function cycleSort (list) {
  for (                 
  	let cycleStart = 0;                                        // 1        
  	cycleStart < list.length;                                  // 2
  	cycleStart++                                               // 3
  ) { 
    let value = list[cycleStart]                               // 4
    let position = searhPosition(list, cycleStart, value)      // 5

    // if it is the same, continue
    if (position === cycleStart) {                             // 6
      continue
    }
    while (value === list[position]) {                         // 7
      position++                                               // 8
    }

    const oldValue = list[position]                            // 9
    list[position] = value                                     // 10
    value = oldValue                                           // 11

    // rotate the rest
    while (position !== cycleStart) {                          // 12
      position = cycleStart                                    // 13
      for (                                 
        let i = cycleStart + 1;                                // 14
        i < list.length;                                       // 15
        i++                                                    // 16
      ) {
        if (list[i] < value) {                                 // 17
          position++                                           // 18
        }
      }
      while (value === list[position]) {                       // 19
        position++                                             // 20
      }
      const oldValueCycle = list[position]                     // 21 
      list[position] = value                                   // 22
      value = oldValueCycle                                    // 23
    }
  }
  return list                                                  // 24
}
```


**flashSort**
```javascript
export function flashSort (arr) {
  const n = arr.length                         // 1
  const m = ~~(0.45 * n)                       // 2
  const l = new Array(m)                       // 3

  let [min, max] = findMinMaxp(arr);           // 4

  if (min === arr[max]) {                      // 5
    return arr                                 // 6
  }

  const c1 = (m - 1) / (arr[max] - min)        // 7
  prepare(l, k, m)                             // 8

  let hold = arr[max]                          // 9               
  arr[max] = arr[0]                            // 10
  arr[0] = hold                                // 11

  // permutation
  let move = 0; let t; let flash               // 12
  let j = 0                                    // 13
  let k = m - 1                                // 14

  while (move < (n - 1)) {                     // 15
    while (j > (l[k] - 1)) {                   // 16
      ++j                                      // 17
      k = ~~(c1 * (arr[j] - min))              // 18
    }
    if (k < 0) break                           // 19                  
    flash = arr[j]                             // 20
    while (j !== l[k]) {                       // 21
      k = ~~(c1 * (flash - min))               // 22
      hold = arr[t = --l[k]]                   // 23
      arr[t] = flash                           // 24
      flash = hold                             // 25
      ++move                                   // 26
    }
  }

  insert(arr, n)                               // 27

  return arr                                   // 28
}
```

**combSort**
```javascript
function combSort (list) {
  if (list.length === 0) {                                    // 1
    return list                                               // 2
  }
  const shrink = 1.3                                          // 3
  let gap = list.length                                       // 4
  let isSwapped = true                                        // 5
  let i = 0                                                   // 6

  while (gap > 1 || isSwapped) {                              // 7
    // Update the gap value for a next comb  
    gap = parseInt(parseFloat(gap) / shrink, 10)              // 8
 
    isSwapped = false                                         // 9
    i = 0                                                     // 10

    while (gap + i < list.length) {                           // 11
      if (list[i] > list[i + gap]) {                          // 12
        const temp = list[i]                                  // 13
        list[i] = list[i + gap]                               // 14
        list[i + gap] = temp                                  // 15
        isSwapped = true                                      // 16
      }
      i += 1                                                  // 17
    }
  }
  return list                                                 // 18
}
```


**cocktailShakerSort**
```javascript
export function cocktailShakerSort (items) {
  for (
    let i = items.length - 1;                                    // 1
    i > 0;                                                       // 2
    i--                                                          // 3
  ) {
    let j 

    // Backwards
    for ( 
      j = items.length - 1;                                      // 4
      j > i;                                                     // 5
      j--                                                        // 6
    ) {
      if (items[j] < items[j - 1]) {                             // 7
        [items[j], items[j - 1]] = [items[j - 1], items[j]]      // 8
      }
    }

    // Forwards
    for (
      j = 0;                                                     // 9
      j < i;                                                     // 10
      j++                                                        // 11
    ) {
      if (items[j] > items[j + 1]) {                             // 12
        [items[j], items[j + 1]] = [items[j + 1], items[j]]      // 13
      }
    }
  }

  return items                                                   // 14
}
```


--------------------------------------


**2) Define equivalence classes and prepare test cases ([See task 4](task04.md))**

| Variant   | Specification             |
|-----------|------------------------|
| 1         | User enters several numbers. Program should calculate average value of entered numbers, round it to three decimal places and print to user in format "9.999" (ex. "0.123"). If the number of entered values is zero, print "0.000". Every non-numeric values should be ignored. User can input fractional values using "." (1.15) and "," (1,15) as separator |
| 2         | The user enters in the format "YYYY-MM-DD" or in the format "YYYY-MM" (in the second case, the first day of the month is assumed). The program should print the number of days that have passed since the beginning of the year. If the user entered the wrong date, print "WRONG DATE". If the user entered empty string instead of date, print nothing |
| 3         | User enters two strings. If the first entered string contains the second one, program should print found position of substring, otherwise print 'NO'. If the first string is empty, print "EMPTY". If the second string is empty, print "0". If the second string is longer than the first one, print "ERROR" |
| 4         | User enters multi-line text. Program should print the shortest line from the entered text. Empty lines should be ignored. If entire entered text is empty, print message "EMPTY TEXT". If there are multiple shortest strings, print them all.  |
| 5         | User enters coordinates of two points: start position and end position. Points' coordinates consist of two integer numbers. Program should calculate distance between two entered points. If resultant value is fractional, round it to two decimal places and print it in format "9.99" (ex, "3.14"). If it is integer print it in format "9" (ex, "42")  |
