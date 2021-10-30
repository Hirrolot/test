# test

[ [`examples/shape.c`](examples/shape.c) ]
```c
#include <interface99.h>

#include <stdio.h>

#define Shape_IFACE                      \
    vfunc( int, perim, const VSelf)      \
    vfunc(void, scale, VSelf, int factor)

interface(Shape);
```

<table>
<tr>
 <td>Rectangle</td>
 <td>Triangle</td>
</tr>
<tr>
<td>

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

</td>
<td>

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

</td>
</tr>
</table>

(Test)
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
