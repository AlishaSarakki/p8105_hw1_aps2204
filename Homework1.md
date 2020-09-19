# p8105_hw1_aps2204
Homework 1
================
Alisha Sarakki (aps2204)
output: github_document

This is my solution to homework 1

``` r
library(tidyverse)
```

    ## ── Attaching packages ───────────────────────────────────────────────────────────────────── tidyverse 1.3.0 ──

    ## ✓ ggplot2 3.3.2     ✓ purrr   0.3.4
    ## ✓ tibble  3.0.3     ✓ dplyr   1.0.2
    ## ✓ tidyr   1.1.2     ✓ stringr 1.4.0
    ## ✓ readr   1.3.1     ✓ forcats 0.5.0

    ## ── Conflicts ──────────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

## problem 1

Create a dataframe with the specified elements

``` r
prob1_df = 
  tibble(
    samp = rnorm(10),
    samp_gt_0 = samp > 0,
    char_vec = c("a","b","c","d","e","f","g","h","i","j"),
    factor_vec = factor(c("low","low","low","mod","mod","mod","mod","high","high","high"))
  )
```

Take the mean of each variable in my data frame

``` r
prob1_df = 
  tibble(
    samp = rnorm(10),
    samp_gt_0 = samp > 0,
    char_vec = c("a","b","c","d","e","f","g","h","i","j"),
    factor_vec = factor(c("low","low","low","mod","mod","mod","mod","high","high","high"))
  )
mean(pull(prob1_df , samp))
```

    ## [1] 0.2320124

``` r
mean(pull(prob1_df , samp_gt_0))
```

    ## [1] 0.6

``` r
mean(pull(prob1_df , char_vec))
```

    ## Warning in mean.default(pull(prob1_df, char_vec)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

``` r
mean(pull(prob1_df , factor_vec))
```

    ## Warning in mean.default(pull(prob1_df, factor_vec)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

I can take the mean of numbers and logical but not character or factor

``` r
as.numeric(pull(prob1_df, samp_gt_0)) * pull(prob1_df, samp)
```

    ##  [1] 0.2118747 0.0000000 0.2091650 0.9764886 0.8203417 1.3290172 0.0000000
    ##  [8] 0.0000000 0.0000000 0.6076222

## problem 2

# describe the penguins data set

``` r
data("penguins", package = "palmerpenguins")
summary(penguins)
```

    ##       species          island    bill_length_mm  bill_depth_mm  
    ##  Adelie   :152   Biscoe   :168   Min.   :32.10   Min.   :13.10  
    ##  Chinstrap: 68   Dream    :124   1st Qu.:39.23   1st Qu.:15.60  
    ##  Gentoo   :124   Torgersen: 52   Median :44.45   Median :17.30  
    ##                                  Mean   :43.92   Mean   :17.15  
    ##                                  3rd Qu.:48.50   3rd Qu.:18.70  
    ##                                  Max.   :59.60   Max.   :21.50  
    ##                                  NA's   :2       NA's   :2      
    ##  flipper_length_mm  body_mass_g       sex           year     
    ##  Min.   :172.0     Min.   :2700   female:165   Min.   :2007  
    ##  1st Qu.:190.0     1st Qu.:3550   male  :168   1st Qu.:2007  
    ##  Median :197.0     Median :4050   NA's  : 11   Median :2008  
    ##  Mean   :200.9     Mean   :4202                Mean   :2008  
    ##  3rd Qu.:213.0     3rd Qu.:4750                3rd Qu.:2009  
    ##  Max.   :231.0     Max.   :6300                Max.   :2009  
    ##  NA's   :2         NA's   :2

This data describes a sample of 344 penguins taken from the islands of
the Palmer Archipelago in Antarctica. Important variables in this data
set include penguin species(Adelie, Chinstrap, and Gentoo), island
location(Biscoe, Dream, Torgersen), bill length(mean length of 43.92mm),
bill depth(mean depth of 17.15mm), flipper length(mean length of
200.9mm), and body mass (mean mass of 4202g). Additional important
descriptive information includes the sex of the penguins sampled (165
female, 168 male), and the years in which the study took place
(2007-2009).

``` r
nrow(penguins)
```

    ## [1] 344

``` r
ncol(penguins)
```

    ## [1] 8

This dataset contains 344 rows and 8 columns. The mean flipper length is
200.9mm.

Below is the plot of bill length(mm) vs. flipper length(mm) of all three
species of sampled penguins.

``` r
penguins_plot =  ggplot(data = penguins, aes(x = bill_length_mm, y = flipper_length_mm, color = species)) + geom_point() + xlab("Bill Length (mm)") + ylab("Flipper Length (mm)")

penguins_plot
```

    ## Warning: Removed 2 rows containing missing values (geom_point).

![](Homework-1_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->
