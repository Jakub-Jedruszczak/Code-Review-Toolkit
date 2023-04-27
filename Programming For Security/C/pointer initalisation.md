# Pointer Initalisation
Pointer initialisation is a process by which an address is allocated in a pointer variable. An uninitalised pointer can expose a lot of data if it is not initialised to the location of a memory location or function address. An attacker may be able to arbitrarily read, write, or potentially execute data that is stored in an uninitialized pointer. Therefore, it is critical to initialise pointers to mitigate the damage an attacker can cause. 
Pointers can also be attacked by a null pointer dereferencing attack, in which an attacker can access a pointer which is set to NULL, causing reliability issues in your code and potential denial of service. This works by causing an undefined behaviour in your program by accessing a `NULL` pointer, which should not be accessible by user processes, causing a crash; this can also allow them to access debugging information to expand their attack surface.
Let’s look at an example:
```c
void main(){
    int *ptr;
    if (nullptr != ptr){
        *ptr = 5;
    }
}
```
Since the pointer is not initialised, we can see that it will be given a random value which can potentially hold the address of a sensitive function or piece of data. 
There are multiple ways to mitigate the damage and risk an attacker could cause, such as error exception handling and using references instead of pointers; if pointers must be used, they should be replaced with smart pointers as opposed to raw pointers.
