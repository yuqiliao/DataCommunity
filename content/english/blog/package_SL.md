---
author: "Sifan Liu"
date: 2018-10-31
linktitle: metro.data
title: Introducing the metro.data R package
highlight: false
image: images/blog/R package logo.png
showonlyimage: false
---
# metro.data

`metro.data` is an R package for working with US Census geographic data. The built-in datasets include latest geographic reference files between census places, counties, metropolitan areas, and states, with population data from 2018 ACS 1-year estimates and employment data from CBP 2018 estimates.

## Installation

You can install the version in development of metro.data frlom Github with: 

``` r
devtools::install_github("BrookingsInstitution/metro-data-warehouse")
library(metro.data)
```


## Datasets

### Relationship file of Census county, metro areas, and state
Source is U.S. Census Bureau's [delineation files](https://www.census.gov/geographies/reference-files/time-series/demo/metro-micro/delineation-files.html). We use population data from ACS 1-year 2018 survey and employment data from County Business Patterns (2017).
``` r
head(county_cbsa_st)


# A tibble: 6 x 15
  stco_code co_name co_pop co_emp co_pcturban co_type st_fips st_name st_emp cbsa_code cbsa_name
  <chr>     <chr>    <dbl>  <dbl>       <dbl> <fct>   <chr>   <chr>    <dbl> <chr>     <chr>    
1 01099     Monroe~  21745   5400       21.0  rural ~ 01      Alabama 1.61e6 NA        NA       
2 01079     Lawren~  33288   3138        8.71 small ~ 01      Alabama 1.61e6 19460     Decatur,~
3 01081     Lee Co~ 156597  43945       72.6  small ~ 01      Alabama 1.61e6 12220     Auburn-O~
4 01093     Marion~  30058   7656       11.2  rural ~ 01      Alabama 1.61e6 NA        NA       
5 01107     Picken~  20170   2639        0    small ~ 01      Alabama 1.61e6 46220     Tuscaloo~
6 01119     Sumter~  13084   2991        0    rural ~ 01      Alabama 1.61e6 NA        NA       
# ... with 4 more variables: cbsa_type <fct>, cbsa_pop <dbl>, cbsa_emp <dbl>, cbsa_size <fct>
```
### Census place to county crosswalk
Crosswalk is generated using [GEOCORR 2018](http://mcdc.missouri.edu/applications/geocorr2018.html) from Missouri Census Data Center
``` r
head(place2county)
  stpl_fips stco_fips st_fips st_ab             pl_name      co_name  pl_pop16 afact1 afact2
1   0100100     01017      01    AL      Abanda CDP, AL  Chambers AL   189.912      1  0.006
2   0100124     01067      01    AL  Abbeville city, AL     Henry AL  2666.561      1  0.155
3   0100460     01073      01    AL Adamsville city, AL Jefferson AL  4529.245      1  0.007
4   0100484     01133      01    AL    Addison town, AL   Winston AL   736.979      1  0.031
5   0100676     01065      01    AL      Akron town, AL      Hale AL   337.748      1  0.023
6   0100820     01117      01    AL  Alabaster city, AL    Shelby AL 32769.300      1  0.156

``` 

## Functions

### find the cbsa_code using metro name keywords

```r
metro.data::find_cbsa_code("portland")

# A tibble: 2 x 2
  cbsa_code cbsa_name                          
  <chr>     <chr>                              
1 38900     Portland-Vancouver-Hillsboro, OR-WA
2 38860     Portland-South Portland, ME   

```

### find all the counties located in the metros using metro name keywords

```r
metro.data::find_cbsa_counties("denver") 

# A tibble: 10 x 6
   stco_code stco_name                    co_pop co_emp co_pcturban co_type       
   <chr>     <chr>                         <dbl>  <dbl>       <dbl> <fct>         
 1 08031     Denver County, Colorado      693417 444646       100   Urban cores   
 2 08047     Gilpin County, Colorado        5924   4885         0   Exurbs        
 3 08059     Jefferson County, Colorado   570427 198024        93.1 Mature suburbs
 4 08001     Adams County, Colorado       497115 173553        96.4 Urban cores   
 5 08019     Clear Creek County, Colorado   9379   2961         0   Exurbs        
 6 08093     Park County, Colorado         17392   1467         0   Exurbs        
 7 08005     Arapahoe County, Colorado    636671 293379        98.4 Urban cores   
 8 08014     Broomfield County, Colorado   66120  46084        99.4 Urban cores   
 9 08035     Douglas County, Colorado     328614 112808        89.7 Mature suburbs
10 08039     Elbert County, Colorado       25162   2595         0   Exurbs   
```
