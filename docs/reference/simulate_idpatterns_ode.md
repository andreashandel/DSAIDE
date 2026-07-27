# Simulation of a compartmental infectious disease transmission model including seasonality

Simulation of a compartmental model with several different compartments:
Susceptibles (S), Infected and Pre-symptomatic (P), Infected and
Asymptomatic (A), Infected and Symptomatic (I), Recovered and Immune (R)
and Dead (D).

This model includes natural births and deaths and waning immunity. It
also allows for seasonal variation in transmission. The model is assumed
to run in units of months. This assumption is hard-coded into the
sinusoidally varying transmission coefficient, which is assumed to have
a period of a year.

## Usage

``` r
simulate_idpatterns_ode(
  S = 1000,
  P = 1,
  bP = 0,
  bA = 0,
  bI = 0.002,
  s = 0,
  gP = 1,
  gA = 1,
  gI = 1,
  f = 0,
  d = 0,
  w = 0,
  n = 0,
  m = 0,
  timeunit = 1,
  tmax = 300
)
```

## Arguments

- S:

  : initial number of susceptible hosts : numeric

- P:

  : initial number of infected, pre-symptomatic hosts : numeric

- bP:

  : level/rate of infectiousness for hosts in the P compartment :
  numeric

- bA:

  : level/rate of infectiousness for hosts in the A compartment :
  numeric

- bI:

  : level/rate of infectiousness for hosts in the I compartment :
  numeric

- s:

  : strength of seasonal/annual sigmoidal variation of transmission rate
  : numeric

- gP:

  : rate at which a person leaves the P compartment : numeric

- gA:

  : rate at which a person leaves the A compartment : numeric

- gI:

  : rate at which a person leaves the I compartment : numeric

- f:

  : fraction of pre-symptomatic individuals that have an asymptomatic
  infection : numeric

- d:

  : fraction of symptomatic infected hosts that die due to disease :
  numeric

- w:

  : rate at which recovered persons lose immunity and return to
  susceptible state : numeric

- n:

  : the rate at which new individuals enter the model (are born) :
  numeric

- m:

  : the rate of natural death (the inverse it the average lifespan) :
  numeric

- timeunit:

  : units of time in which the model should run (1=day, 2=week, 3=month,
  4=year) : numeric

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
something nonsensical (e.g. have I0 \> PopSize or any negative values or
fractions \> 1), the code will likely abort with an error message.

## References

See e.g. Keeling and Rohani 2008 for SIR models and the documentation
for the deSolve package for details on ODE solvers

## See also

The UI of the app, which is part of this package, contains more details
on the model.

## Author

Andreas Handel

## Examples

``` r
  # To run the simulation with default parameters just call the function:
  result <- simulate_idpatterns_ode()
  # To choose parameter values other than the standard one, specify them like such:
  result <- simulate_idpatterns_ode(S = 2000, P = 10, tmax = 100, f = 0.1, d = 0.2, s = 0.1)
  # You should then use the simulation result returned from the function, like this:
  plot(result$ts[ , "time"],result$ts[ , "S"],xlab='Time',ylab='Number Susceptible',type='l')
```
