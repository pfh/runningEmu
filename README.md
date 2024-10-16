
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
bigM <- 1e6
m <- matrix(rnorm(bigM), nrow=as.integer(sqrt(bigM)))
bench::system_time(un(m))
#> process    real 
#>  17.9ms  17.7ms
v <- sample(1:10, bigM, replace=TRUE)
bench::system_time(deux(v))
#> process    real 
#>   164ms   164ms
vv <- sample(1:10, bigM, replace=TRUE, prob=sample(seq(0.1,0.9,by=0.1), 10, replace = TRUE))
bench::system_time(trois(vv))
#> process    real 
#>  48.8ms  48.7ms
```

And here are the runtimes for 50 evaluations of these functions.

``` r
bench::mark(un(m), iterations = 10)
#> Warning: Some expressions had a GC in every iteration; so filtering is
#> disabled.
#> # A tibble: 1 × 6
#>   expression      min   median `itr/sec` mem_alloc `gc/sec`
#>   <bch:expr> <bch:tm> <bch:tm>     <dbl> <bch:byt>    <dbl>
#> 1 un(m)        19.6ms   23.7ms      37.4    38.4MB     52.3
bench::mark(deux(v), iterations = 10)
#> Warning: Some expressions had a GC in every iteration; so filtering is
#> disabled.
#> # A tibble: 1 × 6
#>   expression      min   median `itr/sec` mem_alloc `gc/sec`
#>   <bch:expr> <bch:tm> <bch:tm>     <dbl> <bch:byt>    <dbl>
#> 1 deux(v)       152ms    162ms      6.13        0B     55.2
bench::mark(trois(vv), iterations = 10)
#> Warning: Some expressions had a GC in every iteration; so filtering is
#> disabled.
#> # A tibble: 1 × 6
#>   expression      min   median `itr/sec` mem_alloc `gc/sec`
#>   <bch:expr> <bch:tm> <bch:tm>     <dbl> <bch:byt>    <dbl>
#> 1 trois(vv)    33.3ms   34.9ms      22.3    61.4MB     55.8
```
