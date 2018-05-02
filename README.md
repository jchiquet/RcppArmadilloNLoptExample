

# RcppArmadilloNLoptExample

I wrote two simple packages trying to access respectively the `C` and `C++` nlopt API. These packages also link to *RcppArmadillo* and *Rcpp* since the ultimate goal is to write some C/C++ code using the features of both Rcpp(Armadillo) and nlopt, to eventually interface this code with R.

# nloptC

Interface with the C API of nlopt works just fine through the development version of *nloptr*. It accesses the header of nlopt via the file "nloptrAPI.h". Thus you will need


```r
devtools::install_github("jyypma/nloptr", force = TRUE)
```

In `nloptC/src/nlopt_c.cpp`, I export the function  `test_nlopt_c`, based on the example provided in the NLopt's website:


```r
library(nloptC)
```

```
## Error in library(nloptC): there is no package called 'nloptC'
```

```r
test_nlopt_c()
```

```
## Error in test_nlopt_c(): could not find function "test_nlopt_c"
```

# nloptCpp

Interface with the C++ API of nlopt works independtly of *nloptr*.  You will need nlopt installed. Hopefully, the configure file will check this for you. Only work on Linux for now.

Installation from source on Linux requires libnlopt 2.4-2. On Debian or Ubuntu use libnlopt-dev:


```bash
sudo apt-get install libnlopt-dev
```

On Fedora we need NLopt-devel:


```bash
sudo yum install NLopt-devel
```

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

