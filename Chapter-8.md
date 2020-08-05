Chapter 8
================
Alyssa Counsell
April 1, 2014

Carmen’s attempt to fix troubled file
<https://r4ds.had.co.nz/tibbles.html>

``` r
library(tidyverse)
```

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.0 --

    ## v ggplot2 3.3.1     v purrr   0.3.4
    ## v tibble  3.0.1     v dplyr   1.0.0
    ## v tidyr   1.1.0     v stringr 1.4.0
    ## v readr   1.3.1     v forcats 0.5.0

    ## Warning: package 'readr' was built
    ## under R version 4.0.2

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
tibble(
    x = 1:5, 
    y = 1, 
    z = x ^ 2 + y
)
```

    ## # A tibble: 5 x 3
    ##       x     y     z
    ##   <int> <dbl> <dbl>
    ## 1     1     1     2
    ## 2     2     1     5
    ## 3     3     1    10
    ## 4     4     1    17
    ## 5     5     1    26

``` r
tribble(
  ~x, ~y, ~z,
  #--|--|----
  "a", 2, 3.6,
  "b", 1, 8.5
)
```

    ## # A tibble: 2 x 3
    ##   x         y     z
    ##   <chr> <dbl> <dbl>
    ## 1 a         2   3.6
    ## 2 b         1   8.5

``` r
tibble(
  a = lubridate::now() + runif(1e3) * 86400,
  b = lubridate::today() + runif(1e3) * 30,
  c = 1:1e3,
  d = runif(1e3),
  e = sample(letters, 1e3, replace = TRUE)
)
```

    ## # A tibble: 1,000 x 5
    ##    a                   b         
    ##    <dttm>              <date>    
    ##  1 2020-08-05 20:49:24 2020-08-21
    ##  2 2020-08-05 10:31:48 2020-08-27
    ##  3 2020-08-05 11:23:54 2020-08-31
    ##  4 2020-08-05 07:18:10 2020-08-25
    ##  5 2020-08-05 16:14:13 2020-08-26
    ##  6 2020-08-05 08:25:41 2020-09-03
    ##  7 2020-08-05 10:33:37 2020-08-27
    ##  8 2020-08-05 05:24:56 2020-08-11
    ##  9 2020-08-05 07:43:01 2020-08-25
    ## 10 2020-08-05 04:09:40 2020-08-17
    ## # ... with 990 more rows, and 3
    ## #   more variables: c <int>,
    ## #   d <dbl>, e <chr>

``` r
nycflights13::flights %>% 
  print(n = 10, width = Inf)
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time
    ##    <int> <int> <int>    <int>
    ##  1  2013     1     1      517
    ##  2  2013     1     1      533
    ##  3  2013     1     1      542
    ##  4  2013     1     1      544
    ##  5  2013     1     1      554
    ##  6  2013     1     1      554
    ##  7  2013     1     1      555
    ##  8  2013     1     1      557
    ##  9  2013     1     1      557
    ## 10  2013     1     1      558
    ##    sched_dep_time dep_delay
    ##             <int>     <dbl>
    ##  1            515         2
    ##  2            529         4
    ##  3            540         2
    ##  4            545        -1
    ##  5            600        -6
    ##  6            558        -4
    ##  7            600        -5
    ##  8            600        -3
    ##  9            600        -3
    ## 10            600        -2
    ##    arr_time sched_arr_time
    ##       <int>          <int>
    ##  1      830            819
    ##  2      850            830
    ##  3      923            850
    ##  4     1004           1022
    ##  5      812            837
    ##  6      740            728
    ##  7      913            854
    ##  8      709            723
    ##  9      838            846
    ## 10      753            745
    ##    arr_delay carrier flight tailnum
    ##        <dbl> <chr>    <int> <chr>  
    ##  1        11 UA        1545 N14228 
    ##  2        20 UA        1714 N24211 
    ##  3        33 AA        1141 N619AA 
    ##  4       -18 B6         725 N804JB 
    ##  5       -25 DL         461 N668DN 
    ##  6        12 UA        1696 N39463 
    ##  7        19 B6         507 N516JB 
    ##  8       -14 EV        5708 N829AS 
    ##  9        -8 B6          79 N593JB 
    ## 10         8 AA         301 N3ALAA 
    ##    origin dest  air_time distance
    ##    <chr>  <chr>    <dbl>    <dbl>
    ##  1 EWR    IAH        227     1400
    ##  2 LGA    IAH        227     1416
    ##  3 JFK    MIA        160     1089
    ##  4 JFK    BQN        183     1576
    ##  5 LGA    ATL        116      762
    ##  6 EWR    ORD        150      719
    ##  7 EWR    FLL        158     1065
    ##  8 LGA    IAD         53      229
    ##  9 JFK    MCO        140      944
    ## 10 LGA    ORD        138      733
    ##     hour minute time_hour          
    ##    <dbl>  <dbl> <dttm>             
    ##  1     5     15 2013-01-01 05:00:00
    ##  2     5     29 2013-01-01 05:00:00
    ##  3     5     40 2013-01-01 05:00:00
    ##  4     5     45 2013-01-01 05:00:00
    ##  5     6      0 2013-01-01 06:00:00
    ##  6     5     58 2013-01-01 05:00:00
    ##  7     6      0 2013-01-01 06:00:00
    ##  8     6      0 2013-01-01 06:00:00
    ##  9     6      0 2013-01-01 06:00:00
    ## 10     6      0 2013-01-01 06:00:00
    ## # ... with 336,766 more rows

``` r
df <- tibble(
  x = runif(5),
  y = rnorm(5)
)

# extracting a vector (single variable/column)
df$x
```

    ## [1] 0.3609653 0.5142207 0.7923352
    ## [4] 0.5763301 0.2727978

``` r
df[["x"]]
```

    ## [1] 0.3609653 0.5142207 0.7923352
    ## [4] 0.5763301 0.2727978

``` r
df[[1]]
```

    ## [1] 0.3609653 0.5142207 0.7923352
    ## [4] 0.5763301 0.2727978

``` r
# extracting using the pipe
df %>% .$x
```

    ## [1] 0.3609653 0.5142207 0.7923352
    ## [4] 0.5763301 0.2727978

``` r
df %>% .[["x"]]
```

    ## [1] 0.3609653 0.5142207 0.7923352
    ## [4] 0.5763301 0.2727978

``` r
# change to regular data frame instead of tibble
as.data.frame(df)
```

    ##           x           y
    ## 1 0.3609653  0.76120850
    ## 2 0.5142207 -0.09171199
    ## 3 0.7923352  1.63207776
    ## 4 0.5763301 -0.41589839
    ## 5 0.2727978  0.30245449

### Exercises 10.5

1.  How can you tell if an object is a tibble? (Hint: try printing
    mtcars, which is a regular data frame).

<!-- end list -->

``` r
# You can use the str() function. mtcars is a data.frame with 32 obs and 11 variables

# diamonds (a tibble) has multiple classes:
# tbl_df, tbl, and data.frame

# If you print diamonds, before providing the first 10 rows, it says "A tibble" followed by the dimensions. Printing mtcars prints the whole dataframe and doesn't give information about it's class or structure. 
```

2.  Compare and contrast the following operations on a data.frame and
    equivalent tibble. What is different? Why might the default data
    frame behaviours cause you frustration?

<!-- end list -->

``` r
# df <- data.frame(abc = 1, xyz = "a")
# df$x
# df[, "xyz"]
# df[, c("abc", "xyz")]
# 
# df2<-tibble(abc = 1, xyz = "a")
# df2$x 
# df2[, "xyz"]
# df2[, c("abc", "xyz")]


# The dataframe takes x as a shorthand for xyz which maybe you didn't want to do. It also makes xyz a factor by automatically converting string data into a factor.
# 
# the tibble throws an error for df$x and preserves the character vector instead of converting to factor.
```

3.  If you have the name of a variable stored in an object, e.g. var \<-
    “mpg”, how can you extract the reference variable from a tibble?
4.  Practice referring to non-syntactic names in the following data
    frame by:

<!-- end list -->

``` r
# annoying <- tibble(
#   `1` = 1:10,
#   `2` = `1` * 2 + rnorm(length(`1`))
# )
# 
# # 1
# annoying$`1`
# 
# #2
# plot(annoying$`1`, annoying$`2`)
# ggplot(annoying, aes(x=`1`, y=`2`))+geom_point()
# 
# #3
# annoying2<-mutate(annoying, 
#                   `3`=`1`/`2`)
# 
# annoying3<-rename(annoying2,
#     three=`3`, one=`1`, two=`2`)


# * Extracting the variable called 1.
# 
# * Plotting a scatterplot of 1 vs 2.
# 
# * Creating a new column called 3 which is 2 divided by 1.
# 
# * Renaming the columns to one, two and three.
```

5.  What does tibble::enframe() do? When might you use it?

<!-- end list -->

``` r
tibble::enframe(c(a = 5, b = 4))
```

    ## # A tibble: 2 x 2
    ##   name  value
    ##   <chr> <dbl>
    ## 1 a         5
    ## 2 b         4

``` r
tibble::enframe(c(a = 5, b = c(4,7)))
```

    ## # A tibble: 3 x 2
    ##   name  value
    ##   <chr> <dbl>
    ## 1 a         5
    ## 2 b1        4
    ## 3 b2        7

``` r
tibble::enframe(list(one = 1, two = 2:3, three = 4:6))
```

    ## # A tibble: 3 x 2
    ##   name  value    
    ##   <chr> <list>   
    ## 1 one   <dbl [1]>
    ## 2 two   <int [2]>
    ## 3 three <int [3]>

``` r
# provides a tibble with the name of the variable as the column variable and the value in a new variable. If a list the value would correspond to the list.
```

6.  What option controls how many additional column names are printed at
    the footer of a tibble?

<!-- end list -->

``` r
# n_extra argument in print function on a tibble

package?tibble
?print.tbl

print(nycflights13::flights, n_extra=5)
```

    ## # A tibble: 336,776 x 19
    ##     year month   day dep_time
    ##    <int> <int> <int>    <int>
    ##  1  2013     1     1      517
    ##  2  2013     1     1      533
    ##  3  2013     1     1      542
    ##  4  2013     1     1      544
    ##  5  2013     1     1      554
    ##  6  2013     1     1      554
    ##  7  2013     1     1      555
    ##  8  2013     1     1      557
    ##  9  2013     1     1      557
    ## 10  2013     1     1      558
    ## # ... with 336,766 more rows, and
    ## #   15 more variables:
    ## #   sched_dep_time <int>,
    ## #   dep_delay <dbl>,
    ## #   arr_time <int>,
    ## #   sched_arr_time <int>,
    ## #   arr_delay <dbl>, ...
