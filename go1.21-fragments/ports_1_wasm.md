## Ports

### +WebAssembly {#wasm}

<!-- https://go.dev/issue/38248, https://go.dev/issue/59149, CL 489255 -->
The new `go:wasmimport` directive can now be used in Go programs
to import functions from the WebAssembly host.

<!-- https://go.dev/issue/56100 -->

The Go scheduler now interacts much more efficiently with the
JavaScript event loop, especially in applications that block
frequently on asynchronous events.

### +WebAssembly System Interface {#wasip1}

<!-- https://go.dev/issue/58141 -->
Go 1.21 adds an experimental port to the [
WebAssembly System Interface (WASI)](https://wasi.dev/), Preview 1
(`GOOS=wasip1`, `GOARCH=wasm`).

As a result of the addition of the new `GOOS` value
"`wasip1`", Go files named `*_wasip1.go`
will now be [ignored
by Go tools](/pkg/go/build/#hdr-Build_Constraints) except when that `GOOS` value is being
used.
If you have existing filenames matching that pattern, you will
need to rename them.
