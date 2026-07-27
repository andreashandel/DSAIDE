# A helper function that produces a call to a simulator function for specific settings

This function takes a modelsettings structure and uses that information
to create an unevaluated function call that runs the simulator function
with the specified settings

## Usage

``` r
generate_fctcall(modelsettings)
```

## Arguments

- modelsettings:

  a list with model settings. Required list elements are:\
  List elements with names and values for all inputs expected by
  simulation function.\
  modelsettings\$simfunction - name of simulation function in variable\

## Value

A string containing an unevaluated function call with the specified
settings, or an error message

## Details

This function produces a function call for specific settings.
