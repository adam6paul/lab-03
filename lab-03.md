Lab 03 - Nobel laureates
================
Adam Paul
2/11

### Load packages and data

``` r
library(tidyverse) 
```

``` r
nobel <- read_csv("data/nobel.csv")
```

# Exercises

## Exercise 1

### Question 1

How many observations and how many variables are in the dataset? Use
inline code to answer this question. What does each row represent?

``` r
view(nobel)
```

935 observations of 26 variables. Each row represents an individual
nobel laureate.

### Question 2

Create a new data frame called nobel\_living that filters for:

1.  Laureates for whom country is available

2.  Laureates who are people as opposed to organizations (organizations
    are denoted with “org” as their gender)

3.  Laureates who are still alive (their died\_date is NA)

``` r
nobel_living <- nobel %>% #Is creating the new data frame out of nobel
  filter(!is.na(country), #Is opening filter, and beginning by filtering for ones where country is not NA
  gender != "org",        #Is filtering for ones where gender is not (! meaning not) equal to org
  is.na(died_date))       #Is filtering for ones that do not have a death date
view(nobel_living)
```

## Exercise 2

### Set-up

Rather than write up my own explanation, here is the one offered by
Mason for this set-up portion.

First, we’ll create a new variable to identify whether the laureate was
in the US when they won their prize. We’ll use the `mutate()` function
for this. The following pipeline mutates the `nobel_living` data frame
by adding a new variable called `country_us`. We use an if statement to
create this variable. The first argument in the `if_else()` function
we’re using to write this if statement is the condition we’re testing
for. If country is equal to `"USA"`, we set country\_us to `"USA"`. If
not, we set the country\_us to `"Other"`.

> Note: I do want it known that in my desire to make things look good I
> both looked up how to replicate making the variable names appear in
> boxes, *and* the text formatting used here. If only I I could dedicate
> a fraction of that neuroticism towards anything else.

``` r
nobel_living <- nobel_living %>% #This is saying to create a change in nobel_living, modeled off of the same data frame
  mutate(
    country_us = if_else(country == "USA", "USA", "Other")
  )
```

Next, we will limit our analysis to only the following categories:
Physics, Medicine, Chemistry, and Economics.

``` r
nobel_living_science <- nobel_living %>%
  filter(category %in% c("Physics", "Medicine", "Chemistry", "Economics"))
```

Create a faceted bar plot visualizing the relationship between the
category of prize and whether the laureate was in the US when they won
the nobel prize. Interpret your visualization, and say a few words about
whether the Buzzfeed headline is supported by the data.

Laureate country and category of prize

### Exercise 3

Remove this text, and add your answer for Exercise 1 here. Add code
chunks as needed. Don’t forget to label your code chunk. Do not use
spaces in code chunk labels.

### Exercise 4

…

### Exercise 5

…

### Exercise 6

…
