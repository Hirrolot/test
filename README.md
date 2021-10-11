# test

 - Each listed identifier in the above grammar corresponds to a macro name defined in `datatype99.h` by default -- these are called _shortened versions_. On the other hand, there are also _postfixed versions_, which are defined by default. If you want to avoid name clashes caused by shortened versions, define `DATATYPE99_NO_ALIASES` before including `datatype99.h`. Library headers are strongly advised to use the postfixed macros, but without resorting to `DATATYPE99_NO_ALIASES`.
