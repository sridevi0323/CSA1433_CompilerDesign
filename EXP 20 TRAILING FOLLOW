#include <stdio.h>
#include <string.h>

#define MAX_STACK_SIZE 100
#define MAX_INPUT_SIZE 100

// Define the terminals and non-terminals
enum { TERM_PLUS, TERM_STAR, TERM_LPAREN, TERM_RPAREN, TERM_ID, TERM_END, NON_TERM_E, NON_TERM_T, NON_TERM_F };

// Define the operator precedence table
const char precedenceTable[6][6] = {
    // +  *  (  )  id  $
    {'>', '<', '<', '>', '<', '>'}, // +
    {'>', '>', '<', '>', '<', '>'}, // *
    {'<', '<', '<', '=', '<', ' '}, // (
    {'>', '>', ' ', '>', ' ', '>'}, // )
    {'>', '>', ' ', '>', ' ', '>'}, // id
    {'<', '<', '<', ' ', '<', '='}  // $
};

char stack[MAX_STACK_SIZE];
char input[MAX_INPUT_SIZE];

int top = -1;

void push(char token) {
    if (top < MAX_STACK_SIZE - 1) {
        stack[++top] = token;
    } else {
        printf("Stack overflow\n");
        exit(1);
    }
}

char pop() {
    if (top >= 0) {
        return stack[top--];
    } else {
        printf("Stack underflow\n");
        exit(1);
    }
}

int getTokenType(char token) {
    switch (token) {
        case '+':
            return TERM_PLUS;
        case '*':
            return TERM_STAR;
        case '(':
            return TERM_LPAREN;
        case ')':
            return TERM_RPAREN;
        case 'id':
            return TERM_ID;
        case '$':
            return TERM_END;
        default:
            return -1;
    }
}

int main() {
    printf("Enter an expression: ");
    fgets(input, sizeof(input), stdin);

    int len = strlen(input);
    int currentToken = 0;
    push('$');
    push('E');

    char token = input[currentToken];

    while (top >= 0) {
        char stackTop = stack[top];

        int stackTopType = getTokenType(stackTop);
        int tokenType = getTokenType(token);

        if (stackTopType == -1 || tokenType == -1) {
            printf("Invalid input.\n");
            return 1;
        }

        if (precedenceTable[stackTopType][tokenType] == '<') {
            push(token);
            currentToken++;
            token = input[currentToken];
        } else if (precedenceTable[stackTopType][tokenType] == '>') {
            int popped = 0;
            while (1) {
                char poppedToken = pop();
                popped++;
                if (poppedToken == '$' || poppedToken == ' ' || poppedToken == '<') {
                    break;
                }
            }
            currentToken -= popped - 1;
        } else if (precedenceTable[stackTopType][tokenType] == '=') {
            pop();
            currentToken++;
            token = input[currentToken];
        } else {
            printf("Invalid input.\n");
            return 1;
        }
    }

    if (token == '$' && currentToken == len - 1) {
        printf("Accepted.\n");
    } else {
        printf("Rejected.\n");
    }

    return 0;
}
