Tidying `dadmom`
================
Kejing Li

# Get the data

``` r
# don't modify this chunk unless you still need to install rcfss
# if so, run "devtools::install_github("uc-cfss/rcfss")" in the console first

library(tidyverse)
```

    ## -- Attaching packages --- tidyverse 1.2.1 --

    ## v ggplot2 3.2.1     v purrr   0.3.2
    ## v tibble  2.1.3     v dplyr   0.8.3
    ## v tidyr   1.0.0     v stringr 1.4.0
    ## v readr   1.3.1     v forcats 0.4.0

    ## -- Conflicts ------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(rcfss)

data("dadmom")
dadmom
```

    ## # A tibble: 3 x 5
    ##   famid named  incd namem  incm
    ##   <dbl> <chr> <dbl> <chr> <dbl>
    ## 1     1 Bill  30000 Bess  15000
    ## 2     2 Art   22000 Amy   18000
    ## 3     3 Paul  25000 Pat   50000

# Tidied data

``` r
# write your code to tidy the data here
dadmom %>%
#unite by sex
  unite(mom, namem, incm) %>%
  unite(dad, named, incd) %>%
#put observation in rows
  pivot_longer(cols = -famid,
              names_to = "Sex",
              values_to = "value") %>%
#seperate name and income
  separate(value, into = c("Name", "Income"))
```

    ## # A tibble: 6 x 4
    ##   famid Sex   Name  Income
    ##   <dbl> <chr> <chr> <chr> 
    ## 1     1 dad   Bill  30000 
    ## 2     1 mom   Bess  15000 
    ## 3     2 dad   Art   22000 
    ## 4     2 mom   Amy   18000 
    ## 5     3 dad   Paul  25000 
    ## 6     3 mom   Pat   50000

## Session info

``` r
# don't modify this chunk
devtools::session_info()
```

    ## - Session info ----------------------------------------------------------
    ##  setting  value                       
    ##  version  R version 3.6.1 (2019-07-05)
    ##  os       Windows 10 x64              
    ##  system   x86_64, mingw32             
    ##  ui       RTerm                       
    ##  language (EN)                        
    ##  collate  English_United States.1252  
    ##  ctype    English_United States.1252  
    ##  tz       America/Chicago             
    ##  date     2019-10-20                  
    ## 
    ## - Packages --------------------------------------------------------------
    ##  package     * version date       lib source                        
    ##  assertthat    0.2.1   2019-03-21 [1] CRAN (R 3.6.1)                
    ##  backports     1.1.5   2019-10-02 [1] CRAN (R 3.6.1)                
    ##  broom         0.5.2   2019-04-07 [1] CRAN (R 3.6.1)                
    ##  callr         3.3.2   2019-09-22 [1] CRAN (R 3.6.1)                
    ##  cellranger    1.1.0   2016-07-27 [1] CRAN (R 3.6.1)                
    ##  cli           1.1.0   2019-03-19 [1] CRAN (R 3.6.1)                
    ##  colorspace    1.4-1   2019-03-18 [1] CRAN (R 3.6.1)                
    ##  crayon        1.3.4   2017-09-16 [1] CRAN (R 3.6.1)                
    ##  desc          1.2.0   2018-05-01 [1] CRAN (R 3.6.1)                
    ##  devtools      2.2.1   2019-09-24 [1] CRAN (R 3.6.1)                
    ##  digest        0.6.21  2019-09-20 [1] CRAN (R 3.6.1)                
    ##  dplyr       * 0.8.3   2019-07-04 [1] CRAN (R 3.6.1)                
    ##  ellipsis      0.3.0   2019-09-20 [1] CRAN (R 3.6.1)                
    ##  evaluate      0.14    2019-05-28 [1] CRAN (R 3.6.1)                
    ##  fansi         0.4.0   2018-10-05 [1] CRAN (R 3.6.1)                
    ##  forcats     * 0.4.0   2019-02-17 [1] CRAN (R 3.6.1)                
    ##  fs            1.3.1   2019-05-06 [1] CRAN (R 3.6.1)                
    ##  generics      0.0.2   2018-11-29 [1] CRAN (R 3.6.1)                
    ##  ggplot2     * 3.2.1   2019-08-10 [1] CRAN (R 3.6.1)                
    ##  glue          1.3.1   2019-03-12 [1] CRAN (R 3.6.1)                
    ##  gtable        0.3.0   2019-03-25 [1] CRAN (R 3.6.1)                
    ##  haven         2.1.1   2019-07-04 [1] CRAN (R 3.6.1)                
    ##  hms           0.5.1   2019-08-23 [1] CRAN (R 3.6.1)                
    ##  htmltools     0.3.6   2017-04-28 [1] CRAN (R 3.6.1)                
    ##  httr          1.4.1   2019-08-05 [1] CRAN (R 3.6.1)                
    ##  jsonlite      1.6     2018-12-07 [1] CRAN (R 3.6.1)                
    ##  knitr         1.25    2019-09-18 [1] CRAN (R 3.6.1)                
    ##  lattice       0.20-38 2018-11-04 [1] CRAN (R 3.6.1)                
    ##  lazyeval      0.2.2   2019-03-15 [1] CRAN (R 3.6.1)                
    ##  lifecycle     0.1.0   2019-08-01 [1] CRAN (R 3.6.1)                
    ##  lubridate     1.7.4   2018-04-11 [1] CRAN (R 3.6.1)                
    ##  magrittr      1.5     2014-11-22 [1] CRAN (R 3.6.1)                
    ##  memoise       1.1.0   2017-04-21 [1] CRAN (R 3.6.1)                
    ##  modelr        0.1.5   2019-08-08 [1] CRAN (R 3.6.1)                
    ##  munsell       0.5.0   2018-06-12 [1] CRAN (R 3.6.1)                
    ##  nlme          3.1-140 2019-05-12 [1] CRAN (R 3.6.1)                
    ##  pillar        1.4.2   2019-06-29 [1] CRAN (R 3.6.1)                
    ##  pkgbuild      1.0.5   2019-08-26 [1] CRAN (R 3.6.1)                
    ##  pkgconfig     2.0.3   2019-09-22 [1] CRAN (R 3.6.1)                
    ##  pkgload       1.0.2   2018-10-29 [1] CRAN (R 3.6.1)                
    ##  prettyunits   1.0.2   2015-07-13 [1] CRAN (R 3.6.1)                
    ##  processx      3.4.1   2019-07-18 [1] CRAN (R 3.6.1)                
    ##  ps            1.3.0   2018-12-21 [1] CRAN (R 3.6.1)                
    ##  purrr       * 0.3.2   2019-03-15 [1] CRAN (R 3.6.1)                
    ##  R6            2.4.0   2019-02-14 [1] CRAN (R 3.6.1)                
    ##  rcfss       * 0.1.8   2019-10-05 [1] Github (uc-cfss/rcfss@574608f)
    ##  Rcpp          1.0.2   2019-07-25 [1] CRAN (R 3.6.1)                
    ##  readr       * 1.3.1   2018-12-21 [1] CRAN (R 3.6.1)                
    ##  readxl        1.3.1   2019-03-13 [1] CRAN (R 3.6.1)                
    ##  remotes       2.1.0   2019-06-24 [1] CRAN (R 3.6.1)                
    ##  rlang         0.4.0   2019-06-25 [1] CRAN (R 3.6.1)                
    ##  rmarkdown     1.16    2019-10-01 [1] CRAN (R 3.6.1)                
    ##  rprojroot     1.3-2   2018-01-03 [1] CRAN (R 3.6.1)                
    ##  rstudioapi    0.10    2019-03-19 [1] CRAN (R 3.6.1)                
    ##  rvest         0.3.4   2019-05-15 [1] CRAN (R 3.6.1)                
    ##  scales        1.0.0   2018-08-09 [1] CRAN (R 3.6.1)                
    ##  sessioninfo   1.1.1   2018-11-05 [1] CRAN (R 3.6.1)                
    ##  stringi       1.4.3   2019-03-12 [1] CRAN (R 3.6.0)                
    ##  stringr     * 1.4.0   2019-02-10 [1] CRAN (R 3.6.1)                
    ##  testthat      2.2.1   2019-07-25 [1] CRAN (R 3.6.1)                
    ##  tibble      * 2.1.3   2019-06-06 [1] CRAN (R 3.6.1)                
    ##  tidyr       * 1.0.0   2019-09-11 [1] CRAN (R 3.6.1)                
    ##  tidyselect    0.2.5   2018-10-11 [1] CRAN (R 3.6.1)                
    ##  tidyverse   * 1.2.1   2017-11-14 [1] CRAN (R 3.6.1)                
    ##  usethis       1.5.1   2019-07-04 [1] CRAN (R 3.6.1)                
    ##  utf8          1.1.4   2018-05-24 [1] CRAN (R 3.6.1)                
    ##  vctrs         0.2.0   2019-07-05 [1] CRAN (R 3.6.1)                
    ##  withr         2.1.2   2018-03-15 [1] CRAN (R 3.6.1)                
    ##  xfun          0.10    2019-10-01 [1] CRAN (R 3.6.1)                
    ##  xml2          1.2.2   2019-08-09 [1] CRAN (R 3.6.1)                
    ##  yaml          2.2.0   2018-07-25 [1] CRAN (R 3.6.0)                
    ##  zeallot       0.1.0   2018-01-28 [1] CRAN (R 3.6.1)                
    ## 
    ## [1] D:/Tools/R-3.6.1/library
