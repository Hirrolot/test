# test

<div align="center">
<h1>Interface99</h1>
<a href="https://github.com/Hirrolot/interface99/actions">
<img src="https://github.com/Hirrolot/interface99/workflows/C/C++%20CI/badge.svg">
</a>
<a href="https://lists.sr.ht/~hirrolot/metalang99">
<img src="https://img.shields.io/badge/mailing%20list-lists.sr.ht-orange">
</a>

Zero-boilerplate software interfaces inspired by Rust and Golang. Multiple inheritance, superinterfaces, and default implementations supported. No external tools required, pure C99.

<table>
<tr>
<td><b>Shape</b></td>
</tr>

<tr>
<td>
<div align="left">

```c
#include <interface99.h>

#include <stdio.h>

#define Shape_IFACE                      \
    vfunc( int, perim, const VSelf)      \
    vfunc(void, scale, VSelf, int factor)

interface(Shape);
```

</div>
</td>
</tr>
</table>

<table>
<tr>
<td><b>Rectangle</b></td>
<td><b>Triangle</b></td>
</tr>
<tr>
<td>
<div align="left">

```c
typedef struct {
    int a, b;
} Rectangle;

int Rectangle_perim(const VSelf) {
    VSELF(const Rectangle);
    return (self->a + self->b) * 2;
}

void Rectangle_scale(VSelf, int factor) {
    VSELF(Rectangle);
    self->a *= factor;
    self->b *= factor;
}

impl(Shape, Rectangle);
```

</div>
</td>
<td>
<div align="left">

```c
typedef struct {
    int a, b, c;
} Triangle;

int Triangle_perim(const VSelf) {
    VSELF(const Triangle);
    return self->a + self->b + self->c;
}

void Triangle_scale(VSelf, int factor) {
    VSELF(Triangle);
    self->a *= factor;
    self->b *= factor;
    self->c *= factor;
}

impl(Shape, Triangle);
```

</div>
</td>
</tr>
</table>

<table>
<tr>
<td><b>Test</b></td>
</tr>
<tr>
<td>
<div align="left">

```c
void test(Shape shape) {
    printf("perim = %d\n", VCALL(shape, perim));
    VCALL(shape, scale, 5);
    printf("perim = %d\n", VCALL(shape, perim));
}

int main(void) {
    Shape r = DYN(Rectangle, Shape, &(Rectangle){.a = 5, .b = 7});
    Shape t = DYN(Triangle, Shape, &(Triangle){.a = 10, .b = 20, .c = 30});

    test(r);
    test(t);
}
```

</div>
</td>
</tr>
</table>

</div>

(Based on [`examples/shape.c`](examples/shape.c).)
