Final_Project
================
Sunday Okechukwu
2022-10-27

Let’s read in our data

``` r
white_df <- read_delim("data/winequality-white.csv")
```

    ## Rows: 4898 Columns: 12
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ";"
    ## dbl (12): fixed acidity, volatile acidity, citric acid, residual sugar, chlo...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
head(white_df)
```

    ## # A tibble: 6 × 12
    ##   `fixed acidity` `volatile acidity` `citric acid` `residual sugar` chlorides
    ##             <dbl>              <dbl>         <dbl>            <dbl>     <dbl>
    ## 1             7                 0.27          0.36             20.7     0.045
    ## 2             6.3               0.3           0.34              1.6     0.049
    ## 3             8.1               0.28          0.4               6.9     0.05 
    ## 4             7.2               0.23          0.32              8.5     0.058
    ## 5             7.2               0.23          0.32              8.5     0.058
    ## 6             8.1               0.28          0.4               6.9     0.05 
    ## # … with 7 more variables: `free sulfur dioxide` <dbl>,
    ## #   `total sulfur dioxide` <dbl>, density <dbl>, pH <dbl>, sulphates <dbl>,
    ## #   alcohol <dbl>, quality <dbl>

``` r
red_df <- read_delim("data/winequality-red.csv")
```

    ## Rows: 1599 Columns: 12
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ";"
    ## dbl (12): fixed acidity, volatile acidity, citric acid, residual sugar, chlo...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
head(red_df)
```

    ## # A tibble: 6 × 12
    ##   `fixed acidity` `volatile acidity` `citric acid` `residual sugar` chlorides
    ##             <dbl>              <dbl>         <dbl>            <dbl>     <dbl>
    ## 1             7.4               0.7           0                 1.9     0.076
    ## 2             7.8               0.88          0                 2.6     0.098
    ## 3             7.8               0.76          0.04              2.3     0.092
    ## 4            11.2               0.28          0.56              1.9     0.075
    ## 5             7.4               0.7           0                 1.9     0.076
    ## 6             7.4               0.66          0                 1.8     0.075
    ## # … with 7 more variables: `free sulfur dioxide` <dbl>,
    ## #   `total sulfur dioxide` <dbl>, density <dbl>, pH <dbl>, sulphates <dbl>,
    ## #   alcohol <dbl>, quality <dbl>

``` r
white_df$color <- rep("White",times= nrow(white_df))
head(white_df)
```

    ## # A tibble: 6 × 13
    ##   `fixed acidity` `volatile acidity` `citric acid` `residual sugar` chlorides
    ##             <dbl>              <dbl>         <dbl>            <dbl>     <dbl>
    ## 1             7                 0.27          0.36             20.7     0.045
    ## 2             6.3               0.3           0.34              1.6     0.049
    ## 3             8.1               0.28          0.4               6.9     0.05 
    ## 4             7.2               0.23          0.32              8.5     0.058
    ## 5             7.2               0.23          0.32              8.5     0.058
    ## 6             8.1               0.28          0.4               6.9     0.05 
    ## # … with 8 more variables: `free sulfur dioxide` <dbl>,
    ## #   `total sulfur dioxide` <dbl>, density <dbl>, pH <dbl>, sulphates <dbl>,
    ## #   alcohol <dbl>, quality <dbl>, color <chr>

``` r
red_df$color <- rep("Red",times= nrow(red_df))
head(red_df)
```

    ## # A tibble: 6 × 13
    ##   `fixed acidity` `volatile acidity` `citric acid` `residual sugar` chlorides
    ##             <dbl>              <dbl>         <dbl>            <dbl>     <dbl>
    ## 1             7.4               0.7           0                 1.9     0.076
    ## 2             7.8               0.88          0                 2.6     0.098
    ## 3             7.8               0.76          0.04              2.3     0.092
    ## 4            11.2               0.28          0.56              1.9     0.075
    ## 5             7.4               0.7           0                 1.9     0.076
    ## 6             7.4               0.66          0                 1.8     0.075
    ## # … with 8 more variables: `free sulfur dioxide` <dbl>,
    ## #   `total sulfur dioxide` <dbl>, density <dbl>, pH <dbl>, sulphates <dbl>,
    ## #   alcohol <dbl>, quality <dbl>, color <chr>

``` r
wine_df <- rbind(white_df, red_df)
head(wine_df)
```

    ## # A tibble: 6 × 13
    ##   `fixed acidity` `volatile acidity` `citric acid` `residual sugar` chlorides
    ##             <dbl>              <dbl>         <dbl>            <dbl>     <dbl>
    ## 1             7                 0.27          0.36             20.7     0.045
    ## 2             6.3               0.3           0.34              1.6     0.049
    ## 3             8.1               0.28          0.4               6.9     0.05 
    ## 4             7.2               0.23          0.32              8.5     0.058
    ## 5             7.2               0.23          0.32              8.5     0.058
    ## 6             8.1               0.28          0.4               6.9     0.05 
    ## # … with 8 more variables: `free sulfur dioxide` <dbl>,
    ## #   `total sulfur dioxide` <dbl>, density <dbl>, pH <dbl>, sulphates <dbl>,
    ## #   alcohol <dbl>, quality <dbl>, color <chr>

``` r
nrow(wine_df)
```

    ## [1] 6497

``` r
colnames(wine_df)
```

    ##  [1] "fixed acidity"        "volatile acidity"     "citric acid"         
    ##  [4] "residual sugar"       "chlorides"            "free sulfur dioxide" 
    ##  [7] "total sulfur dioxide" "density"              "pH"                  
    ## [10] "sulphates"            "alcohol"              "quality"             
    ## [13] "color"

``` r
ncol(wine_df)
```

    ## [1] 13

``` r
# Count the number of NAs
wine_df %>%
  summarise(across(everything(), ~ sum(is.na(.))))
```

    ## # A tibble: 1 × 13
    ##   `fixed acidity` `volatile acidity` `citric acid` `residual sugar` chlorides
    ##             <int>              <int>         <int>            <int>     <int>
    ## 1               0                  0             0                0         0
    ## # … with 8 more variables: `free sulfur dioxide` <int>,
    ## #   `total sulfur dioxide` <int>, density <int>, pH <int>, sulphates <int>,
    ## #   alcohol <int>, quality <int>, color <int>

``` r
# Check for duplicate rows
wine_df %>%
  summarize(dist = nrow(distinct(.)))
```

    ## # A tibble: 1 × 1
    ##    dist
    ##   <int>
    ## 1  5320

``` r
nrow(wine_df)
```

    ## [1] 6497
