## Functions In The Language

This is perhaps the most complex part of the entire interpreter, as we want extreme control over our operations, Functions in this language will be handled just as any other value, which means they can also be used as a variable. Functions can also be declared anywhere, including in other functions and environments, in theory, you can nest as many functions as you'd like, although this might slow down the program.

There are two types of functions in this language, regular Functions denoted by the Fun operator, and In and Out Functions denoted by the InOutFun operator.

Regular Functions, denominated by the Fun operator, followed by the name of the function and the name of the argument. This operator is than followed by a list of commands, which are parsed until the interpreter finds a FunEnd operator, at which point the entire function will be copied onto the current environment so that it can be called upon. In addition to the command list, the function will also take a copy of the environment in which it was first declared. Declaring a function will return a < unit > value, just as binding a variable does.

In order to call a function, you must use the Call operator, which will first look at the two uppermost values in the stack, if the second value is discovered to be a function bound name, it will than parse the first value as the argument of the function, binding it to the variable name previously associated with this argument. Once this is confirmed, the function will run with the argument given, using an empty stack and the environment previously given to it. Every function must have a return statement, which will allow the topmost value of the function stack to be returned to the top of the running stack before the calling.

In and Out Functions are mostly like their regular counterpart, with one small exception, which is that, at the end of the function call, they will also bind the return value to the name first given as an argument. They also will ALWAYS require the passing of a name instead of a variable as an argument.

Functions can also be used as both return values and arguments into other functions, thus allowing for total control.