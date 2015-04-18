[Project Home](http://code.google.com/p/psomatlab/)

# Features under development #

## Binary optimization ##
The latest revision of pso on the SVN branch "psodiscrete" is able to solve binary problems. The fitness function needs to be set up to accept vectors (or matrices, if `options.Vectorized` has been set to `'on'`) of 0s and 1s as the input variable. The field `options.PopulationType` needs to be set to `'bitstring'` in order to enable this feature.

### To do before release ###
  * Constraints are to be ignored for now: set up PSO to warn the user if `options.PopulationType` has been set to `'bitstring'` and constraints have been provided.
  * Linear constraints might actually be applicable to PSO, and solvable using `options.ConstrBoundary` set to `'soft'` with little if any modification to the existing code, set up to handle double vectors. But this needs to be further investigated before allowing pso to do its thing on linearly constrained binary problems. For one thing, we'd still need to check whether it's necessary to force the Constraint Boundary behavior to be `'soft'`.

## Parallel Computing ##

Some interest has been expressed regarding adding parallel computing capability to this algorithm. This would be a great addition, but we need somebody who actually has the Parallel Computing Toolbox to test it.

  * The parallel-computing-enabled code must still run without errors or warnings even if the user doesn't have the Parallel Computing Toolbox installed and the option is turned off. This should be a fairly simple check using a few string comparisons and if/else branches.
  * A new SVN branch should probably be started to implement this feature.

[Project Home](http://code.google.com/p/psomatlab/)