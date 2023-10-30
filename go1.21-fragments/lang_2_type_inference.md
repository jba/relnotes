## Changes to the language

Multiple improvements that increase the power and precision of type inference have been made.

  -     <!-- https://go.dev/issue/59338 -->

    A (possibly partially instantiated generic) function may now be called with arguments that are
    themselves (possibly partially instantiated) generic functions.
    The compiler will attempt to infer the missing type arguments of the callee (as before) and,
    for each argument that is a generic function that is not fully instantiated,
    its missing type arguments (new).
    Typical use cases are calls to generic functions operating on containers
    (such as [slices.IndexFunc](/pkg/slices#IndexFunc)) where a function argument
    may also be generic, and where the type argument of the called function and its arguments
    are inferred from the container type.
    More generally, a generic function may now be used without explicit instantiation when
    it is assigned to a variable or returned as a result value if the type arguments can
    be inferred from the assignment.

  -     <!-- https://go.dev/issue/60353, https://go.dev/issue/57192, https://go.dev/issue/52397, https://go.dev/issue/41176 -->

    Type inference now also considers methods when a value is assigned to an interface:
    type arguments for type parameters used in method signatures may be inferred from
    the corresponding parameter types of matching methods.

  -     <!-- https://go.dev/issue/51593 https://go.dev/issue/39661 -->

    Similarly, since a type argument must implement all the methods of its corresponding constraint,
    the methods of the type argument and constraint are matched which may lead to the inference of
    additional type arguments.

  -     <!-- https://go.dev/issue/58671 -->

    If multiple untyped constant arguments of different kinds (such as an untyped int and
    an untyped floating-point constant) are passed to parameters with the same (not otherwise
    specified) type parameter type, instead of an error, now type inference determines the
    type using the same approach as an operator with untyped constant operands.
    This change brings the types inferred from untyped constant arguments in line with the
    types of constant expressions.

  -     <!-- https://go.dev/issue/59750 -->

    Type inference is now precise when matching corresponding types in assignments:
    component types (such as the elements of slices, or the parameter types in function signatures)
    must be identical (given suitable type arguments) to match, otherwise inference fails.
    This change produces more accurate error messages:
    where in the past type inference may have succeeded incorrectly and lead to an invalid assignment,
    the compiler now reports an inference error if two types can't possibly match.

<!-- https://go.dev/issue/58650 -->
More generally, the description of
[type inference](/ref/spec#Type_inference)
in the language spec has been clarified.
Together, all these changes make type inference more powerful and inference failures less surprising.
