# IBpedigree
Compute pedigree relationships with (fully) inbred founders

This is a modification of the R package 'pedigree' to easily specify inbreeding status of individuals, especially
to mark founders as fully inbred. This is common in many plant species that work with fully inbred individuals.
From the original pedigree package, only the function makeA() has been modified to allow for an extra argument
inbreeding= to give a vector of the inbreeding levels (0 to 1) or each individual in the pedigree. 
When the inbreeding= argument is omitted, makeA() works as before in the original pedigree package. 
The makeAinv() function is NOT updated and cannot include inbreeding.



