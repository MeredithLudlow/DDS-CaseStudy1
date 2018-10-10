---
title: "Case Study"
author: "Meredith Ludlow"
date: "October 9, 2018"
output: 
  html_document:
    keep_md: true
---
## Introduction
Write intro here.

I used the following R packages in the course of this analysis: plyr

```r
library(plyr)
```

First, we will look at the number of breweries in each state. After we imported the brewery data, we created a table of the number of breweries that are located in each state. The table is shown below.

```r
Breweries <- read.csv("Breweries.csv", header=TRUE)
BreweriesPerState <- count(Breweries, "State")
BreweriesPerState
```

```
##    State freq
## 1     AK    7
## 2     AL    3
## 3     AR    2
## 4     AZ   11
## 5     CA   39
## 6     CO   47
## 7     CT    8
## 8     DC    1
## 9     DE    2
## 10    FL   15
## 11    GA    7
## 12    HI    4
## 13    IA    5
## 14    ID    5
## 15    IL   18
## 16    IN   22
## 17    KS    3
## 18    KY    4
## 19    LA    5
## 20    MA   23
## 21    MD    7
## 22    ME    9
## 23    MI   32
## 24    MN   12
## 25    MO    9
## 26    MS    2
## 27    MT    9
## 28    NC   19
## 29    ND    1
## 30    NE    5
## 31    NH    3
## 32    NJ    3
## 33    NM    4
## 34    NV    2
## 35    NY   16
## 36    OH   15
## 37    OK    6
## 38    OR   29
## 39    PA   25
## 40    RI    5
## 41    SC    4
## 42    SD    1
## 43    TN    3
## 44    TX   28
## 45    UT    4
## 46    VA   16
## 47    VT   10
## 48    WA   23
## 49    WI   20
## 50    WV    1
## 51    WY    4
```

```r
# Should we make a histogram?
```

After importing the beer data, we merged the two data sets together on the variable Brew_ID. This varaible contains the specific ID numbers for each brewery. The first and last 6 lines of the merged data set are shown below.

```r
Beers <- read.csv("Beers.csv", header=TRUE)
colnames(Beers)[5] <- "Brew_ID"
BrewsandBeers <- merge(Beers, Breweries, by = "Brew_ID")
colnames(BrewsandBeers)[2] <- "BeerName"
colnames(BrewsandBeers)[8] <- "BrewerieName"
head(BrewsandBeers)
```

```
##   Brew_ID      BeerName Beer_ID   ABV IBU
## 1       1  Get Together    2692 0.045  50
## 2       1 Maggie's Leap    2691 0.049  26
## 3       1    Wall's End    2690 0.048  19
## 4       1       Pumpion    2689 0.060  38
## 5       1    Stronghold    2688 0.060  25
## 6       1   Parapet ESB    2687 0.056  47
##                                 Style Ounces       BrewerieName
## 1                        American IPA     16 NorthGate Brewing 
## 2                  Milk / Sweet Stout     16 NorthGate Brewing 
## 3                   English Brown Ale     16 NorthGate Brewing 
## 4                         Pumpkin Ale     16 NorthGate Brewing 
## 5                     American Porter     16 NorthGate Brewing 
## 6 Extra Special / Strong Bitter (ESB)     16 NorthGate Brewing 
##          City State
## 1 Minneapolis    MN
## 2 Minneapolis    MN
## 3 Minneapolis    MN
## 4 Minneapolis    MN
## 5 Minneapolis    MN
## 6 Minneapolis    MN
```

```r
tail(BrewsandBeers)
```

```
##      Brew_ID                  BeerName Beer_ID   ABV IBU
## 2405     556             Pilsner Ukiah      98 0.055  NA
## 2406     557  Heinnieweisse Weissebier      52 0.049  NA
## 2407     557           Snapperhead IPA      51 0.068  NA
## 2408     557         Moo Thunder Stout      50 0.049  NA
## 2409     557         Porkslap Pale Ale      49 0.043  NA
## 2410     558 Urban Wilderness Pale Ale      30 0.049  NA
##                        Style Ounces                  BrewerieName
## 2405         German Pilsener     12         Ukiah Brewing Company
## 2406              Hefeweizen     12       Butternuts Beer and Ale
## 2407            American IPA     12       Butternuts Beer and Ale
## 2408      Milk / Sweet Stout     12       Butternuts Beer and Ale
## 2409 American Pale Ale (APA)     12       Butternuts Beer and Ale
## 2410        English Pale Ale     12 Sleeping Lady Brewing Company
##               City State
## 2405         Ukiah    CA
## 2406 Garrattsville    NY
## 2407 Garrattsville    NY
## 2408 Garrattsville    NY
## 2409 Garrattsville    NY
## 2410     Anchorage    AK
```

For each column in the merged data set, the number of missing data points are summed. The results are listed in the table below.

```r
na_counts <- sapply(BrewsandBeers, function(y) sum(is.na(y)))
na_counts
```

```
##      Brew_ID     BeerName      Beer_ID          ABV          IBU 
##            0            0            0           62         1005 
##        Style       Ounces BrewerieName         City        State 
##            0            0            0            0            0
```
