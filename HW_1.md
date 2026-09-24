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

### Problem 2

Creating a new data frame.

``` r
set.seed(123)

df_2 = tibble(
  vec_random = rnorm(10),
  vec_logic = vec_random > 0,
  vec_char = c("a","b","c","d","e","f","g","h","i","j"),
  vec_fact = factor(c("easy","easy","medium","hard","easy","hard","medium","hard","medium","easy"))
)

print(df_2)
```

    ## # A tibble: 10 × 4
    ##    vec_random vec_logic vec_char vec_fact
    ##         <dbl> <lgl>     <chr>    <fct>   
    ##  1    -0.560  FALSE     a        easy    
    ##  2    -0.230  FALSE     b        easy    
    ##  3     1.56   TRUE      c        medium  
    ##  4     0.0705 TRUE      d        hard    
    ##  5     0.129  TRUE      e        easy    
    ##  6     1.72   TRUE      f        hard    
    ##  7     0.461  TRUE      g        medium  
    ##  8    -1.27   FALSE     h        hard    
    ##  9    -0.687  FALSE     i        medium  
    ## 10    -0.446  FALSE     j        easy

Taking the mean of each variable

``` r
mean(pull(df_2, vec_random))
```

    ## [1] 0.07462564

``` r
mean(pull(df_2, vec_logic))
```

    ## [1] 0.5

``` r
mean(pull(df_2, vec_char))
```

    ## Warning in mean.default(pull(df_2, vec_char)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

``` r
mean(pull(df_2, vec_fact))
```

    ## Warning in mean.default(pull(df_2, vec_fact)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

- Taking the mean only works for `vec_random` and `vec_logic`.
  `vec_random` produces numerical values that can be used to take the
  mean. In logical vectors, TRUE and FALSE can be interpreted as 1 for
  TRUE and 0 for FALSE, thus giving us the ability to take the mean.

`as.numeric` to our logical, character, and factor variables.

``` r
as.numeric(pull(df_2, vec_logic))
as.numeric(pull(df_2, vec_char))
as.numeric(pull(df_2, vec_fact))
```

When you convert logic variables to numeric ones, we receive 1’s and 0’s
since TRUE and FALSE logical values care treated as 1 and 0. For factor
variables, the strings inside the vector are assigned integer levels. In
contrast, character variables have no underlying mathematical
meaning.Thus, we can take the means of logical and factor variables, but
not character variables.
