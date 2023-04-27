# Buffer Overflow
Buffer overflow is a very common security vulnerability found in languages that allow in-depth memory management, such as C. Buffer overflow errors are caused by languages not having inbuilt boundary checks, which serve to reduce the risk of overwriting memory. Writing outside memory that was allocated to a process can cause data corruption, crashes, and potentially leak sensitive data and execution of malicious code.
In the following example, overflowing the user_input variable by entering an input longer than 10 characters can affect the value in the `important_data` variable.
```c
#include <stdio.h>
int main()
{
    volatile int important_data = 0;
    char user_input[10];
    gets(user_input);
    // checking for buffer overflow
    if(important_data != 0)
    {
        printf(“important_data has been modified”);
    }
    else
    {
        printf(“important_data has not been changed”);
    }
}
```
There are multiple ways to prevent this issue, which can depend on the compiler and kernel features available.

- Stack canaries create random secret values in the stack before execution starts. Before a function returns, this value is verified that it has not been changed.
- Address Space Layout Randomisation (ASLR) randomises the layout of the stack, making it much harder for attackers to guess which buffer to attack.
- Data Execution Prevention (DEP) mark certain memory locations such as the stack as non-executable. 
- Using your compiler or IDE of choice to automatically add boundary checks using Static Application Security Testing (SAST) tools.

In addition to using OS and compiler features, we must implement good coding practices, including bounds checking. We should avoid using standard library functions vulnerable to buffer overflow attacks, such as `get`, `strcpy`, `strcat`, `scanf`, and `printf`, as they don’t perform bounds checking. Instead, we should replace them with equivalent secure functions, like `fgets`.

- Using trusted libraries that implement boundary checks, such as Safe C String Library and `strsafe.h` library will help to mitigate the risk of buffer overflow attacks on strings.
- When using functions that accept a number of bytes to copy, such as `strncpy()`, be aware that if the destination buffer size is equal to the source buffer size, it may not NULL-terminate the string.
- Check buffer boundaries if accessing the buffer in a loop and make sure there is no danger of writing past the allocated space.
- If necessary, truncate all input strings to a reasonable length before passing them to the copy and concatenation functions.

