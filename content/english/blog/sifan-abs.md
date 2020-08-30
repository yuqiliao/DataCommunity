---
author: "Sifan Liu"
date: 2018-10-31
linktitle: Annual Business Survey
title: Analyzing business ownership using Census data
highlight: false
image: images/blog/negative.svg
showonlyimage: false
---

- How many businesses in the United States are owned by women or minorities? 
- Does the ownership vary by industry and region? 
- How many jobs do black-owned business support in Birmingham, AL? 
- What type of businesses are more likely to offer employed-paid benefits?

These are questions that could be answered by Annual Business Survey [ABS](https://www.census.gov/programs-surveys/abs.html), an annual project by the U.S. Census Bureau to provide information on economic and demographic characteristics for business and business owners at regional level.

## Use case: Understanding challenges faced by local business owners

![share of business facing negative impact](/images/blog/negative.svg "Negative Impact")

## Use case: Regional business ownership profiles
Number of firms, employment, annual payroll and sales by owner demographics of small business (firm with fewer than 250 employees) in Denver metropolitan area

```r
# A tibble: 6 x 6
  demo        firm_size         num_owners_or_firms    emp   payroll sales_or_revenue
  <chr>       <chr>                           <dbl>  <dbl>    <dbl>            <dbl>
1 asian       1 - 250 employees                3374  22533   665826          3032563
2 black       1 - 250 employees                 727   3929   119867           569420
3 female      1 - 250 employees               12580  90090  3267951         12538685
4 hispanic    1 - 250 employees                2851  20040   727334          2956540
5 male        1 - 250 employees               34282 314053 14528510         65148492
6 nonminority 1 - 250 employees               46476 398986 17794599         77509978
```