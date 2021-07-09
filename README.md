
<!-- README.md is generated from README.Rmd. Please edit that file -->

# validatesuggest

<!-- badges: start -->

[![CRAN
status](https://www.r-pkg.org/badges/version/validatesuggest)](https://CRAN.R-project.org/package=validatesuggest)
<!-- badges: end -->

The goal of validatesuggest is to generate suggestions for validation
rules specified with `validate`.

## Installation

And the development version from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("edwindj/validatesuggest")
```

## Example

``` r
library(validate)
library(validatesuggest)

data(retailers, package="validate")
data(SBS2000, package="validate")

# does all
#suggest_rules(retailers)


suggest_range_check(retailers)
#> Object of class 'validator' with 10 elements:
#>  RC1 : size %in% c("sc0", "sc3", "sc1", "sc2")
#>  RC2 : in_range(incl.prob, 0.02, 0.14)
#>  RC3 : in_range(staff, 1, 75)
#>  RC4 : in_range(turnover, 1, 931397)
#>  RC5 : in_range(other.rev, -33, 98350)
#>  RC6 : in_range(total.rev, 25, 931397)
#>  RC7 : in_range(staff.costs, 2, 221302)
#>  RC8 : in_range(total.costs, 22, 2725410)
#>  RC9 : in_range(profit, -222, 225493)
#>  RC10: in_range(vat, 41, 9655)

suggest_na_check(retailers)
#> Object of class 'validator' with 2 elements:
#>  NA1: !is.na(size)
#>  NA2: !is.na(incl.prob)

suggest_unique_check(SBS2000)
#> Object of class 'validator' with 1 elements:
#>  UN1: all_unique(id)

suggest_type_check(retailers)
#> Object of class 'validator' with 10 elements:
#>  TC1 : is.factor(size)
#>  TC2 : is.numeric(incl.prob)
#>  TC3 : is.integer(staff)
#>  TC4 : is.integer(turnover)
#>  TC5 : is.integer(other.rev)
#>  TC6 : is.integer(total.rev)
#>  TC7 : is.integer(staff.costs)
#>  TC8 : is.integer(total.costs)
#>  TC9 : is.integer(profit)
#>  TC10: is.integer(vat)
```
