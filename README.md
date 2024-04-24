# Recursive Descent Parser
_Erin Cameron_

## Introduction
What is a Recursive Descent Parser? A recursive descent parser has a subprogram for each nonterminal in its grammar. Many of these subprograms are recursive - hence the name - and produces a parse tree in top-down nature.

In this application, I have created a program to analyze the syntax of input programs for a hypothetical imperative programming language. The Extended Backus-Naur Form (EBNF) grammar for this imperative programming language is below:
```
<program> -> program begin <statement_list> end

<statement_list> -> <statement> {;<statement>}

<statement> -> <assignment_statement> | <if_statement> | <loop_statement>

<assignment_statement> -> <variable> = <expression>

<variable> -> identifier

<expression> -> <term> { (+|-) <term>}

<term> -> <factor> {(* | /) <factor> }

<factor> -> identifier | int_constant | (<expr>)

<if_statement> -> if (<logic_expression>) then <statement>

<logic_expression> -> <variable> (< | >) <variable>

<loop_statement> -> loop (<logic_expression>) <statement>
```

Where:
* Separators:
    * `|` --> OR
    * `{}` --> optional statement with zero or more repetitions
    * `()` --> encapsulates an OR selection
    * `;` --> statement terminator
* Keywords:
    * `program`
    * `begin`
    * `end`
    * `if`
    * `then`
    * `loop`
* Operators:
    * `+` --> Addition
    * `-` --> Subtraction
    * `*` --> Multiplication
    * `/` --> Division
    * `>` --> Greater than
    * `<` --> Less than
        * In this grammar, there are only two logic expressions `>` and `<`.
* Identifiers:
    * A string value that begins with a letter followed by 0 or more letters and/or digits

The nonterminal symbols include:
* `<program>`
* `<statement_list>`
* `<statement>`
* `<assignment_statement>`
* `<variable>`
* `<if_statement>`
* `<loop_statement>`
* `<expression>`
* `<logic_expression>`
* `<term>`
* `<factor>`
* `<expr>`

The program reads in an input test `.txt` file and determines whether or not the file contains syntax errors.


## Tools & Techniques
* Java
* Eclipse IDE


## Implementation
The implementation of the program follows the two steps below:
1. Implement a lexical analyzer as a subprogram of the main program. Each time the lexical analyzer is called, it should return the next lexeme and its token code.
2. Implement a parser based on the above Extended Backus-Naur Form (EBNF) rules. Create a subprogram for each nonterminal symbol which should parse only sentences that can be generated by the nonterminal.


## Test Cases
The following test case files have been included:
* `BeginMissing.txt` --> The syntax error in this test file is on line 2 where the keyword `begin` should be.
* `ExtraSemicolon.txt` --> The syntax error in this test file is on line 7 where there should not be a semicolon.
* `IfMisspelled.txt` --> The syntax error in this test file is on the beginning of line 6, where the keyword `if` is misspelled.
* `MissingThen.txt` --> The syntax error in this test file is at the end of line 4, there should be a `then` keyword.
* `NoErrors.txt` --> There are no syntax errors in this test file. 
* `SemicolonMissing.txt` --> The syntax error in this test file is a missing semicolon at the end of line 4.


## Run
To execute the program, follow the instructions below:
1. Clone the git repo: `https://github.com/erincameron11/recursive-descent-parser`
2. Open up the files as a Java project in the IDE of your choice.
3. Run the `RecursiveDescentParser.java` file and follow the commands in the console.
    * _Note: When entering a file name in the console, do not put the file extensions (in this case, `.txt`). For example: `NoErrors` is a valid file name entry in the console.