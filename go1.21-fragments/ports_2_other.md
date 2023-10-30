## Ports

### +ppc64/ppc64le {#PPC64}

<!-- go.dev/issue/44549 -->
On Linux, `GOPPC64=power10` now generates PC-relative instructions, prefixed
instructions, and other new Power10 instructions. On AIX, `GOPPC64=power10`
generates Power10 instructions, but does not generate PC-relative instructions.

When building position-independent binaries for `GOPPC64=power10`
`GOOS=linux` `GOARCH=ppc64le`, users can expect reduced binary
sizes in most cases, in some cases 3.5%. Position-independent binaries are built for
ppc64le with the following `-buildmode` values:
`c-archive`, `c-shared`, `shared`, `pie`, `plugin`.

### +loong64 {#loong64}

<!-- go.dev/issue/53301, CL 455075, CL 425474, CL 425476, CL 425478, CL 489576 -->
The `linux/loong64` port now supports `-buildmode=c-archive`,
`-buildmode=c-shared` and `-buildmode=pie`.
