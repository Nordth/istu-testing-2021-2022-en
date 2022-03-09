# Task 6 (Test driven development)

For given text specification of function you need to create Unit-tests, which check correctness of function and then you need to code this function

## Phone number normalizer:

Function should check if input string contains valid phone number and transform it to following form: `+79999999999`

* valid phone number should consists of 11 digits
* first digit in valid phone number should be 7 or 8. (if it is 8 change it to 7)
* valid phone number can have plus sign at begining of the input strng
* valid phone number can have opening parenthesis between 1st and 2st digits
* valid phone number can have closing parenthesis between 4st and 5st digits
* valid phone number can have any number of dashes (`-`) and spaces

If input string doesn't contain valid phone number function should return `null`

```
function normalizePhone(str){
   // [...]
}
```

Examples:
|Input:  |Output: |
|-------|--------|
|`+7 999 233 4455` | `+79992334455` |
|`8 (999) 233-4455` | `+79992334455` |
|`8 (999) 233-44` | `null` |
|`+19992334455` | `null` |

