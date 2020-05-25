# OCaml Interpreter

As a final project for my Concepts of Programming Languages class at BU (CS 320 - Spring 2020), I developed a functional stack interpreter in OCaml, the project was devided in 3 stages and constructed to allow for a functional programming language.

All the code is MY OWN, and, although I had assistance from faculty, no parts of this work were written by them.
 
 
## Basic Grammar

The following is the basic grammar for the programming language:

- digit ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
- letter ::= a | b | ... | z | A | B | ... | Z
- simpleASCII ::= { All simple ASCII characters besides " and \ }

- int ::= [−] digit { digit }
- bool ::= <true> | <false>
- error ::= <error>
- unit ::= <unit>
- string ::= "{ simpleASCII }"
- name ::= { _ } letter { letter | digit | _ }

- const ::= int | bool | error | string | name | unit

<br />

In addition, the grammar for this language allows for the creation of programs and functions:

- funBind ::= (Fun | InOutFun) name1 name2
- com ::= PushI int | PushB bool | PushS string | PushN name | Push <unit> | Add | Sub | Mul | Div | Rem | Neg | Swap | Pop | Concat | And | Or | Not | LessThan | Equal | If | Bind | Begin com {com} End 
          | funBind com {com} [ Return ] FunEnd | Call | Quit
- prog ::= com {com} Quit