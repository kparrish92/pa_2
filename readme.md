pa\_2
================

``` r
library(tidyverse)
```

    ## Warning: package 'tidyverse' was built under R version 3.6.3

    ## -- Attaching packages -------------------------------------------------------------------------------- tidyverse 1.3.0 --

    ## v ggplot2 3.3.0     v purrr   0.3.3
    ## v tibble  2.1.3     v dplyr   0.8.5
    ## v tidyr   1.0.2     v stringr 1.4.0
    ## v readr   1.3.1     v forcats 0.5.0

    ## Warning: package 'ggplot2' was built under R version 3.6.3

    ## Warning: package 'tidyr' was built under R version 3.6.3

    ## Warning: package 'readr' was built under R version 3.6.3

    ## Warning: package 'purrr' was built under R version 3.6.3

    ## Warning: package 'dplyr' was built under R version 3.6.3

    ## Warning: package 'forcats' was built under R version 3.6.3

    ## -- Conflicts ----------------------------------------------------------------------------------- tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
set_1 = read.csv("data/data.csv")
```

``` r
set_2 = separate(data = set_1, col = info, into = c("verb", "stress"), sep = "-")
```

    ## Warning: Expected 2 pieces. Missing pieces filled with `NA` in 10 rows [1, 2, 3,
    ## 4, 5, 6, 7, 8, 9, 10].

``` r
set_3 <- gather(data = set_2, key = stress, value = quantity, int, durationV, f0)
```

``` r
set_3 %>%
  group_by(stress) %>%
  summarize(mean_duration = mean(quantity))
```

    ## # A tibble: 3 x 2
    ##   stress    mean_duration
    ##   <chr>             <dbl>
    ## 1 durationV         0.113
    ## 2 f0              197.   
    ## 3 int              52.4
