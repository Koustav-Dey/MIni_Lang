# MIni_Lang
A Basic interpreted Programming Language from scratch in Python



Building a programming language from scratch can seem like a daunting task, but with the right approach and tools, it can also be a fun and educational experience. In this project, we will be using Python to build a simple interpreted programming language. An interpreted programming language is a language that is executed directly by the computer without being compiled. This means that the source code is read and executed line by line, with each line being translated into machine code and executed immediately.
There are many reasons why you might want to build your own programming language. For example, you might want to create a language that is tailored to a specific domain or task, or you might want to gain a deeper understanding of how programming languages work. Whatever your motivation, building a programming language is a challenging and rewarding endeavor.
In this project, we will start by defining the syntax and grammar of our language. We will then build a parser that can read and interpret the source code. Fin ally, we will add support for variables, arithmetic operations, control flow statements, functions, and recursion.
Before we dive into the details of building our language, let's take a moment to understand the basics of programming languages. A programming language is a formal language that is used to instruct a computer to perform specific tasks. Programs written in a programming language are composed of statements that are executed in a specific order to produce a desired result.


There are two main categories of programming languages: compiled and interpreted. A compiled language, such as C or C++, is translated into machine code by a compiler before being executed by the computer. An interpreted language, on the other hand, is executed directly by the computer without being compiled.
Interpreted languages have several advantages over compiled languages. For example, they are generally easier to use and require less setup and configuration. They are also more flexible and dynamic, which makes them ideal for tasks such as scripting, prototyping, and rapid application development.
Python is an interpreted language that is widely used for a variety of tasks, including web development, data analysis, and machine learning. Python is a popular choice for building interpreted programming languages because it is easy to learn, has a simple syntax, and provides powerful tools for parsing and interpreting source code.
Now that we have a basic understanding of programming languages and the advantages of interpreted languages, let's dive into the details of building our own interpreted programming language in Python.
The first step in building a programming language is to define its syntax and grammar. The syntax of a language refers to the rules for writing statements and expressions in the language. The grammar of a language refers to the rules for combining statements and expressions to form valid programs.
In our language, we will use a simple syntax that is similar to Python. Statements will be separated by newlines, and expressions will be evaluated and printed to the console. Here is an example of what a simple program in our language might look like:
suppose : 
x = 3
y = 4
print(x + y)

This program defines two variables, x and y, and prints their sum to the console. Note that we are using the print statement to output the result of the expression x + y.
To define the grammar of our language, we will use a 
context-free grammar (CFG). A CFG is a formal way of describing the syntax of a language. It consists of a set of production rules that specify how valid statements and expressions can be constructed.

Creating an interpreted programming language in Python was an interesting exercise to understand the basics of programming languages and how to create an interpreter. In this chapter, we will go through the steps required to create a very simple interpreted programming language in Python.

Step 1: Define the language syntax and grammar

The first step in creating an interpreted programming language is to define its syntax and grammar. The syntax defines the set of rules that determine how the code is written, while the grammar defines the structure of the code. In our case, we will define a very simple syntax and grammar that only supports arithmetic operations.

Our language will support basic arithmetic operations such as addition, subtraction, multiplication, and division. The syntax will consist of numbers, operators, and parentheses. For example, the expression "2 + 3 * 4" would be valid in our language.

Step 2: Define lexer

Once we have defined the syntax and grammar of our language, we need to write a lexer. A lexer is a program that breaks down the input code into a stream of tokens that can be easily parsed by the interpreter. In our case, the lexer will scan the input code and identify each token as a number, an operator, or a parenthesis.

We implement the lexer as a class the lexer will go through the input character by character and break up the text into a list of what we call tokens in the process that returns 

the next token in the input code. We can use regular expressions to match the tokens and return them as tuples consisting of a token type and a token value.


For example, the lexer can return the following tokens for the input "2 + 3 * 4":

('NUMBER', 2)
('PLUS', '+')
('NUMBER', 3)
('MUL', '*')
('NUMBER', 4)

Step 3: Define Parser

Once we have the lexer in place, we can write the parser. The parser takes the stream of tokens produced by the lexer and builds a syntax tree that represents the structure of the code. In our case, the syntax tree will be a binary tree that represents the arithmetic expressions.

We can implement the parser as a class that takes the lexer as a parameter and has a method called "parse()" that returns the syntax tree. We can use recursion to parse the tokens and build the syntax tree.
For example, the parser can parse the tokens produced by the lexer and build the following syntax tree for the input "2 + 3 * 4":
  
 ADD
  /   \
 2    MUL
     /   \
    3     4

Step 4: Write the interpreter

Once we have the parser in place, we can write the interpreter. The interpreter takes the syntax tree produced by the parser and evaluates the expressions. In our case, the interpreter will recursively evaluate the nodes of the syntax tree and perform the arithmetic operations.



We can implement the interpreter as a class that takes the syntax tree as a parameter and has a method called "interpret()" that returns the result of the expression. We can use recursion to evaluate the nodes of the syntax tree and perform the arithmetic operations.



For example, the interpreter can evaluate the syntax tree produced by the parser and return the result of the expression "2 + 3 * 4":

2 + 3 * 4 = 14
Step 5: Test the language

Once we have implemented the interpreter, we test our language by writing some test cases. We write some simple expressions and check if the interpreter produces the correct result.



4.1 Grammar Rules 

Programming languages generally have a formal grammar specification that defines the rules for writing code. This specification usually includes information on the types of tokens that are allowed, such as keywords, variables, and operators, as well as the order and arrangement in which these tokens can appear. We discussed about grammar after section.

exr         :  KEYWORD:VAR INDENTIFIER EQ expr
               : compr-expr ((KEYWORD: AND | KEYWORD: OR) comp-expr)*

comp-expr     : NOT compr-expr
                         :  arith-expr ((EE|LT|GT|LTE|GTE) arith-expr)*

artih-expr       :  term((PLUS|MINUS) term)*

term                 : factor ((MUL|DIV) factor)*

factor               : (PLUS|MINUS) factor
                          : power
 

power              : call (POW factor)*      

call                    : atom(LPAREN (expr (COMMA expr)*)? RPAREN)?

atom                 : INT|FLOAT|INDENTIFIER
                          : LPAREN expr RPAREN
                        
             : if-expr
                          : for-expr
                          : while-expr
                          : func-def

if-expr              : KEYWORD:IF expr KEYWORD:THEN expr
                         (KEYWORD:ELIF expr KEYWORD:THEN expr)*
                         (KEYWORD:ELSE expr)?

for-expr          : KEYWORD:FOR INDENTIFIER EQ expr KEYWORD: TO expr
                         (KEYWORD:STEP expr)? KEYWORD:THEN expr

while-expr    : KEYWORD:WHILE expr KEYWORD: THEN expr

func-def      : KEYWORD:FUN INDENTIFIER
                        LPAREN (INDENTIFIER (COMMA INDENTIFIER)*)? RPAREN
                        ARROW expr
