Or simply ask ChatGPT...


Roadmap:
- [ ] cover below topics shortly for now, then go deeper into each as time permits
- [ ] clarify undefined behavior
- [ ] how to avoid undefined behavior
- [ ] segmentation fault
- [ ] how to avoid seg fault
- [ ] other fancy words?
- [ ] minimum compilation `make` and `cmake` for both gcc and clang
- [ ] I heard pointers are scary (how to go about them)
- [ ] I heard memory management is scary (how to go about it)
- [ ] object lifetime, copy, move semantics
- [ ] ...
- [ ] table of contents

C++ Best Practices
==================
While catchy title this document is to solidify my knowledge of C++ peculiarities and document common issues.

I work on providing correct information but I'm not a C++ expert. Use at your own risk :)

## What are the compilers available?
Most widely used are GCC, Clang and MSVC.

## How do I build my code into an executable?
TODO

## Where is the documentation on functions?
[cppreference.com](https://cppreference.com) is highly recommended.
Other notable resources are:
- [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines) - actual best practices
- [ISO standard](https://isocpp.org) - I recommend checking out [Get Started](https://isocpp.org/get-started), [Tour](https://isocpp.org/tour) and [FAQ](https://isocpp.org/faq)
- [cplusplus.com](https://cplusplus.com) - another website with reference and tutorials

## Undefined behavior
How come a language can have an undefined behavior (let's shorten to UB)?

C++ has an ISO standard which defines types of compiler freedom. One of the types is called "undefined behavior" where compiler is given freedom to decide how to behave.

Why does it exist then? It allows compiler to perform optimizations.

UB should be avoided since the code may produce unexpected results and may (may not!) fail at run-time (not compile-time!).
*For this reason, Clang provides [UndefinedBehaviorSanitizer](https://clang.llvm.org/docs/UndefinedBehaviorSanitizer.html) and gcc has -fsanitize=undefined(?).*

Examples of undefined behavior:
- Simple (expected) cases:
    - `NULL` or `nullptr` pointer dereference, or accessing pointer after calling `delete` or `free`
    - Division by zero, or INT32_MIN divided by -1 (see signed integer overflow)
        - since INT32_MAX is 2147483647 and INT32_MIN is -2147483648 so division by -1 will result in overflow
    - Accessing array or memory out of bounds
- More nuanced cases:
    - Use of an uninitialized variables. Very common. Yes, in C++ you should initialize variables.
    - Signed integer overflow is UB. Unsigned integer is defined to wrap around.
    - Modifying same variable more than once in an expression

### How to avoid undefined behavior?
"Be very careful, use good tools, and hope for the best." John Regehr
1. One approach is to define -Wall -Werr flags for gcc?

For now just copied exceprt from [Regehr's article](https://blog.regehr.org/archives/213) but would like to specify concrete steps:
- Enable and heed compiler warnings, preferably using multiple compilers
- Use static analyzers (like Clang’s, Coverity, etc.) to get even more warnings
- Use compiler-supported dynamic checks; for example, gcc’s -ftrapv flag generates code to trap signed integer overflows
- Use tools like Valgrind to get additional dynamic checks
- When functions are “type 2” as categorized above, document their preconditions and postconditions
- Use assertions to verify that functions’ preconditions are postconditions actually hold
- Particularly in C++, use high-quality data structure libraries

*to be continued...*

## Learn More
[A Guide to Undefined Behavior in C and C++, Part 1](https://blog.regehr.org/archives/213)
