Lab 02 - Plastic waste
================
Insert your name here
Insert date here

## Load packages and data

``` r
library(tidyverse) 
```

``` r
plastic_waste <- read.csv("data/plastic-waste.csv")
```

## Exercises

### Exercise 1

From the graph, it looks like that African has the lowest plastic waste
per capical on average. The distribution of plastic waste per capital
for North America has the greatest variation.

``` r
ggplot(data = plastic_waste, aes(x = plastic_waste_per_cap)) +
 geom_histogram(binwidth = 0.2) +
 labs (x="plastic_waste_per_captical", y="count", title="graph 1.1") +
 facet_wrap(~continent, nrow=7)
```

    ## Warning: Removed 51 rows containing non-finite values (`stat_bin()`).

![](lab-02_files/figure-gfm/plastic-waste-continent-1.png)<!-- -->


    ### Exercise 2


    ```r
    ggplot(data = plastic_waste, 
         mapping = aes(x = plastic_waste_per_cap, 
                      color = continent, 
                      fill = continent)) +
      geom_density(alpha = 0.3)

    ## Warning: Removed 51 rows containing non-finite values (`stat_density()`).

![](lab-02_files/figure-gfm/plastic-waste-density-1.png)<!-- -->

### Exercise 3

Color and the fill can be specified by the name of the color, like
“red”. but the alpha refers to the transparency of all the colors that
is presented in the graph.

### Exercise 4

violin plots also shows the density of each category. The botplots
emphasize some extreme values which can not be directly seen in the
violin plots.

``` r
ggplot(data = plastic_waste, 
      mapping = aes(x = continent, 
                    y = plastic_waste_per_cap)) +
    geom_violin()
```

    ## Warning: Removed 51 rows containing non-finite values (`stat_ydensity()`).

![](lab-02_files/figure-gfm/plastic-waste-violin-1.png)<!-- -->

``` r
ggplot(data = plastic_waste, 
      mapping = aes(x = continent, 
                    y = plastic_waste_per_cap)) +
   geom_boxplot()
```

    ## Warning: Removed 51 rows containing non-finite values (`stat_boxplot()`).

![](lab-02_files/figure-gfm/plastic-waste-violin-2.png)<!-- -->

### Exercise 5

4.1. a slight positive correlation between mismanaged waste per capital
and waste per capital.

``` r
 ggplot(data = plastic_waste, 
       mapping = aes(x = mismanaged_plastic_waste_per_cap,
                     y = plastic_waste_per_cap)) +
    geom_point()
```

    ## Warning: Removed 51 rows containing missing values (`geom_point()`).

![](lab-02_files/figure-gfm/plastic-waste-mismanaged-1.png)<!-- -->

### Exercise 6

4.2. It helps to visualize difference among continents and distinguish
the correlation for each continent, but the points are still very
concentrated and hard to look at.

``` r
ggplot(data = plastic_waste, 
       mapping = aes(x = mismanaged_plastic_waste_per_cap, 
       y = plastic_waste_per_cap,color = continent,fill = continent)) +
   geom_point()
```

    ## Warning: Removed 51 rows containing missing values (`geom_point()`).

![](lab-02_files/figure-gfm/plastic-waste-mismanaged-continent-1.png)<!-- -->

### Exercise 7

coastal population has slightly negative relationship with plastic waste
per capital. Total population and plastic waste per capital has weaker
associations in general. None of the pairs of variables appear to be
storngly linearly associated.

``` r
 ggplot(data = plastic_waste, 
        mapping = aes(x = total_pop, 
                     y = plastic_waste_per_cap,color = continent,fill = continent)) +
                     geom_point()
```

    ## Warning: Removed 61 rows containing missing values (`geom_point()`).

![](lab-02_files/figure-gfm/plastic-waste-population-total-1.png)<!-- -->

``` r
ggplot(data = plastic_waste, 
      mapping = aes(x = coastal_pop, 
                     y = plastic_waste_per_cap, color = continent,fill = continent)) +
   geom_point()
```

    ## Warning: Removed 51 rows containing missing values (`geom_point()`).

![](lab-02_files/figure-gfm/plastic-waste-population-coastal-1.png)<!-- -->

### Exercise 8

Remove this text, and add your answer for Exercise 8 here.

``` r
# insert code here
```

## Pro-Tips

### Excercise 3

Try this :D

ggplot(data = plastic_waste, mapping = aes(x = continent, y =
plastic_waste_per_cap)) + geom_violin()+ geom_boxplot(width=.3,
fill=“green”) + stat_summary(fun.y=median, geom=“point”)

### Exercise 5

Helpful
reference:<http://www.sthda.com/english/wiki/ggplot2-themes-and-background-colors-the-3-elements>
