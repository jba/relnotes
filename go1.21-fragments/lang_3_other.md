## Changes to the language

<!-- https://go.dev/issue/57969 -->

Go 1.21 includes a preview of a language change we are considering for a future version of Go:
making for loop variables per-iteration instead of per-loop, to avoid accidental sharing bugs.
For details about how to try that language change, see [the LoopvarExperiment wiki page](https://go.dev/wiki/LoopvarExperiment).

<!-- https://go.dev/issue/25448 -->

Go 1.21 now defines that if a goroutine is panicking and recover was called directly by a deferred
function, the return value of recover is guaranteed not to be nil. To ensure this, calling panic
with a nil interface value (or an untyped nil) causes a run-time panic of type
[`*runtime.PanicNilError`](/pkg/runtime/#PanicNilError).

To support programs written for older versions of Go, nil panics can be re-enabled by setting
`GODEBUG=panicnil=1`.
This setting is enabled automatically when compiling a program whose main package
is in a module that declares `go` `1.20` or earlier.
