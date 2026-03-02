Lab 07 - Conveying the right message through visualisation
================
George Nesbitt
2/24/2026

### Load packages and data

``` r
library(tidyverse)
library(dplyr)
```

``` r
kansas <- read_csv("/Users/georgenesbitt/Desktop/Data Science/Labs/lab_07_datascience/kansas_grouped_rolling_avg.csv")
```

    ## Rows: 46 Columns: 3
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (1): mask_mandate
    ## dbl  (1): rolling_avg
    ## date (1): date
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

### Exercise 1

``` r
ggplot(kansas, aes(x = date, 
                   y = rolling_avg, 
                   color = mask_mandate)) +
  geom_line() +
  scale_color_manual(values = c("Mask" = "orange",
                                "No Mask" = "blue")) +
  labs(
    title = "Kansas COVID-19 7-Day Rolling Average of Daily Cases Per 100K Population",
    subtitle = "Mask Counties vs. No-Mask Mandate Counties",
    caption = "Source: Kansas Department of Health and Environment",
    x = NULL,
    y = "Cases per 100K Population",
    color = NULL)
```

![](lab-07_files/figure-gfm/recreation%20of%20misleading%20graph-1.png)<!-- -->

Below is the misleading graph: \### Excercise 2

``` r
ggplot(kansas, aes(x = date, 
                   y = rolling_avg, 
                   color = mask_mandate)) +
  geom_line() +
  scale_color_manual(values = c("Mask" = "orange",
                                "No Mask" = "blue")) +
  labs(
    title = "Kansas COVID-19 7-Day Rolling Average of Daily Cases Per 100K Population",
    subtitle = "Mask Counties vs. No-Mask Mandate Counties",
    caption = "Source: Kansas Department of Health and Environment",
    x = NULL,
    y = "Cases per 100K Population",
    color = NULL)
```

![](lab-07_files/figure-gfm/new%20less%20misleading%20graph-1.png)<!-- -->
\### Exercise 3 The message that is more clear in this graph than in the
misleading one is the comparison of the dependent variable across mask
conditions. Initially, it made the two look similar, however after
equalizing the dependent variable along the y axis, you can see that
mask counties had drastically higher numbers of cases.

### Excercise 4

What this graph tells us (without any other context whatsoever) is that
counties that have mask mandates also tend to have a higher number of
covid cases. This does not reflect on what I know about mask wearing,
however if you consider many factors, this might be due to that fact
that counties with higher population density might also be more likely
to have mask mandates in general.

### Excercise 5

As I stated above, what likely contributes to this trend is that liberal
cities typically have higher population densities and also typically
have larger/more strict mask mandates. The lack of mask mandates in more
rural areas with much lower population density is likely not enough to
allow more covid cases.
