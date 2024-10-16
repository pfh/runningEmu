
<!-- README.md is generated from README.Rmd. Please edit that file -->

# runningEmu

<!-- badges: start -->
<!-- badges: end -->

``` r
library(runningEmu)
```

The goal of runningEmu is to create an environment for a Hacky Hour
competition

## Example

There are 3 functions to be optimized in this package.

Below are the runtimes for one evaluation of these functions

``` r
m <- matrix(rnorm(1e8), nrow=1e4)
bench::system_time(un(m))
#> process    real 
#>   2.22s   2.69s
bench::system_time(deux())
#> process    real 
#>    23µs  23.4µs
bench::system_time(trois())
#> process    real 
#>     9µs  9.47µs
```

And here are the runtimes for 50 evaluations of these functions.

``` r
bench::mark(un(m), iterations = 50)
#> Warning: Some expressions had a GC in every iteration; so filtering is
#> disabled.
#> # A tibble: 1 × 6
#>   expression      min   median `itr/sec` mem_alloc `gc/sec`
#>   <bch:expr> <bch:tm> <bch:tm>     <dbl> <bch:byt>    <dbl>
#> 1 un(m)         1.79s    2.25s     0.416    3.73GB     1.92
bench::mark(deux(), iterations = 50)
#> # A tibble: 1 × 6
#>   expression      min   median `itr/sec` mem_alloc `gc/sec`
#>   <bch:expr> <bch:tm> <bch:tm>     <dbl> <bch:byt>    <dbl>
#> 1 deux()         41ns     41ns 13858086.        0B        0
bench::mark(trois(), iterations = 50)
#> # A tibble: 1 × 6
#>   expression      min   median `itr/sec` mem_alloc `gc/sec`
#>   <bch:expr> <bch:tm> <bch:tm>     <dbl> <bch:byt>    <dbl>
#> 1 trois()           0     41ns 10888513.        0B        0
```
