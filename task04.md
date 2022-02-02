Task 04: Equivalence classes
=======================

For following specifications:
- define equivalence classes
- make test cases using defined equivalence classes and possible boundary values

Example
-------
**Specification:**

Calculate square root of input positive number x. If x is not a positive number (or it is not number at all) throw exception

**Equivalence classes**
```
EC1. X is number
EC2. X is not number (invalid)
EC3. X > 0 
EC4. x <= 0 (invalid)
```

**Test cases**

Source  | Input    | Expected output
--------| ---------|---------------
EC1     | 4        | 2
EC2     | abc      | throws exception
EC3     | 16       | 4
EC4     | -16      | throws exception
EC3-4 B1 | -0.01   | throws exception  
EC3-4 B2 | 0       | throws exception  
EC3-4 B3 | 0.01    | 0.1

* `EC3-4 B1` - boundary between EC3 and EC4, sample 1


Specifications:
---------------

**Specification 1.** 

The user enters the number of tickets he wants to buy. Number of tickrts should be less than 10. 

Program calculates total price by formula and prints result: N * $100. 

If user number of tickets is not valid, it should print error message "Enter valid number of tickets"

**Specification 2.** 

User enters one of following command: `clone`, `pull`, `push`, `commit`. 

If command is correct, it should be executed. 

If user enters wrong command, program should print "Undefined command"

**Specification 3.** 

User enters his/her birthday in the format DD.MM.YYYY. 

If input is correct and age of user >= 18, the form should be sent.

If age of user < 18, program should show error: "Your age should be >= 18"

If input is invalid, program should show error: "Enter valid date"

**Specification 4.** 

User enters two datetimes in format: "YYYY-MM-dd HH:mm". 

Program should calculate number of seconds between two entered datetimes. 

The first entered datetime should be less than the second, otherwise program should return -1.

If entered date is in wrong format, print message "Enter correct date" and ask user to enter date again

**Specification 5.** 

Program ask user to enter old password, new password and repeat the new password. 

If any of entered passwords are empty print message "Enter passwords".

If old password is not corrent, print message "Wrong old password"

If length of new password less than 8 characters, print message: "Too short password"

If length of new password more than 16 charactes, print message "To long password"

If new password has no digit, print message "Password should have at least one digit"

If new password has no letters, print message "Password shoud have at least one letter"

If new password is not equal to repeated password, print message "Entered passwords are not same"

If no error occured save new password of user
