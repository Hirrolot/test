# test

## Highlights

 - **Type-safe.** Such things as improperly typed variants, non-exhaustive pattern matching, and invalid field access are caught at compile-time.

 - **Portable.** Everything you need is a standard-conforming C99 compiler; neither the standard library, nor compiler/platform-specific functionality or VLA are required.

 - **Predictable.** Datatype99 comes with formal [code generation semantics], meaning that the generated data layout is guaranteed to always be the same.

 - **Comprehensible errors.** Datatype99 is [resilient to bad code].

 - **Battle-tested.** Datatype99 is used at [OpenIPC] to develop real-time streaming software for IP cameras; this includes an [RTSP 1.0 implementation] along with ~50k lines of private code.

[resilient to bad code]: #q-what-about-compile-time-errors
[OpenIPC]: https://openipc.org/
[RTSP 1.0 implementation]: http://example.com/
