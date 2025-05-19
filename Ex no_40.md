## Given an array of strings sorted in lexicographical order, print all of its permutations in strict lexicographical order. If two permutations look the same, only print one of them. See the 'note' below for an example.

Complete the function next_permutation which generates the permutations in the described order.

## For example, s=[ab,bc,cd]. The six permutations in correct order are:

ab bc cd
ab cd bc
bc ab cd
bc cd ab
cd ab bc
cd bc ab
Note: There may be two or more of the same string as elements of .
## For example, s=[ab,bc,cd]. Only one instance of a permutation where all elements match should be printed. In other words, if s[0]==s[1], then print either s[0]  or s[1] but not both.

A three element array having three distinct elements has six permutations as shown above. In this case, there are three matching pairs of permutations where ab and ba are switched. We only print the three visibly unique permutations:

ab ab bc
ab bc ab
bc ab ab
## Input Format

The first line of each test file contains a single integer , the length of the string array .

Each of the next  lines contains a string .

Constraints

 contains only lowercase English letters.
Output Format

Print each permutation as a list of space-separated strings on a single line.

## Sample Input 0

2
ab
cd
## Sample Output 0

ab cd
cd ab
## Sample Input 1

3
a
bc
bc
## Sample Output 1

a bc bc
bc a bc
bc bc a

CODE:
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Compare function for qsort
int cmp(const void *a, const void *b) {
    return strcmp(*(const char **)a, *(const char **)b);
}

// Swap two pointers to strings
void swap(char **a, char **b) {
    char *temp = *a;
    *a = *b;
    *b = temp;
}

// Find the next lexicographical permutation of array of strings
// Returns 1 if next permutation exists, else 0
int next_permutation(char *arr[], int n) {
    int i = n - 2;

    // Step 1: Find the rightmost ascent
    while (i >= 0 && strcmp(arr[i], arr[i + 1]) >= 0)
        i--;
    if (i < 0)
        return 0; // no next permutation

    // Step 2: Find the rightmost element greater than arr[i]
    int j = n - 1;
    while (strcmp(arr[j], arr[i]) <= 0)
        j--;

    // Step 3: Swap arr[i] and arr[j]
    swap(&arr[i], &arr[j]);

    // Step 4: Reverse from i+1 to end
    int left = i + 1, right = n - 1;
    while (left < right) {
        swap(&arr[left], &arr[right]);
        left++;
        right--;
    }

    return 1;
}

// Print array of strings separated by space
void print_arr(char *arr[], int n) {
    for (int i = 0; i < n; i++) {
        printf("%s", arr[i]);
        if (i != n - 1) printf(" ");
    }
    printf("\n");
}

int main() {
    int n;
    scanf("%d", &n);
    char *arr[n];
    char buffer[101];
    for (int i = 0; i < n; i++) {
        scanf("%100s", buffer);
        arr[i] = strdup(buffer);  // allocate and copy
    }
    qsort(arr, n, sizeof(char *), cmp);
    print_arr(arr, n);
    while (next_permutation(arr, n)) {
        print_arr(arr, n);
    }
    for (int i = 0; i < n; i++) {
        free(arr[i]);
    }

    return 0;
}
OUTPUT:
a bc bc
bc a bc
bc bc a
