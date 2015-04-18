# PSO #
Find the minimum of a function using Particle Swarm Optimization.

# Syntax #
```
psodemo
pso
x = pso(fitnessfcn,nvars)
x = pso(fitnessfcn,nvars,Aineq,bineq)
x = pso(fitnessfcn,nvars,Aineq,bineq,Aeq,beq)
x = pso(fitnessfcn,nvars,Aineq,bineq,Aeq,beq,LB,UB)
x = pso(fitnessfcn,nvars,Aineq,bineq,Aeq,beq,LB,UB,nonlcon)
x = pso(fitnessfcn,nvars,Aineq,bineq,Aeq,beq,LB,UB,nonlcon,options)
x = pso(problem)
[x, fval] = pso(...)
[x, fval,exitflag] = pso(...)
[x, fval,exitflag,output] = pso(...)
[x, fval,exitflag,output,population] = pso(...)
[x, fval,exitflag,output,population,scores] = pso(...)
```

# Description #
`psodemo`

Runs a demonstration of the PSO algorithm using test function specified
by user.

`pso`

Runs a default demonstration using Rosenbrock's banana function.

`x = pso(fitnessfcn,nvars)`

Runs the particle swarm algorithm with no constraints and default
options. fitnessfcn is a function handle, nvars is the number of
parameters to be optimized, i.e. the dimensionality of the problem.

`x = pso(fitnessfcn,nvars,Aineq,bineq)`

Linear constraints, such that Aineq\*x <= bineq. Soft boundaries only.
Aineq is a matrix of size nconstraints x nvars, while b is a column
vector of length nvars.

`x = pso(fitnessfcn,nvars,Aineq,bineq,Aeq,beq)`

Linear equality constraints, such that Aeq\*x = beq. If no inequality constraints exist, set Aineq and bineq to [.md](.md).

`x = pso(fitnessfcn,nvars,Aineq,bineq,Aeq,beq,LB,UB)`

Lower and upper bounds definted as LB and UB respectively. Use empty
arrays [.md](.md) for A, b, Aeq, or beq if no linear constraints exist.

`x = pso(fitnessfcn,nvars,Aineq,bineq,Aeq,beq,LB,UB,nonlcon)`

Non-linear constraints. Nonlinear inequality constraints in the form c(x)
<= 0 have now been implemented using 'soft' boundaries only. See the
Optimization Toolbox documentation for the proper syntax for defining
nonlinear constraints.

`x = pso(fitnessfcn,nvars,Aineq,bineq,Aeq,beq,LB,UB,nonlcon,options)`

Default algorithm parameters replaced with those defined in the options
structure:
Use `>> options = psooptimset('Param1,'value1','Param2,'value2',...)` to
generate the options structure. Type `>> psooptimset` with no input or
output arguments to display a list of available options and their
default values.

NOTE: the swarm will perform better if the `PopInitRange` option is defined
so that it closely bounds the expected domain of the feasible region.
This is automatically done for lower and upper bound constraints, but not
for linear and nonlinear constraints.

NOTE 2: If `options.HybridFcn` is to be defined, and if it is necessary to
pass a non-default options structure to the hybrid function, then the
options structure may be included in a cell array along with the pointer
to the hybrid function. Example:
```
>> % Let's say that we want to use fmincon to refine the result from PSO:
>> hybridoptions = optimset(@fmincon) ;
>> options.HybridFcn = {@fmincon, hybridoptions} ;
```

`x = pso(problem)`

Parameters imported from problem structure. Should work, but no error
checking yet.

`[x, fval] = pso(...)`

Returns the fitness value of the best solution.

`[x, fval,exitflag] = pso(...)`

Returns information on outcome of pso run. Should match `exitflag` values
for GA where applicable, for code reuseability.

`[x, fval,exitflag,output] = pso(...)`

The structure output contains more detailed information about the PSO
run. Should match output fields of GA, where applicable.

`[x, fval,exitflag,output,population] = pso(...)`
A matrix population of size PopulationSize x nvars, with the locations of
particles across the rows.

`[x, fval,exitflag,output,population,scores] = pso(...)`
Final scores of the particles in population.

See also:
[PSODEMO](docPSODEMO.md), [PSOOPTIMSET](docPSOOPTIMSET.md).