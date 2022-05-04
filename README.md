# Assignment 8: Concurrent Sorting

This is the starter code for [Assignment 8](https://course.ccs.neu.edu/cs3650sp22/a08.html).

# Please use the following command before using the make command "find . -exec touch {} \;"

The [Makefile](Makefile) contains the following targets:

- `make all` - compile `msort` and `tmsort`
- `make msort` and `make tmsort` - compile the individual programs
- `make diff-N` - compile and run a diff test, comparing the results of `msort` and `tmsort` on a random input. `N` needs to be replaced by a positive integer. E.g., `make diff-100`.
- `make clean` - perform a minimal clean-up of the source tree
