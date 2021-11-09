# test

A: There is a lot of software written in plain C that can benefit from Datatype99; C is #1 programming language as of 2020, [according to TIOBE](https://jaxenter.com/c-programming-may-2020-171598.html). People use C due to technical and social reasons:

 - Datatype99 can be seamlessly integrated into existing codebases written in pure C -- just `#include <datatype99.h>` and you are ready to go. On the other hand, other languages force you to separate native C files from their sources, which is clearly less convenient.

 - In some environments, developers strick to pure C for historical reasons (e.g., embedded devices, Linux and other operating systems).

 - C has a stable ABI which is vital for some projects (e.g., plugin systems such as [MetaCall]).

 - C is a mature language with a complete specification and a plenitude of libraries. Rust has no specification, and [Zig] is not yet production-ready. I know a few stories when these two languages were rejected for new projects, and I can understand this decision.

 - Historically, C has been targeting nearly all platforms. This is not the case with Rust, which depends on LLVM as for now.

 - Your company obligates you to use C.

 - Etc.

[MetaCall]: https://github.com/metacall/core
[Zig]: https://ziglang.org/

See also:
 - [_Rust is not a good C replacement_](https://drewdevault.com/2019/03/25/Rust-is-not-a-good-C-replacement.html) by Drew DeVault.

Overall, if you can afford a more modern/high-level language, I encourage you to do so instead of using old C. However, many people do not have this possibility (or it would be too costly).
