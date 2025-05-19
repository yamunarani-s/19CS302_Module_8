# EX 39 C program to find sum of digits.
## DATE: 19/05/25
## AIM:
To write a C program to find sum of digits.

## Algorithm
1. Analyze the question
2. Follow the algorithm
3. Try the code
4. Check for error
5. Run & Display the output

## Program:
```
/*
C program to find sum of digits.
Developed by: 
RegisterNumber:  
*/
```
#include <stdio.h>

int main() {
    int num, sum = 0, temp;
    scanf("%d", &num);
    temp = num; 
    while (temp != 0) {
        sum += temp % 10; 
        temp /= 10;        
    }
    printf("Sum of digits of %d is %d\n", num, sum);
    return 0;
}


## Output:

Sum of digits of 1234 is 10

## Result:
Thus the program was executed and the output was verified successfully.
