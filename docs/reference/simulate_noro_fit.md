# Fitting a simple SIR type model to norovirus outbreak data

This function runs a simulation of a compartment model using a set of
ordinary differential equations. The model describes a simple SIR model
with an additional environmental source of infection The user provides
initial conditions and parameter values for the system. The function
simulates the ODE using an ODE solver from the deSolve package.

## Usage

``` r
simulate_noro_fit(
  S = 100,
  I = 1,
  R = 0,
  b = 0.001,
  blow = 1e-10,
  bhigh = 0.1,
  g = 0.5,
  glow = 0.001,
  ghigh = 100,
  n = 0,
  nlow = 0,
  nhigh = 1000,
  t1 = 8,
  t2 = 15,
  fitmodel = 1,
  iter = 100,
  solvertype = 1
)
```

## Arguments

- S:

  : starting value for Susceptible : numeric

- I:

  : starting value for Infected : numeric

- R:

  : starting value for Recovered : numeric

- b:

  : infection rate : numeric

- blow:

  : lower bound for infection rate : numeric

- bhigh:

  : upper bound for infection rate : numeric

- g:

  : recovery rate : numeric

- glow:

  : lower bound for g : numeric

- ghigh:

  : upper bound for g : numeric

- n:

  : rate of infection from common source : numeric

- nlow:

  : lower bound for n : numeric

- nhigh:

  : upper bound for n : numeric

- t1:

  : start time of infection from common source : numeric

- t2:

  : end time of infection from common source: numeric

- fitmodel:

  : fitting model variant 1, 2 or 3 : numeric

- iter:

  : max number of steps to be taken by optimizer : numeric

- solvertype:

  : the type of solver/optimizer to use (1-3) : numeric

## Value

The function returns a list containing the best fit timeseries, the best
fit parameters, the data and the AICc for the model.

## Details

Three versions of a simple SIR type compartmental ODE model are fit to
cases of norovirus during an outbreak. \#' @section Warning: This
function does not perform any error checking. So if you try to do
something nonsensical (e.g. specify negative parameter or starting
values), the code will likely abort with an error message.

## See also

See the Shiny app documentation corresponding to this function for more
details on this model.

## Author

Andreas Handel

## Examples

``` r
# To run the code with default parameters just call the function:
if (FALSE) result <- simulate_noro_fit() # \dontrun{}
# To apply different settings, provide them to the simulator function, like such:
result <- simulate_noro_fit(iter = 5, fitmodel = 2)
```
