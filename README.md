Here, `DYN_LIT(Rectangle, Shape, {5, 7})` creates `Shape` by assigning `Shape.self` to `&(Rectangle){5, 7}` and `Shape.vptr` to the aforementioned `&Rectangle_Shape_impl`. Eventually, you can accept `Shape` as a function parameter and perform dynamic dispatch through the [`VCALL`](#vcall_) macro:
