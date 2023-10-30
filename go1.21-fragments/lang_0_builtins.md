## Changes to the language

Go 1.21 adds three new built-ins to the language.

  -     <!-- https://go.dev/issue/59488 -->

    The new functions `min` and `max` compute the
    smallest (or largest, for `max`) value of a fixed number
    of given arguments.
    See the language spec for
    [details](/ref/spec#Min_and_max).

  -     <!-- https://go.dev/issue/56351 -->

    The new function `clear` deletes all elements from a
    map or zeroes all elements of a slice.
    See the language spec for
    [details](/ref/spec#Clear).
