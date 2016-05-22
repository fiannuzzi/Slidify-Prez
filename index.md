---
title       : (Sun)day distance
subtitle    : A very simple Shiny app
author      : Francesca Iannuzzi
job         : 
framework   : html5slides        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [shiny]            # {mathjax, quiz, bootstrap}
mode        : standalone  # {selfcontained, draft}
knit        : slidify::knit2slides
---

## The app

**(Sun)day distance** gives the number of days and sundays between today and a custom input date.

The user selects the desired date (past or future) and the app does the rest.

*That's how I found out I have been living about 12000 days and 1700 Sundays*



--- .class #id 

## The code: part 1

This function from server.R computes the absolute value of the difference between today and the input date:


```r
day_distance <- function(date) {
  new_date <- as.Date(date, format="%Y-%m-%d")
  today <- Sys.Date()
  return(abs(new_date-today))
}
```

Example:

```r
day_distance("2015-12-31")
```

```
## Time difference of 143 days
```

---

## The code: part 2
This function from server.R computes how many Sundays there are between today and the input date (only the relevant lines of codes are shown):



```r
sundays <- function(date) {
  #...
  days_seq <- seq(today, new_date, by="days")
  weekdays_seq <- weekdays(days_seq)
  sundays <- sum(weekdays_seq == "Sunday")
  #...  
}
```

Example:

```r
sundays("2015-12-31")
```

```
## [1] 21
```

---

## Conclusions
That's all for my first Shiny App. 

You can play with it [here](https://fiannuzzi.shinyapps.io/Shiny_App/)

*P.S. If someone knows how to embed a Shiny app in Slidify please let me know! I miserably failed at that...*

<style>
em {
  font-style: italic
}
</style>

<style>
strong {
  font-weight: bold;
}
</style>

