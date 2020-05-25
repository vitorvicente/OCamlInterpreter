# OCaml Interpreter

As a final project for my Concepts of Programming Languages class at BU (CS 320 - Spring 2020), I developed a functional stack interpreter in OCaml, the project was devided in 3 stages and constructed to allow for a functional programming language.

All the code is MY OWN, and, although I had assistance from faculty, no parts of this work were written by them.

<br />
 
## Basic Grammar

The following is the basic grammar for the programming language:

- digit ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
- letter ::= a | b | ... | z | A | B | ... | Z
- simpleASCII ::= { All simple ASCII characters besides " and \ }

- int ::= [−] digit { digit }
- bool ::= < true > | < false >
- error ::= < error >
- unit ::= < unit >
- string ::= "{ simpleASCII }"
- name ::= { _ } letter { letter | digit | _ }

- const ::= int | bool | error | string | name | unit

<br />

In addition, the grammar for this language allows for the creation of programs and functions:

- funBind ::= (Fun | InOutFun) name1 name2
- com ::= PushI int | PushB bool | PushS string | PushN name | Push <unit> | Add | Sub | Mul | Div | Rem | Neg | Swap | Pop | Concat | And | Or | Not | LessThan | Equal | If | Bind | Begin com {com} End 
          | funBind com {com} [ Return ] FunEnd | Call | Quit
- prog ::= com {com} Quit

<br />

## Command Explanation

Push Commands allow the user to push values onto the stack, to then use with other commands, these commands are followed by a string representing a value of the specific type in question, if they are not followed by any value, they will be ignored, with the exception of Push <unit>, which does not require any values, as it will always be the same value.

Add, Sub, Mul, Div and Rem commands are used to manipulate integers on the stack, they will use the integer ontop of the stack following by the next one. In case these commands are used with anything other than integers the programming will throw an error. The commands will work independently on the values themselves, with the maximum and minimum values of the int being the ones present in OCaml. Each of these operations does exactly what is expected of them, adding, subtracting, dividing, multiplying and performing the module operation on integers, they do this by using the built in functionalities in OCaml.

The Neg operator will swap the sign of whatever int is ontop of the stack. If this value is not an int, it will throw an error.

The Swap operator works on any set of values, and will invert the order of the two topmost values on the stack. It will throw an error if there is only a single value on the stack.

The Pop operator removes the topmost value of the stack, independently of what it is.

The Concat operator works on two strings at the top of the stack, concatonating them with the topmost coming first and the other coming second. If the two values ontop of the stack are not strings it will throw an error.

The And, Or, Not operators will work on either a pair, or in the case of Not, a single boolean value ontop of the stack, performing the logic operations they refer to. If the operators find that the needed values ontop of the stack are not booleans, it will throw an error.

The LessThan and Equal operators will compare two integer values present ontop of the stack, and return either < true > or < false > depending on the result of the operation.

The If operator is quite a unique one as it takes in 3 values, a boolean and two others of any type, it will then check if said boolean is < true > or < false >, then returning one of the two values depending on said boolean. The boolean must be the third value onto the stack, and the order of the other two is inverted, so if the boolean is < true > it will return the second value, and vice-versa.