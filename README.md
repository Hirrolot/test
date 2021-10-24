# test

Here, `DYN(Num, State, &n)` creates `State` by initialising `State.self` to `&n` and `State.vptr` to the aforementioned `Num_State_impl` (also accessible as [`VTABLE(Num, State)`](#VTABLE)). Eventually, since `State` is polymorphic over its implementations (which is the essence of dynamic dispatch), you can accept `st` as a function parameter and invoke some methods on it:
