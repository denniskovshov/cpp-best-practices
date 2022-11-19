TODO: table of contents

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

## Common issues

### Undefined behavior
*This is a nuanced topic. This section will be a work in progress for some time.*

How come a language can have an undefined behavior (let's shorten to UB)?

C++ has an ISO standard but certain behaviors are not defined in the standard and so compilers decide how to behave in that case.

UB should be avoided since it causes an incorrect program and happens at run-time, not compile time (for this reason Clang provides [UndefinedBehaviorSanitizer](https://clang.llvm.org/docs/UndefinedBehaviorSanitizer.html)).

#### Null pointer dereferencing
TODO

#### Learn more
- https://en.cppreference.com/w/cpp/language/ub

*to be continued...*
