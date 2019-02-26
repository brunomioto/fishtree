
<!-- README.md is generated from README.Rmd. Please edit that file -->

[![Build
Status](https://travis-ci.com/jonchang/fishtree.svg?token=CAAYReeKsDcnZM7jk2wY&branch=master)](https://travis-ci.com/jonchang/fishtree)
[![CRAN
status](https://www.r-pkg.org/badges/version/fishtree)](https://cran.r-project.org/package=fishtree)

# fishtree

The goal of `fishtree` is to provide an easy interface in R to the Fish
Tree of Life API, to download taxonomies, phylogenies, diversification
rate information, and other data for ray-finned fishes. It should
seamlessly integrate with the rest of the R ecosystem, especially the
package `ape`.

## Example

See a list of taxa available to download.

``` r
library(fishtree)

tax <- fishtree_taxonomy()
head(tax)
#>         rank        name
#> 1      class Actinopteri
#> 2      class   Cladistia
#> 3   subclass Chondrostei
#> 4   subclass Neopterygii
#> 5 infraclass    Holostei
#> 6 infraclass   Teleostei
```

Retrieve a phylogeny for the surgeonfishes and plot the phylogeny and
lineage through time plot.

``` r
library(ape)
phy <- fishtree_phylogeny(rank = "Acanthuridae")
phy
#> 
#> Phylogenetic tree with 67 tips and 66 internal nodes.
#> 
#> Tip labels:
#>  Acanthurus_mata, Acanthurus_blochii, Acanthurus_xanthopterus, Acanthurus_bariene, Acanthurus_dussumieri, Acanthurus_leucocheilus, ...
#> 
#> Rooted; includes branch lengths.
```

``` r
par(mfrow=c(2, 1))
plot(phy, show.tip.label = FALSE)
ltt.plot(phy)
```

You can also check out the vignettes for more detailed examples.

## Installation

You can install the released version of fishtree from
[CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("fishtree")
```

Alternatively, download the development version with devtools:

``` r
devtools::install_github("jonchang/fishtree")
```

## References

The manuscript for this package is currently in review.

## License

The `fishtree` package is licensed under a [2-clause BSD
license](https://opensource.org/licenses/BSD-2-Clause).

## Releasing

    withr::with_envvar(c("NOT_CRAN" = "true"), devtools::release())
