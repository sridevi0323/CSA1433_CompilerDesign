#include <stdio.h>
#include <string.h>


int isOperator(char c) {
    return (c == '+' || c == '*');
}


int precedence(char op) {
    if (op == '+')
        return 1;
    if (op == '*')
        return 2;
    return 0; 
}


int operatorPrecedenceParsing(char input[]) {
    int i = 0;
    int stack[100];
    int top = -1;

    
    stack[++top] = '$';

   
    strcat(input, "$");

    
    char token = input[i++];

    while (top >= 0) {
        if (token == stack[top]) {
            
            top--;
            token = input[i++];
        } else {
            int topPrecedence = precedence(stack[top]);
            int tokenPrecedence = precedence(token);

            if (topPrecedence < tokenPrecedence) {
                
                stack[++top] = token;
                token = input[i++];
            } else {
                
                printf("Reducing: %c\n", stack[top]);
                top--;
            }
        }
    }

    if (token == '$') {
        printf("Accepted\n");
        return 1;
    } else {
        printf("Rejected\n");
        return 0;
    }
}

int main() {
    char input[100];

    printf("Enter an expression: ");
    scanf("%s", input);

    if (operatorPrecedenceParsing(input)) {
        printf("Valid Expression\n");
    } else {
        printf("Invalid Expression\n");
    }

    return 0;
}
