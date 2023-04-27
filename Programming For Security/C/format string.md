# Format String Vulnerability
The format string vulnerability’s main cause is C’s lack of input sanitation for user input; this applies to both the format function (e.g., `printf`) and the function argument. For example:
```c
printf(“The value of the variable is: %d”, 10);
```
In this example, `printf` is the format function and `“The value of the variable is: %d”` and `10` are the arguments. `%d` denotes the type of the variable as well as where to insert it in the output. 
This can cause a vulnerability if the user can control either the first argument, the string to be formatted, or the data that will be formatted into the string. For example, an attacker could be able to change the string to something like this: 
```c
printf(“Values pulled from the stack are %d %p %p %p”, 10);
```
This would allow them to print values of void pointers from the stack, potentially exposing sensitive data or allow them to execute malicious code. Note that the attacker keeps the `%d` to stop the code from crashing.
To prevent this, we can add `%s` as an argument to the function, converting the potential code into plain text which cannot be executed. 
For C++, you can instead use the `std::format` and `std::vformat` which raises an error whenever types don’t match for the input at runtime or compile time.
