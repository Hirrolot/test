 - **Small.** SmolRTSP is a relatively lightweight library designed to be used in resource-constrained systems (e.g., IP cameras).
 - **Unopinionated.** SmolRTSP does not prescribe contexts in which your code must be executed. You can use it with bare POSIX sockets, [libevent], or any other network framework.
 - **Zero-copy.** SmolRTSP does not allocate or copy data while parsing; instead, it returns [array slices] to a user-supplied string.
 - **Battle-tested.** SmolRTSP is used extensively by [Majestic], an IP camera streamer developed by [OpenIPC].

[libevent]: https://libevent.org/
[array slices]: https://github.com/Hirrolot/slice99
[Majestic]: https://openipc.github.io/wiki/en/majestic-streamer.html
[OpenIPC]: https://openipc.org/
