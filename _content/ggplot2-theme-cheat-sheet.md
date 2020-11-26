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

You can both go granular by specifying the style of each and every element, or address them in bulk by using global line, rect, text, and title arguments passed to the theme() function.

In this post, I'll show you how you can customize your plots step by step, using the data from <code>library(palmerpenguins)</code> (credits to <a href="https://github.com/allisonhorst/palmerpenguins">Allison Horst</a> for creating the dataset).

## Setting up
Let's start by downloading and loading the package.

```r
# Get the palmerpenguins library
remotes::install_github("allisonhorst/palmerpenguins")
# Load required libraries and the data
library(palmerpenguins)
library(tidyverse)
# Inspect the data
data = penguins
summary(data)
```

Looking at the summary of our data, we have some missing values, particularly when it comes to the penguins' sex (As with many species of birds, <a href="https://www.antarctica.gov.au/about-antarctica/animals/penguins/gentoo-penguins/#:~:text=Males%20tend%20to%20be%20larger,from%20other%20species%20of%20penguin">it isn't always easy to determine a penguin's sex</a>).

For the purpose of this article, let's just omit all the rows where there are missing data.

```r
data = na.omit(data)
```
## A basic plot

Now, let's look at a simple plot showing how bill and flipper lengths vary among specimens of the three penguin species in the dataset.

```r
# A basic plot with with bill length on the X axis, flipper length on the Y axis, and species represented by color.
p = ggplot(data, aes(x = bill_length_mm, y = flipper_length_mm, color = species)) +
  geom_point() +
  # Using the labs() function, I add some text description to the plot.
  labs(title = "The bill and flipper lengths of various penguin species",
  subtitle = "The Gentoo penguins have longer bills and flippers.",
  caption = "Data collected by Dr Kristen Gorman")
p
```
![A basic penguins plot](/assets/ggplot_cheat_sheet/penguins.jpeg)

This plot is definitely readable and informative. But since you're here, you probably want to learn how to make your ggplot2 plots more custom.

# Text styling

Text elements of your plots can be altered by using the *element_text()* function.

## Scoping element_text() styling

### Global styling

You can style text elements globally using the *text* argument within the theme() function.

```r
# Using the text argument, we can define all text elements of the plot.
p + theme(
  text = element_text()
```

Although the documentation claims that the *text* argument defines all text elements, technically this is not true - there's one exception to this rule.

*axis.text* arguments inherit some properties from the default theme, instead of the *text* argument. This is a <a href="https://github.com/tidyverse/ggplot2/issues/2175">known issue</a> and it's unlikely to be fixed anytime soon. In any case, you need to define your axis text elements separately from the *text* argument.

### Scoped styling

You can also modify each text element on a granular level. In the following example I'm defining the plot caption, subtitle, and title separately.

```r
# It's also possible to define each text element separately.
X = element_text(
  color = "red")
Y = element_text(
  color = "green")
Z = element_text(
  color = "blue")
p + theme(
  plot.caption = X,
  plot.subtitle= Y,
  plot.title = Z
)
```
![A penguins plot with colored text](/assets/ggplot_cheat_sheet/penguins_2.jpeg)

## element_text() arguments

```r
p + theme(
  text = element_text(
  family = "Montserrat",
  face = "plain",
  color = "#124a21",
  size = 13,
  hjust = 0.5,
  vjust = 0.5,
  angle = 0,
  lineheight = 1,
  margin = margin(0,0,0,0),
  debug = FALSE,
  inherit.blank = FALSE
  ))
```
![A penguins plot that's a little more customized](/assets/ggplot_cheat_sheet/penguins_1.jpeg)

That's a lot of arguments, right? Fortunately, they are mostly self-explanatory:

* **family**
Your desired font family. To browse available fonts, use windowsFonts().

* **face**
You can pick the font face from among "plain", "italic", "bold", or "bold.italic". Keep in mind that in some cases, font face may already be specified in the family argument.

* **color**: The color of your text. You can use both <a href="http://sape.inf.usi.ch/sites/default/files/ggplot2-colour-names.png">R's predefined colors</a> and hexadecimal values.

* **size**: Your desired text size in <a href="https://www.computerhope.com/jargon/f/font-size.htm#:~:text=A%20font%20is%20often%20measured,a%20half%20of%20an%20inch.">points.</a>

* **hjust**: Horizontal justification that takes a value between 0 and 1 (0: left-justified, 1: right-justified). hjust and vjust are brilliantly explained in detail <a href="https://stackoverflow.com/questions/7263849/what-do-hjust-and-vjust-do-when-making-a-plot-using-ggplot">here</a>.

* **vjust**: Vertical justification, see above.

* **angle**: The angle of your text elements, ranging from 0-360 and applied counterclockwise.

* **lineheight**: Line height that applies to text elements which occupy more than one line.

* **margin**: The margin around your elements. The margin argument is used together with the margin() function. **margin() takes 5 arguments:** four margins specified in the direction of top, right, bottom, left, and the unit argument, such as "pt" for points, or "cm" for centimeters.

* **debug**: Setting the debug to a logical TRUE outputs a plot with all the text elements marked by colored rectangles, so that you can better see the effects of your changes.

* **inherit_blank**: If set to TRUE, this argument makes an element inherit the blank state from its parent.

# Borders and backgrounds styling

Borders and backgrounds of your plots can be altered by using the element_rect() function.

## Scoping element_rect() styling

### Global styling

You can style rect elements globally using the rect argument within the theme() function.

```r
p + theme(rect = element_rect(
  fill = "#d1cdcd"))
```
![A penguins plot with a grey rect styling](/assets/ggplot_cheat_sheet/penguins_3.jpeg)

### Scoped styling

You can also scope your rect elements separately. In the following example I'm styling the legend and panel backgrounds separately.

```r
p + theme(legend.background = element_rect(fill = "#8a8a8a"),
          panel.background = element_rect(fill = "#d1cdcd"))
```
![A penguins plot with a grey rect styling of panel and legend backgrounds](/assets/ggplot_cheat_sheet/penguins_4.jpeg)

## element_rect() arguments

```r
p + theme(
  rect = element_rect(
    fill = NULL, 
    colour = NULL, 
    size = NULL, 
    linetype = NULL, 
    color = NULL)
```

element_rect() takes fewer arguments than element_text(), so we'll be done in no time!

* **fill**: Determines the fill color of your rect elements.

* **colour** (or **color**): The color of your borders.

* **size**: The size of your borders in points.

* **linetype**: The linetype of your border. You can choose from blank, solid, dashed, dotted, dotdash, longdash, and twodash. 
You can also use an integer from 0-6, 0 being blank and 6 being twodash. Alternatively, you can pass a string of an even number of hexadecimal digits which give the lengths in consecutive positions in the string.

![A plot showing various linetypes available in ggplot](/assets/ggplot_cheat_sheet/ggplot2-linetype-identity.png)

# Lines styling

# "Removing" ggplot elements 

