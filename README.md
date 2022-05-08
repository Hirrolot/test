This warning happens when you try to return control from within a `match` statement, and your compiler thinks that not all hypothetical variants are handled. For example:

```c
datatype(MyType, (Foo), (Bar));

int handle(MyType val) {
    match(val) {
        of(Foo) return 5;
        of(Bar) return 7;
    }
}
```

This code may seem perfect at first glance, but in fact, it is not. The reason is this: `match(val)` boils down to `switch(val.tag)` under the hood, with `val.tag` being an ordinary C enumeration consisting of the variants `Foo` and `Bar`. But what if a caller provides us with neither `Foo` nor `Bar`, but with something like `42` (not a valid variant)? Since `enum` is merely an another way to give integers names, a compiler would not complain on the caller site. However, on the callee site we would have the warning:

```
test.c: In function ‘handle’:
test.c:10:1: warning: control reaches end of non-void function [-Wreturn-type]
   10 | }
      | ^
```

The solution is to either panic or return some error-signaling code, like this:

```c
int handle(MyType val) {
    match(val) {
        of(Foo) return 5;
        of(Bar) return 7;
    }

    // Invalid input (no such variant).
    return -1;
}
```

See [issue #9](https://github.com/Hirrolot/datatype99/issues/9).
