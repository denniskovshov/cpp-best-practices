Roadmap:
- [ ] clarify undefined behavior
- [ ] how to avoid undefined behavior
- [ ] segmentation fault
- [ ] how to avoid seg fault
- [ ] other fancy words?
- [ ] minimum compilation `make` and `cmake` for both gcc and clang
- [ ] ...
- [ ] table of contents

C++ Best Practices
==================
While catchy title this document is to solidify my knowledge of C++ pecularities and document common issues.

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
*This is a nuanced topic. This section will be a work in progress for some time.*

How come a language can have an undefined behavior (let's shorten to UB)?

C++ has an ISO standard which defines types of compiler freedom. One of the types is called 'undefined behavior' where compilers given freedom decide how to behave.

UB should be avoided since it is not guaranteed to work and may (may not!) fail at run-time (not compile-time!).
For this reason Clang provides [UndefinedBehaviorSanitizer](https://clang.llvm.org/docs/UndefinedBehaviorSanitizer.html) and gcc has -fsanitize=undefined(?).

TODO: some of these examples cause `Segmentation fault` (which is not UB?) so they will be moved to a new section.

Examples of undefined behavior:
- Simple (expected) cases:
    - `NULL` or `nullptr` pointer dereference, or accessing pointer after calling `delete` or `free`
    - Division by zero, or INT32_MIN divided by -1 (see signed integer overflow)
        - since INT32_MAX is 2147483647 and INT32_MIN is -2147483648 so division by -1 will result in overflow
    - Accessing array or memory out of bounds
- More nuanced cases:
    - Use of an uninitialized variables. Very common. Yes, in C++ you should initilize variables.
    - Signed integer overflow is undefined. Unsigned integer is defined to wrap around.
    - Modifying same variable more than once in an expression
- TBD

### How to avoid undefined behavior?
TODO: "Be very careful, use good tools, and hope for the best." John Regehr

*to be continued...*
