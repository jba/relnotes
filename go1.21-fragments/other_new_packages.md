## Core library


### +New slices package {#slices}

<!-- https://go.dev/issue/45955, https://go.dev/issue/54768 -->
<!-- https://go.dev/issue/57348, https://go.dev/issue/57433 -->
<!-- https://go.dev/issue/58565, https://go.dev/issue/60091 -->
<!-- https://go.dev/issue/60546 -->
<!-- CL 467417, CL 468855, CL 483175, CL 496078, CL 498175, CL 502955 -->
The new [slices](/pkg/slices) package provides many common
operations on slices, using generic functions that work with slices
of any element type.

### +New maps package {#maps}

<!-- https://go.dev/issue/57436, CL 464343 -->
The new [maps](/pkg/maps/) package provides several
common operations on maps, using generic functions that work with
maps of any key or element type.

### +New cmp package {#cmp}

<!-- https://go.dev/issue/59488, CL 496356 -->
The new [cmp](/pkg/cmp/) package defines the type
constraint [`Ordered`](/pkg/cmp/#Ordered) and
two new generic functions
[`Less`](/pkg/cmp/#Less)
and [`Compare`](/pkg/cmp/#Compare) that are
useful with [ordered
types](/ref/spec/#Comparison_operators).
