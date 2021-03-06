Cwrap: Wraps C libraries in Go
==============================

Cwrap is a Go wrapper generator for C libraries.

Features
--------
* No Cgo types exposed out of the wrapper package, and uses as less allocation/copy as possible.
* C name prefix mapped to Go packages, and a wrapper package can import another wrapper package.
* Follows Go naming conventions.
* C union.
* Use Go language features when possible:
  * string and bool.
  * Multiple return values.
  * Slice, slice of slice and slice of string.
  * struct with methods. 
  * Go closures as callbacks.
* Stay out of the way when you need to do it manually for specified definitions.

Examples
--------
In the examples directory, there are C libraries that I have successfully applied Cwrap, including:
* GSL (GNU Scientific Library)
* PLplot
* SDL2 (Simple DirectMedia Layer)

You are very welcome to submit examples you think useful to others.

Issue Report
------------
Cwrap may not cover every possible case and fails to come up with a corrresonding Go type or convertion, then the generated code may not be able to compile. When this happens, do the following steps:

1. Comment out the failed function wrappers till it compiles.
2. Add the C names of these failed functions to the excluded list (Package.From.Excluded).
3. Submit the generator example to me. I cannot guarantee anything but I will try to fix critical issues.

TODO
----
* Alignment and padding of generated Go struct fields may need more careful checking (currently no checking is done at all, Cwrap just naively assume the same rules are applied to both Go and C).

Limitations
-----------
* C variadic functions (...) are not supported.

Acknowledgement
---------------
Cwrap uses gccxml (http://gccxml.github.io) to parse C headers to an XML file. Thanks very much for their excellent work.
