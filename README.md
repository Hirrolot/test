# test

Metalang99 is just a set of header files and nothing else; therefore, the only thing you need to tell your compiler is to add `metalang99/include` to include directories.

If you use CMake, the recommended way is [`FetchContent`]:

[`FetchContent`]: https://cmake.org/cmake/help/latest/module/FetchContent.html

```cmake
include(FetchContent)

FetchContent_Declare(
    metalang99
    URL https://github.com/Hirrolot/metalang99/archive/refs/tags/v1.2.3.tar.gz # v1.2.3
)

FetchContent_MakeAvailable(metalang99)

target_link_libraries(MyProject metalang99)

# Metalang99 relies on heavy macro machinery. To avoid useleless macro expansion
# errors, please write this:
if(CMAKE_C_COMPILER_ID STREQUAL "Clang")
  target_compile_options(MyProject PRIVATE -fmacro-backtrace-limit=1)
elseif(CMAKE_C_COMPILER_ID STREQUAL "GNU")
  target_compile_options(MyProject PRIVATE -ftrack-macro-expansion=0)
endif()
```

Another approach is downloading Metalang99 as a [Git submodule]; in this case, you can use CMake's [`add_subdirectory`]. Please, avoid directly copy-pasting `metalang99/include` to your project, because it will complicate updating to new versions of Metalang99 in the future.

[Git submodule]: https://git-scm.com/book/en/v2/Git-Tools-Submodules
[`add_subdirectory`]: https://cmake.org/cmake/help/latest/command/add_subdirectory.html

To reduce compilation times, you can try [precompiling headers] that rely on Metalang99 so that they will not be compiled each time they are included. And **PLEASE**, do not forget to specify [`-ftrack-macro-expansion=0`] (GCC), [`-fmacro-backtrace-limit=1`] (Clang), or something similar to limit macro expansion backtraces; otherwise, Metalang99 will throw your compiler to the moon.

[precompiling headers]: https://en.wikipedia.org/wiki/Precompiled_header
[`-ftrack-macro-expansion=0`]: https://gcc.gnu.org/onlinedocs/gcc/Preprocessor-Options.html
[`-fmacro-backtrace-limit=1`]: https://clang.llvm.org/docs/ClangCommandLineReference.html#cmdoption-clang-fmacro-backtrace-limit

[Tutorial](https://hirrolot.gitbook.io/metalang99/) | [Examples](examples/) | [User documentation](https://metalang99.readthedocs.io/en/latest/)

Happy hacking!
