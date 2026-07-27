# Simulation of a compartmental infectious disease transmission model to study the reproductive number

Simulation of a basic SIR compartmental model with these compartments:
Susceptibles (S), Infected/Infectious (I), Recovered and Immune (R).

The model is assumed to be in units of months when run through the Shiny
App. However as long as all parameters are chosen in the same units, one
can directly call the simulator assuming any time unit.

## Usage

``` r
simulate_idvaccine_ode(
  S = 1000,
  I = 1,
  f = 0,
  e = 0,
  b = 0.01,
  g = 10,
  n = 0,
  m = 0,
  w = 0,
  tmax = 300
)
```

## Arguments

- S:

  : initial number of susceptible hosts : numeric

- I:

  : initial number of infected hosts : numeric

- f:

  : fraction of vaccinated individuals. Those individuals are moved from
  S to R at the beginning of the simulation : numeric

- e:

  : efficacy of vaccine, given as fraction between 0 and 1 : numeric

- b:

  : level/rate of infectiousness for hosts in the I compartment :
  numeric

- g:

  : rate at which a person leaves the I compartment : numeric

- n:

  : the rate at which new individuals enter the model (are born) :
  numeric

- m:

  : the rate of natural death (the inverse it the average lifespan) :
  numeric

- w:

  : rate at which recovered persons lose immunity and return to
  susceptible state : numeric

- tmax:

  : maximum simulation time : numeric

## Value

This function returns the simulation result as obtained from a call to
the deSolve ode solver.

## Details

A compartmental ID model with several states/compartments is simulated
as a set of ordinary differential equations. The function returns the
output from the odesolver as a matrix, with one column per
compartment/variable. The first column is time.

## Warning

This function does not perform any error checking. So if you try to do
something nonsensical (e.g. negative values or fractions \> 1), the code
will likely abort with an error message.

## References

See e.g. Keeling and Rohani 2008 for SIR models and the documentation
for the deSolve package for details on ODE solvers

## See also

The UI of the app contains more details on the model.

## Author

Andreas Handel

## Examples

``` r
  # To run the simulation with default parameters just call the function:
  result <- simulate_idvaccine_ode()
  # To choose parameter values other than the standard one,
  # specify the parameters you want to change, e.g. like such:
  result <- simulate_idvaccine_ode(S = 2000, I = 10, tmax = 100, g = 0.5, n = 0.1)
  # You should then use the simulation result returned from the function, like this:
  plot(result$ts[ , "time"],result$ts[ , "S"],xlab='Time',ylab='Number Susceptible',type='l')
```
