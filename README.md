# Ex.No:5
# RECOGNITION OF THE GRAMMAR(a^nb where n>=10) USING YACC
## Register Number: 212223040233
## Date:27-04-02-2025
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
```
// EXP5.l file
%{
/* Definition section */ #include "y.tab.h"
%}

/* Rule Section */
%%
[aA] {return A;}
[bB] {return B;}
\n {return NL;}
. {return yytext[0];}
%%

int yywrap()
{
return 1;
}
// EXP5.y file

%{
/* Definition section */
#include<stdio.h> 
#include<stdlib.h>
%}

%token A B NL

/* Rule Section */
%%
stmt: S NL { printf("valid string\n");
exit(0); }
;
S: A S B |;
%%

int yyerror(char *msg)
{
printf("invalid string\n"); exit(0);
}
int main()
{
printf("enter the string\n"); yyparse();
}

```
## OUTPUT:

![384919537-0ad9fbad-420d-40ac-85f0-abfbe3b2c634](https://github.com/user-attachments/assets/c7c343a1-0bbf-4de3-8b85-9d242c1acb4f)

## RESULT:
The YACC program to recognize the grammar anb where n>=10 is executed successfully and the output is verified.
