HW 1
================
2026-09-24

Calling necessary packages.

``` r
library("tidyverse") #for ggplot
library("palmerpenguins")
```

### Problem 1

Load the penguins dataset.

``` r
data("penguins", package = "palmerpenguins")

str(penguins)
```

In the `penguins` dataset, there are 344 rows and 8 columns of data. One
row corresponds to one penguin. The variables are species, island,
bill_length_mm, bill_depth_mm, flipper_length_mm, body_mass_g, sex,
year. The `species` column lists one of three penguin species for each
individual penguin: Adelie, Chinstrap, and Gintoo. The `island` columns
contains the island of each penguin: Biscoe, Dream, and Torgersen.
`bill_length_mm` contains each penguin’s bill length in mm
`bill_depth_mm` states the bill depth in mm. Both bill length and bill
depth are expressed with decimals. `flipper_length_mm` and `body_mass_g`
both express numeric values that measure the length of a penguin’s
flipper, and the body mass of each penguin respectively. `sex` is a
factor with two levels: “female” and “male”. The `year` column expresses
the year.The mean of `flipper_length_mm` is 200.9152047 mm.

Scatterplot of `flipper_length_mm` and `bill_length_mm`

``` r
penguin_scatter = ggplot(penguins, aes(x=bill_length_mm, y=flipper_length_mm, color = species)) + 
  geom_point(na.rm = TRUE)

penguin_scatter
```

![](HW_1_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

Save plot.

``` r
ggsave("penguin_scatter.pdf", height = 4, width = 6)
```
