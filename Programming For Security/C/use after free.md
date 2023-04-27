# Use After Free (AKA Dangling Pointer)
C and its derivatives have a problem with memory management and garbage collection – clearing up used data and memory after it is no longer needed. Reading data from an area of memory that has been marked as free can lead to malicious actors reading the memory which was stored there.
The use of previously freed memory can have any number of adverse consequences, ranging from the corruption of valid data to the execution of arbitrary code, depending on the instantiation and timing of the flaw. The simplest way data corruption may occur involves the system's reuse of the freed memory. Use-after-free errors have two common and sometimes overlapping causes:

- Error conditions and other exceptional circumstances.
- Confusion over which part of the program is responsible for freeing the memory.

In the following example, a buffer is freed before being used by the `strncpy` command. This can allow a malicious actor to substitute data into the now freed area that used to belong to buffer1, allowing them to execute arbitrary code or enter arbitrary data into the buffer.
```c
#include <stdio.h>
#include <unistd.h>

#define BUFSIZE 512

int main(int argc, char **argv) {
    char *buffer1;
    char *buffer2;
    buffer1 = (char *) malloc(BUFSIZE);
    buffer2 = (char *) malloc(BUFSIZE);

    free(buffer1);

    strncpy(buffer1, argv[1], BUFSIZE - 1);
    free(buffer2);
}
```
If the newly allocated data happens to hold a class, in C++ for example, various function pointers may be scattered within the heap data. If one of these function pointers is overwritten with an address to valid shellcode, execution of arbitrary code can be achieved.
## Possible solutions
When freeing pointers, be sure to set them to `NULL` once they are freed. However, the utilization of multiple or complex data structures may lower the usefulness of this strategy.
Therefore, the above code would be fixed as such:
```c
#include <stdio.h>
#include <unistd.h>

#define BUFSIZE 512

int main(int argc, char **argv) {
	 char *buffer1;
	 char *buffer2;
    buffer1 = (char *) malloc(BUFSIZE);
    buffer2 = (char *) malloc(BUFSIZE);

    free(buffer1);
          buffer1 = NULL;

    strncpy(buffer1, argv[1], BUFSIZE - 1); // will produce an error
    free(buffer2);
}
```
