# A helper function which processes and displays the documentation part for each app

This function take the documentation provided as html file and extracts
sections to generate the tabs with content for each Shiny app. This is a
helper function and only useful for this package.

## Usage

``` r
generate_documentation(docfilename)
```

## Arguments

- docfilename:

  full path and name to html file containing the documentation

## Value

tablist A list of tabs for display in a Shiny UI.

## Details

This function is called by the Shiny UIs to populate the documentation
and information tabs.

## Author

Andreas Handel
