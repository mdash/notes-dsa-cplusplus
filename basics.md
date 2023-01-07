## Basic syntax
includes type varname assignment

Ambersand operator returns memory address

 a pointer (denoted by asterisk) is basically going to be a level of indirection away from data

```c++
int prime=7;
int *p = &prime;
```



### Stacks and pointers
- All variables are stored in stack memory by default
- stack memory starts at high address and goes/grows down towards 0.. C++ compilers can transform or rearrange the compiled code for optimization. In that case, the addresses of the variables in the stack layout may not be as predicted
- lifecycle of variable created inside function is as long as the function is being ran
    - local variable memory is cleared up after function execution and reused for something else
    - with this understanding of how memory is actually allocated, how memory works, we should never return a reference to a local variable from a function - will cause undefined behavior
- In C++, if we ever need memory that is longer than the life cycle of a function, we have to use heap memory. What it does:
    1. Allocate memory on heap for the data structure
    2. Initialize the data structure
    3. Return a Pointer to the first memory address of the data structure
- The new keyword is an operator in C++ that's going to return a pointer to the memory address starting of the new data, and not an instance of the data itself.
    - example: int *numPtr = new int; *numPtr = 42; Here numPtr refers to heap memory address but is itself stored in stack memory
    - the only time this memory's ever reclaimed is when we use the delete keyword.
    - after the line "delete c;" the pointer c still stores the address of the deleted variable, which is no longer valid to dereference and is therefore dangerous. The pointer won't be automatically set to nullptr. Then, you should manually set c to nullptr if you want to better protect against coding mistakes
    - always set to nullptr after delete Example: delete numPtr; numPtr = nullptr;
    - nullptr represents a pointer to nowhere (address 0x0). it will generate a segmentation fault when tried to access. Calls to delete 0x0 are ignored.
- Heap memory starts at low addresses and grows up (opposite of stack memory behavior)

