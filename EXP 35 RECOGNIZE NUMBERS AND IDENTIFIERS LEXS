%{
#include<stdio.h>
%}
%%
if|else|while|int|switch|for|char { printf("\n%s is a KEYWORD", yytext);}
[a-zA-Z0-9]+ { printf("\n%s is IDENTIFIER", yytext);}
%%
int yywrap( ){}
int main()
{
	yylex();
}	%{
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
char alphabetList[1000] = "";
char numberList[1000] = "";  
%}

%%
[0-9]+  { strcat(numberList, yytext); }
[a-zA-Z]+ { strcat(alphabetList, yytext); }
. { printf("Invalid input: %s\n", yytext); }

%%

int yywrap() {
    printf("Alphabets: %s\n", alphabetList);
    printf("Numbers: %s\n", numberList);
    return 1;
}

int main() {
    char input[100];
    printf("Enter the input: ");
    fgets(input, sizeof(input), stdin);
    yy_scan_string(input);
    yylex();
    return 0;
}	%{
int positive_no=0,negative_no=0;
%}
%%
[-][0-9]+ {negative_no++;
              printf("negative number=%s\n",yytext);}
[0-9]+ {positive_no++; 
               printf("positive number=%s\n",yytext);}
%%
int yywrap(){}
int main()
{
yylex();
printf("number of posive integers=%d,"
               "number of negativenumbers=%d\n",
                        positive_no,negative_no);
return 0;
}
