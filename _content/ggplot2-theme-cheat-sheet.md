---
layout: page
title: ggplot2 Theme Cheat Sheet (with code examples!)
description: All the ways in which you can customize your data visualizations in ggplot2.
---

1. asd
{:toc}

# Introduction

ggplot2 is an extremely popular library for data visualization.

Using the theme() function from the ggplot2 library, you can customize every element of your visualization, ranging from the margins around various elements to the font family, size and color.

In this post, I'll show you how you can customize your plot step by step, using the data from <code>library(palmerpenguins)</code> (credits to <a href="https://github.com/allisonhorst/palmerpenguins">Allison Horst</a> for creating the dataset).

## Setting up
Let's start by downloading and loading the package.

``` r
#Get the palmerpenguins library
remotes::install_github("allisonhorst/palmerpenguins")
#Load required libraries and the data
library(palmerpenguins)
library(tidyverse)
#Inspect the data
data = penguins
summary(data)
```

Looking at the summary of our data, we have some missing values, particularly when it comes to the penguins' sex (As with many species of birds, <a href="https://www.antarctica.gov.au/about-antarctica/animals/penguins/gentoo-penguins/#:~:text=Males%20tend%20to%20be%20larger,from%20other%20species%20of%20penguin">it isn't always easy to determine a penguin's sex</a>).

For the purpose of this article, let's just omit all the rows where there are missing data.

``` r
data = na.omit(data)
```
## A basic plot

Now, let's look at a simple plot showing how bill and flipper lengths vary among specimens of the three penguin species in the dataset.

``` r
p = ggplot(data, aes(x = bill_length_mm, y = flipper_length_mm, color = species)) +
  geom_point() +
  labs(title = "The bill and flipper lengths of various penguin species",
  subtitle = "The Gentoo penguins have longer bills and flippers.",
  caption = "Data collected by Dr Kristen Gorman")
p
```
![A basic penguins plot](/assets/penguins.png)

This plot is definitely readable and informative, but there's room for improvement.

# Labels
