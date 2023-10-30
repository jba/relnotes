## Compiler

Profile-guide optimization (PGO), added as a preview in Go 1.20, is now ready
for general use. PGO enables additional optimizations on code identified as
hot by profiles of production workloads. As mentioned in the
[Go command section](#go-command), PGO is enabled by default for
binaries that contain a `default.pgo` profile in the main
package directory. Performance improvements vary depending on application
behavior, with most programs from a representative set of Go programs seeing
between 2 and 7% improvement from enabling PGO. See the
[PGO user guide](/doc/pgo) for detailed documentation.

<!-- https://go.dev/issue/59959 -->

PGO builds can now devirtualize some interface method calls, adding a
concrete call to the most common callee. This enables further optimization,
such as inlining the callee.

<!-- CL 497455 -->

Go 1.21 improves build speed by up to 6%, largely thanks to building the
compiler itself with PGO.
