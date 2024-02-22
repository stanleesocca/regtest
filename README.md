
<!-- README.md is generated from README.Rmd. Please edit that file -->

**Note: This is a toy package to demonstrate R package development
workflow.**

# regtest

<!-- badges: start -->
<!-- badges: end -->

The goal of regtest is to streamline the use and manipulation of strings
in R. It is a collection of simple routine to do basic text/character
operation in R.

## Installation

You can install the development version of regtest from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("stanleesocca/regtest")
```

## Example

This is a basic example which shows you how to solve a common string
splitting problem with vector as output is:

``` r
(x <- "alfa,bravo,charlie,delta")
#> [1] "alfa,bravo,charlie,delta"
strsplit(x, split = ",")
#> [[1]]
#> [1] "alfa"    "bravo"   "charlie" "delta"
```

Notice how the return value is a **list** of length one, where the first
element holds the character vector of parts. Often the shape of this
output is inconvenient, i.e. we want the un-listed version.

That’s exactly what `regtest::str_split_one()` does.

``` r
library(regtest)
str_split_one(x, pattern = ",")
#> [1] "alfa"    "bravo"   "charlie" "delta"
```

Use `str_split_one()` when the input is known to be a single string. For
safety, it will error if its input has length greater than one.

`str_split_one()` is built on `stringr::str_split()`, so you can use its
`n` argument and stringr’s general interface for describing the
`pattern` to be matched.

``` r
str_split_one(x, pattern = ",", n = 2)
#> [1] "alfa"                "bravo,charlie,delta"

y <- "192.168.0.1"
str_split_one(y, pattern = stringr::fixed("."))
#> [1] "192" "168" "0"   "1"
```

Don’t take this package seriously.
