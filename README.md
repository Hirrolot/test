# test

A: VS Code automatically enables suggestions of generated types but, of course, it does not support macro syntax highlightment. The sad part is that `VCALL` and its friends break go-to definitions and do not highlight function parameters -- thus, we trade some IDE support for syntax conciseness. We could instead generate wrapper functions `Iface_method(self, ...)` with appropriate signatures, but they would be anyway less expressive than `VCALL` because we could not call superinterface functions using this mechanism.
