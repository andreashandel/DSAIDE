# Simulation of a compartmental infectious disease transmission model with 3 types of hosts and intervention

This model allows for the simulation of an ID with 3 types of hosts.
Groups are assumed to be children, adults and elderly. Intervention can
be applied to any of the groups for a certain duration.

## Usage

``` r
simulate_idcontrolmultigroup_ode(
  Sc = 1000,
  Ic = 0,
  Sa = 1000,
  Ia = 1,
  Se = 1000,
  Ie = 0,
  bcc = 3e-04,
  bca = 1e-04,
  bce = 1e-04,
  bac = 1e-04,
  baa = 3e-04,
  bae = 1e-04,
  bec = 1e-04,
  bea = 1e-04,
  bee = 3e-04,
  gc = 0.1,
  ga = 0.1,
  ge = 0.1,
  wc = 0,
  wa = 0,
  we = 0,
  mc = 0.001,
  ma = 0.01,
  me = 0.1,
  f1 = 0,
  T1_start = 50,
  T1_end = 150,
  f2 = 0,
  T2_start = 50,
  T2_end = 150,
  f3 = 0,
  T3_start = 50,
  T3_end = 150,
  tmax = 600
)
```

## Arguments

- Sc:

  : initial number of susceptible children : numeric

- Ic:

  : initial number of infected children : numeric

- Sa:

  : initial number of susceptible adults : numeric

- Ia:

  : initial number of infected adults : numeric

- Se:

  : initial number of susceptible elderly : numeric

- Ie:

  : initial number of infected elderly : numeric

- bcc:

  : rate of transmission to susceptible child from infected child :
  numeric

- bca:

  : rate of transmission to susceptible child from infected adult :
  numeric

- bce:

  : rate of transmission to susceptible child from infected elderly :
  numeric

- bac:

  : rate of transmission to susceptible adult from infected child :
  numeric

- baa:

  : rate of transmission to susceptible adult from infected adult :
  numeric

- bae:

  : rate of transmission to susceptible adult from infected elderly :
  numeric

- bec:

  : rate of transmission to susceptible elderly from infected child :
  numeric

- bea:

  : rate of transmission to susceptible elderly from infected adult :
  numeric

- bee:

  : rate of transmission to susceptible elderly from infected elderly :
  numeric

- gc:

  : rate at which infected children recover or die : numeric

- ga:

  : rate at which infected adults recover or die : numeric

- ge:

  : rate at which infected elderly recover or die : numeric

- wc:

  : rate at which immunity in children wanes : numeric

- wa:

  : rate at which immunity in adults wanes : numeric

- we:

  : rate at which immunity in elderly wanes : numeric

- mc:

  : fraction of infected children who die : numeric

- ma:

  : fraction of infected adults who die : numeric

- me:

  : fraction of infected elderly who die : numeric

- f1:

  : strength of intervention applied to children, between 0 and 1 :
  numeric

- T1_start:

  : start of intervention applied to children : numeric

- T1_end:

  : end of intervention applied to children : numeric

- f2:

  : strength of intervention applied to adults, between 0 and 1 :
  numeric

- T2_start:

  : start of intervention applied to adults : numeric

- T2_end:

  : end of intervention applied to adults : numeric

- f3:

  : strength of intervention applied to elderly, between 0 and 1 :
  numeric

- T3_start:

  : start of intervention applied to elderly : numeric

- T3_end:

  : end of intervention applied to elderly : numeric

- tmax:

  : maximum simulation time : numeric

## Value

This function returns the simulation result as obtained from a call to
the deSolve ode solver.

## Details

A compartmental ID model with several states/compartments is simulated
as a set of ordinary differential equations. The function returns the
output from the odesolver as a matrix, with one column per
compartment/variable. The first column is time. The model implement
basic processes of infection, recovery and death. Waning immunity is
also implemented. Control is applied, which reduces transmission by the
indicated proportion, during times tstart and tend. Control can be
applied at different levels to the different groups.

## Warning

This function does not perform any error checking. So if you try to do
something nonsensical (e.g. any negative values or fractions \> 1), the
code will likely abort with an error message.

## Author

Andreas Handel

## Examples

``` r
  # To run the simulation with default parameters just call the function:
  result <- simulate_idcontrolmultigroup_ode()
```
