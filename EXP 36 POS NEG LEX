%{
int positive_no = 0, negative_no = 0;
%}

%%
[-][0-9]+ {negative_no++;}
[0-9]+ {positive_no++;} 	
%%


int yywrap()
{}

int main()											
{
printf("\nEnter the input:");
yylex();
printf ("number of positive numbers = %d",positive_no);
printf("\nnumber of negative numbers = %d",negative_no);
return 0;
}
