# Simulation of a compartmental infectious disease transmission model with 2 types of pathogens

This model allows for the simulation of 2 IDs in a single host

## Usage

``` r
simulate_multipathogen_ode(
  S = 1000,
  I1 = 1,
  I2 = 0,
  I12 = 0,
  b1 = 0.001,
  b2 = 0,
  b12 = 0,
  g1 = 0.5,
  g2 = 0.5,
  g12 = 0.5,
  a = 0,
  tmax = 100
)
```

## Arguments

- S:

  : initial number of susceptible hosts : numeric

- I1:

  : initial number of hosts infected with type 1 : numeric

- I2:

  : initial number of hosts infected with type 2 : numeric

- I12:

  : initial number of double infected hosts : numeric

- b1:

  : rate at which type 1 infected hosts transmit : numeric

- b2:

  : rate at which type 2 infected hosts transmit : numeric

- b12:

  : rate at which double infected hosts transmit : numeric

- g1:

  : the rate at which infected type 1 hosts recover : numeric

- g2:

  : the rate at which infected type 2 hosts recover : numeric

- g12:

  : the rate at which double infected hosts recover : numeric

- a:

  : fraction of type 1 infections produced by double infected hosts :
  numeric

- tmax:

  : maximum simulation time, units of months : numeric

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
something nonsensical (e.g. any negative values or fractions \> 1), the
code will likely abort with an error message.

## References

See e.g. Keeling and Rohani 2008 for SIR models and the documentation
for the deSolve package for details on ODE solvers

## See also

The UI of the Shiny app 'Multi-Pathogen Dynamics', which is part of this
package, contains more details on the model

## Author

Andreas Handel and Spencer Hall

## Examples

``` r
  # To run the simulation with default parameters just call the function:
  result <- simulate_multipathogen_ode()
  # To choose parameter values other than the standard one, specify them like such:
  result <- simulate_multipathogen_ode(S = 100, I2 = 10, tmax = 100, b1 = 2.5)
  # You should then use the simulation result returned from the function, like this:
  plot(result$ts[,"time"],result$ts[,"I1"], xlab="Time",ylab="Number Infected Type 1",type="l")
```
