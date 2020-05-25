## Variables In The Language

This language allows for its users to bind whatever value they wish, including < unit > to a variable of type name. As such, all operations check for the use of variables before returning errors.

In order to use variables however, you first need to bind the variable to a specific value, to do so you can use the Bind operator, this will search for a name ontop of the stack, followed by a value of any type, and will bind it to the current environment. Running this operator will result in a < unit > value being pushed ontop of the stack.

Although you are technically allowed to bind a variable to another variable, what will actually happen is that the program will look for the value represented by this variable, and bind the new one to that value. This is done to lower search times when trying to find variables.

With variables we are faced with another issue, environments, now, each time you run this program you will start off with a fresh environment. This is coupled with the Begin and End operators, which will open (or close) new environments. Once an environment is open, any variables declared on the previous one will be transfered, however, any variables declared INSIDE this new environment will not be transfered back once it is closed. This follows the basic idea of variable scoping.

Environments can be nested indefinitely. When going into an environment, you will be given a copy of the current stack, and once you end said environment, it will return whatever value is at the topmost position of the stack.