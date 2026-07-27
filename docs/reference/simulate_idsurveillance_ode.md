# Simulation of a compartmental infectious disease transmission model illustrating the impact of ID surveillance

This model allows for the exploration of the impact of ID surveillance
on transmission dynamics

## Usage

``` r
simulate_idsurveillance_ode(
  S = 1000,
  P = 1,
  tmax = 200,
  bP = 0,
  bA = 0,
  bI = 0.001,
  gP = 0.5,
  f = 0,
  d = 0,
  w = 0,
  m = 0,
  n = 0,
  rP = 0,
  rA = 0,
  rI = 0.5
)
```

## Arguments

- S:

  : initial number of susceptible hosts : numeric

- P:

  : initial number of infected pre-symptomatic hosts : numeric

- tmax:

  : maximum simulation time : numeric

- bP:

  : rate of transmission from presymptomatic to susceptible host :
  numeric

- bA:

  : rate of transmission from asymptomatic to susceptible host : numeric

- bI:

  : rate of transmission from symptomatic to susceptible host : numeric

- gP:

  : the rate at which presymptomatic hosts move to the next stage :
  numeric

- f:

  : fraction of asymptomatic hosts : numeric

- d:

  : rate at which infected hosts die : numeric

- w:

  : the rate at which host immunity wanes : numeric

- m:

  : the rate of births : numeric

- n:

  : the rate of natural deaths : numeric

- rP:

  : rate of pre-symptomatic host removal due to surveillance : numeric

- rA:

  : rate of asymptomatic host removal due to surveillance : numeric

- rI:

  : rate of symptomatic host removal due to surveillance : numeric

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

## See also

The UI of the app 'Parasite Model', which is part of the DSAIDE package,
contains more details.

## Author

Andreas Handel, Ronald Galiwango

## Examples

``` r
  # To run the simulation with default parameters just call the function:
  result <- simulate_idsurveillance_ode()
  # To choose parameter values other than the standard one, 
  # specify the parameters you want to change, e.g. like such:
  result <- simulate_idsurveillance_ode(S = 2000, tmax = 100, f = 0.5)
  # You should then use the simulation result returned from the function, like this:
  plot(result$ts[ , "time"],result$ts[ , "S"],xlab='Time',ylab='Number Susceptible',type='l')
```
