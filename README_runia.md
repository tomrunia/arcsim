# Installation

After running `make` in `dependencies` you need to update the file: `/dependencies/include/taucs.h`. Comment out the following definitions:

```
#ifndef isnan
// Runia, 2019-04: line disabled because compiler error
//extern int isnan(double);
#endif

//...

#ifndef isinf
// Runia, 2019-04: line disabled because compiler error
//extern int isinf(double);
#endif

```

# JSON problem

`Expected value to be of type array, but found Null instead.` ==> Solve by adding a `motions` field to the JSON. 