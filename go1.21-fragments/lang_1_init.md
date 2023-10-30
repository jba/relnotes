## Changes to the language

<!-- https://go.dev/issue/57411 -->
Package initialization order is now specified more precisely. The
new algorithm is:

  - Sort all packages by import path.

  - Repeat until the list of packages is empty:

      - Find the first package in the list for which all imports are
        already initialized.
      - Initialize that package and remove it from the list.

This may change the behavior of some programs that rely on a
specific initialization ordering that was not expressed by explicit
imports. The behavior of such programs was not well defined by the
spec in past releases. The new rule provides an unambiguous definition.
