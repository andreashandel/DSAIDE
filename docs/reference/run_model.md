# A function that runs an app for specific settings and processes results for plot and text generation

This function runs a model based on information provided in the
modelsettings list passed into it.

## Usage

``` r
run_model(modelsettings)
```

## Arguments

- modelsettings:

  a list with model settings. Required list elements are:\
  modelsettings\$simfunction - name of simulation function(s) as
  string.\
  modelsettings\$is_mbmodel - indicate of simulation function has
  mbmodel structure modelsettings\$modeltype - specify what kind of
  model should be run. Currently one of: \_ode\_, \_discrete\_,
  \_stochastic\_, \_usanalysis\_, \_modelexploration\_, \_fit\_.\
  For more than one model type, place \_and\_ between them.\
  modelsettings\$plottype - 'Boxplot' or 'Scatterplot' , required for US
  app\
  Optinal list elements are:\
  List elements with names and values for inputs expected by simulation
  function. If not provided, defaults of simulator function are used.\
  modelsettings\$plotscale - indicate which axis should be on a log
  scale (x, y or both). If not provided or set to ”, no log scales are
  used.\
  modelsettings\$nplots - indicate number of plots that should be
  produced (number of top list elements in result). If not provided, a
  single plot is assumed.\
  modelsettings\$nreps - required for stochastic models to indicate
  numer of repeat simulations. If not provided, a single run will be
  done.\

## Value

A vectored list named "result" with each main list element containing
the simulation results in a dataframe called dat and associated metadata
required for generate_plot and generate_text functions. Most often there
is only one main list entry (result\[\[1\]\]) for a single plot/text.

## Details

This function runs a model for specific settings.
