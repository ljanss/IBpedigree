# IBpedigree
Compute pedigree relationships with (fully) inbred founders.

This is a modification of the R package 'pedigree' to allow specifying inbreeding status of individuals, especially
to mark founders as fully inbred. In many plant species it is common to work with founders (and also progeny) that are
fully inbred. Especially when the pedigree includes F1's (which are fully outbred), it is needed to correctly include
full inbreeding status of parents to correctly compute the relationships. An F1 from fully inbred parents has
no Mendelian sampling, and sibling F1's are genetically identical.

From the original pedigree package, only the function makeA() has been modified to allow for an extra argument
inbreeding= to give a vector of the inbreeding levels (0 to 1) for each individual in the pedigree. 
When the inbreeding= argument is omitted, makeA() works as before in the original pedigree package. 
The makeAinv() function is NOT updated and cannot include inbreeding. When the pedigree includes F1's from
fully inbred parents, A becomes singular but can still be computed and used in single-step algorithms, but Ainv
cannot be computed. 

# Installation

To install you need the devtools package. Then download and install:

``` r
library(devtools)
devtools::install_github("ljanss/IBpedigree")
```

# Short manual and example

Many things are still working the same as in the original pedigree package. See .... for the manual of the original.
In this version only the makeA() has been updated. The updated makeA() function now has the arguments:

``` r
makeA(ped, which, inbreeding)
```

Arguments ped and which are as in the original - see the manual for pedigree.
Inbreeding can supply a vector with inbreeding levels for all individuals in the pedigree, if omitted makeA() works
as before in the original pedigree package. The inbreeding levels are fractial numbers from 0-1, but in our plant pedigrees
most are fully inbred (all founders, DH progeny or naturally inbred progeny), exceptions are when an F1 is uncluded (inbreeding 0)
or for instance and F4 from single-seed descent (inbreeding 0.875). 

A file with a small example with 6 individuals is supplied with the package: 3 founders (inbred), 1 F1 (not inbred), and 2 inbred
(for instance DH) progeny. The following code demonstrates makeA() with inbreeding using this example:

