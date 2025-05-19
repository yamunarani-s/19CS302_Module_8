# # #Task - Hackerrank Problem

This challenge requires you to print Hello Saveetha! on a single line, and then print the already provided input string to stdout. If you are not familiar with C, you may want to read about the printf() command.

# # Example:

Saveetha

The required output is: Hello, Saveetha! C Programming
#include <stdio.h>

int main() {
    char input[100];
    printf("Hello Saveetha!\n");
    fgets(input, sizeof(input), stdin);
    printf("%s", input);

    return 0;
}
