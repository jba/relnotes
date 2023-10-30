## Linker

<!-- https://go.dev/issue/57302, CL 461749, CL 457455 -->
On windows/amd64, the linker (with help from the compiler) now emits
SEH unwinding data by default, which improves the integration
of Go applications with Windows debuggers and other tools.

<!-- CL 463395, CL 461315 -->

In Go 1.21 the linker (with help from the compiler) is now capable of
deleting dead (unreferenced) global map variables, if the number of
entries in the variable initializer is sufficiently large, and if the
initializer expressions are side-effect free.
