# test

 - **Zero-boilerplate.** Forget about maintaining virtual tables -- Interface99 will do it for you!

 - **Portable.** Everything you need is a standard-conforming C99 compiler; neither the standard library, nor compiler/platform-specific functionality or VLA are required.

 - **Predictable.** Interface99 comes with formal [code generation semantics], meaning that the generated data layout is guaranteed to always be the same.

 - **Comprehensible errors.** Interface99 is [resilient to bad code].

 - **Battle-tested.** Datatype99 is used at [OpenIPC] to develop real-time streaming software for IP cameras; this includes an [RTSP 1.0 implementation] along with ~50k lines of private code.

[OpenIPC]: https://openipc.org/
[RTSP 1.0 implementation]: http://example.com/
[code generation semantics]: #semantics
[resilient to bad code]: #q-what-about-compile-time-errors
