## Tools {#tools}

Go 1.21 adds improved support for backwards compatibility and forwards compatibility
in the Go toolchain.

<!-- https://go.dev/issue/56986 -->
To improve backwards compatibility, Go 1.21 formalizes
Go's use of the GODEBUG environment variable to control
the default behavior for changes that are non-breaking according to the
[compatibility policy](/doc/go1compat)
but nonetheless may cause existing programs to break.
(For example, programs that depend on buggy behavior may break
when a bug is fixed, but bug fixes are not considered breaking changes.)
When Go must make this kind of behavior change,
it now chooses between the old and new behavior based on the
`go` line in the workspace's `go.work` file
or else the main module's `go.mod` file.
Upgrading to a new Go toolchain but leaving the `go` line
set to its original (older) Go version preserves the behavior of the older
toolchain.
With this compatibility support, the latest Go toolchain should always
be the best, most secure, implementation of an older version of Go.
See “[Go, Backwards Compatibility, and GODEBUG](/doc/godebug)” for details.

<!-- https://go.dev/issue/57001 -->
To improve forwards compatibility, Go 1.21 now reads the `go` line
in a `go.work` or `go.mod` file as a strict
minimum requirement: `go` `1.21.0` means
that the workspace or module cannot be used with Go 1.20 or with Go 1.21rc1.
This allows projects that depend on fixes made in later versions of Go
to ensure that they are not used with earlier versions.
It also gives better error reporting for projects that make use of new Go features:
when the problem is that a newer Go version is needed,
that problem is reported clearly, instead of attempting to build the code
and printing errors about unresolved imports or syntax errors.

To make these new stricter version requirements easier to manage,
the `go` command can now invoke not just the toolchain
bundled in its own release but also other Go toolchain versions found in the PATH
or downloaded on demand.
If a `go.mod` or `go.work` `go` line
declares a minimum requirement on a newer version of Go, the `go`
command will find and run that version automatically.
The new `toolchain` directive sets a suggested minimum toolchain to use,
which may be newer than the strict `go` minimum.
See “[Go Toolchains](/doc/toolchain)” for details.
