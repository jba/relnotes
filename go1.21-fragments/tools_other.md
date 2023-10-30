## Tools {#tools}

### +Go command {#go-command}

<!-- https://go.dev/issue/58099, CL 474236 -->
The `-pgo` build flag now defaults to `-pgo=auto`,
and the restriction of specifying a single main package on the command
line is now removed. If a file named `default.pgo` is present
in the main package's directory, the `go` command will use
it to enable profile-guided optimization for building the corresponding
program.

The `-C` `dir` flag must now be the first
flag on the command-line when used.

<!-- https://go.dev/issue/37708, CL 463837 -->
The new `go` `test` option
`-fullpath` prints full path names in test log messages,
rather than just base names.

<!-- https://go.dev/issue/15513, CL 466397 -->
The `go` `test` `-c` flag now
supports writing test binaries for multiple packages, each to
`pkg.test` where `pkg` is the package name.
It is an error if more than one test package being compiled has a given package name.

<!-- https://go.dev/issue/15513, CL 466397 -->
The `go` `test` `-o` flag now
accepts a directory argument, in which case test binaries are written to that
directory instead of the current directory.

### +Cgo {#cgo}

<!-- CL 490819 -->
In files that `import "C"`, the Go toolchain now
correctly reports errors for attempts to declare Go methods on C types.
