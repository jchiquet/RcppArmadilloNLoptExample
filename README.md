

# RcppArmadilloNLoptExample

I wrote two simple packages trying to access respectively the `C` and `C++` nlopt API. These packages also link to *RcppArmadillo* and *Rcpp* since the ultimate goal is to write some C/C++ code using the features of both Rcpp(Armadillo) and nlopt, to eventually interface this code with R.

These packages require (of course) nlopt installed. For instance, on Linux Ubuntu, try 


```bash
sudo apt-get install libnlopt-dev
```

# nloptC


Interface with the C API of nlopt works just fine through the development version of *nloptr*. It accesses the header of nlopt via the file "nloptrAPI.h". Thus you will need


```r
devtools::install_github("jyypma/nloptr", force = TRUE)
```

In `nloptC/src/nlopt_c.cpp`, I export the function  `test_nlopt_c`, based on the example provided in the NLopt's website:


```r
library(nloptC)
test_nlopt_c()
```

```
## [1] 0.3333333 0.2962963
```

# nloptCpp

Interface with the C++ API of nlopt works independtly of *nloptr*. It accesses the header of nlopt via the file "nloptCpp/inst/include/nloptr.hpp".

The example in now in `nloptCpp/src/nlopt_cpp.cpp`:


```r
library(nloptCpp)
test_nlopt_cpp()
```

```
## $f
## [1] 0.544331
## 
## $x
## [1] 0.3333333 0.2962963
```

