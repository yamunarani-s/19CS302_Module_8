# # Task

# # Given a positive integer denoting , do the following:

# If  41<=n <=49 print the lowercase English word corresponding to the number (e.g., forty one for 41 , forty two for 42 etc.).
If n>49 print Greater than 49.
## Input Format

The first line contains a single integer, .

## Constraints

## Output Format

If  41<=n <=49 print the lowercase English word corresponding to the number (e.g., forty one for 4 , forty two for 42 etc.).
If n>49 print Greater than 49.
## Sample Input

41
## Sample Output

forty one
#include <stdio.h>

int main() {
    int n;
    scanf("%d", &n);
    if (n < 41) {
        return 0;
    }
    if (n > 49) {
        printf("Greater than 49\n");
        return 0;
    }
    char *tens = "forty";
    char *ones[] = {
        "one", "two", "three", "four", "five",
        "six", "seven", "eight", "nine"
    };
    printf("%s %s\n", tens, ones[n - 41]);
    return 0;
}
outputr:
forty one
