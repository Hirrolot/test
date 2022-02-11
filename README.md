# test


Datatype99 consists of just one header `datatype99.h` and one dependency [Metalang99]; therefore, you need to add `datatype99` and `metalang99/include` to your include directories.

[Metalang99]: https://github.com/Hirrolot/metalang99

If you use CMake, the recommended way is either [`FetchContent`] or [`add_subdirectory`], e.g.:

[`FetchContent`]: https://cmake.org/cmake/help/latest/module/FetchContent.html

```cmake
include(FetchContent)

FetchContent_Declare(
    datatype99
    URL https://github.com/Hirrolot/datatype99/archive/refs/tags/v1.2.3.tar.gz # v1.2.3
)

FetchContent_MakeAvailable(datatype99)

target_link_libraries(MyProject datatype99)

# Datatype99 relies on heavy macro machinery. To avoid useleless macro expansion
# errors, please write this:
if(CMAKE_C_COMPILER_ID STREQUAL "Clang")
  target_compile_options(MyProject PRIVATE -fmacro-backtrace-limit=1)
elseif(CMAKE_C_COMPILER_ID STREQUAL "GNU")
  target_compile_options(MyProject PRIVATE -ftrack-macro-expansion=0)
endif()
```

Another approach is downloading Datatype99 as a [Git submodule]; in this case, you can use CMake's [`add_subdirectory`]. Please, avoid directly copy-pasting `datatype99.h` to your project, because it will complicate updating to new versions of Datatype99 in the future.

[Git submodule]: https://git-scm.com/book/en/v2/Git-Tools-Submodules
[`add_subdirectory`]: https://cmake.org/cmake/help/latest/command/add_subdirectory.html

To reduce compilation times, you can try [precompiling headers] that rely on Datatype99 so that they will not be compiled each time they are included. And **PLEASE**, do not forget to specify [`-ftrack-macro-expansion=0`] (GCC), [`-fmacro-backtrace-limit=1`] (Clang), or something similar to limit macro expansion backtraces; otherwise, Datatype99 will throw your compiler to the moon.

[precompiling headers]: https://en.wikipedia.org/wiki/Precompiled_header
[`-ftrack-macro-expansion=0`]: https://gcc.gnu.org/onlinedocs/gcc/Preprocessor-Options.html
[`-fmacro-backtrace-limit=1`]: https://clang.llvm.org/docs/ClangCommandLineReference.html#cmdoption-clang-fmacro-backtrace-limit

Note that by default, Datatype99's `CMakeLists.txt` downloads Metalang99 [v1.13.1](https://github.com/Hirrolot/metalang99/releases/tag/v1.13.1) from the GitHub release archives; if you want to override this behaviour, you can do so by invoking [`FetchContent_Declare`] earlier.

[`FetchContent_Declare`]: https://cmake.org/cmake/help/latest/module/FetchContent.html#command:fetchcontent_declare

Happy hacking!
