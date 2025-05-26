# Ex.No:5
# RECOGNITION OF THE GRAMMAR(a^nb where n>=10) USING YACC
## Register Number: 212223040233
## Date:30-04-2025
## AIM:
To write a YACC program to recognize the grammar a^nb where n>=10.
## ALGORITHM:
1.	Start the program.
2.	Write a program in the vi editor and save it with .l extension.
3.	In the lex program, write the translation rules for the variables a and b.
4.	Write a program in the vi editor and save it with .y extension.
5.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
6.	Compile the yacc program with yacc compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
7.	Compile these with the C compiler as gcc lex.yy.c y.tab.c
8.	Enter a string as input and it is identified as valid or invalid.
## PROGRAM:

## anb.h

```
%{
#include "anb.tab.h"
%}

%%
[aA]    { return A; }
[bB]    { return B; }
\n      { return NL; }
.       { return INVALID; }  // Catch invalid characters
%%

int yywrap() {
    return 1;
}
```

## anb.y

```
%{
#include <stdio.h>
#include <stdlib.h>

int a_count = 0;
int yylex(void);
int yyerror(const char *msg);
%}

%token A B NL INVALID

%%
stmt: S B NL {
    if (a_count >= 10)
        printf("valid string\n");
    else
        printf("invalid string\n");
    exit(0);
};

S: A S { a_count++; }
 | A   { a_count++; }
;

%%

int yyerror(const char *msg) {
    printf("invalid string\n");
    exit(0);
    return 0;
}

int main() {
    printf("Enter the string:\n");
    yyparse();
    return 0;
}

```
## OUTPUT:

![439089118-289ff512-7177-4982-90d6-57a8c8126c6e](https://github.com/user-attachments/assets/067c4ffe-56a6-4aa2-8e46-e6fad2e0b8e3)

## RESULT:
The YACC program to recognize the grammar anb where n>=10 is executed successfully and the output is verified.
