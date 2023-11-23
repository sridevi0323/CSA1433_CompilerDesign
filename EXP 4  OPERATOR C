#include <stdio.h>
#include <string.h>
#include <stdbool.h>
#include <ctype.h>

bool isOperator(char op) {
    return (op == '+' || op == '-' || op == '*' || op == '/');
}

int main() {
    char input[100];
    printf("Enter an arithmetic expression: ");
    fgets(input, sizeof(input), stdin);

    int i = 0;
    while (input[i] != '\0') {
        if (isOperator(input[i])) {
            printf("%c is a valid operator.\n", input[i]);
        }
        i++;
    }

    return 0;
}
