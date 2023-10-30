## Assembler

<!-- https://go.dev/issue/58378 -->

On amd64, frameless nosplit assembly functions are no longer automatically marked as `NOFRAME`.
Instead, the `NOFRAME` attribute must be explicitly specified if desired,
which is already the behavior on other architectures supporting frame pointers.
With this, the runtime now maintains the frame pointers for stack transitions.

<!-- CL 476295 -->

The verifier that checks for incorrect uses of `R15` when dynamic linking on amd64 has been improved.
