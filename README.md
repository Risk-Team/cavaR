cavaR
================
2022-11-01

# Introduction

If you had hard times working with several netCDF files and perform
meaningful analysis, especially related to climate change, then this
package might be what you are looking for.

cavaR is the package version of
[CAVA-Analytics](https://github.com/Risk-Team/CAVA-Analytics). It allows
easy loading of cllimate models, both from local data and remotely,
through
[climate4RUDG](https://github.com/SantanderMetGroup/climate4R.UDG).
cavaR can be seen as a wrapper of several packages, but the main engine
for loading and processing climate models is the [climate4R
framework](https://github.com/SantanderMetGroup/climate4R), applied with
a tidyverse approach.

# Installation

The development version of cavaR can be installed directly from github
with:

    library(devtools)
    install_github("Risk-Team/cavaR")

if you encounter problems with dependencies, such as loadeR, downscaleR
and climate4R.indices, follow the following instructions:
[loadeR](https://github.com/SantanderMetGroup/loadeR),
[downscaleR](https://github.com/SantanderMetGroup/downscaleR),
[climate4R.indices](https://github.com/SantanderMetGroup/climate4R.indices)

A conda environment will follow

# A framework to work with climate data and other netCDF files

cavaR makes it easier to work with a large number of climate or impact
model simulations (netCDF files) and perform meaningful analysis. The
idea behind cavaR is to first load the data and then work with the
output of the load_data with other **cavaR** functions.

## 1st step

### Loading data: load_data function

**cavaR** simplifies and standardize how to load multiple climate
models/simulations or other netcdf files (e.g impact models from
ISIMIP). To **load local data**, specify the path to your directories,
containing, for example, several RCPs and a folder with historical runs.

``` r
library(cavaR)

exmp1 <- load_data(country = "Somalia", variable="hurs", years.hist=2000, years.proj=2010,
              path.to.rcps = "~/Databases/CORDEX-CORE/AFR-22", path.to.obs="~/Databases/W5E5")
```

    ## The process is currently parallelized using 9 cores. Type TRUE to continue or set the argument n.cores

``` r
class(exmp1)
```

    ## [1] "list"

``` r
head(exmp1[[1]])
```

    ## # A tibble: 3 x 3
    ##   RCP        models_mbrs      obs             
    ##   <chr>      <list>           <list>          
    ## 1 historical <named list [6]> <named list [4]>
    ## 2 rcp26      <named list [6]> <named list [4]>
    ## 3 rcp85      <named list [6]> <named list [4]>
