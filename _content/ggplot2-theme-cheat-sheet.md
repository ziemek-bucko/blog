---
layout: page
title: ggplot2 Theme Cheat Sheet (with code examples!)
description: All the ways in which you can customize your data visualizations in ggplot2.
---

ggplot2 is an extremely popular library for data visualization.

Using the theme() function from the ggplot2 library, you can customize every element of your visualization, ranging from the margins around various elements to the font family, size and color.
1. asd
{:toc}
In this post, I'll show you how you can customize your ggplot step by step, using the data from <code>library(palmerpenguins)</code>.

{% highlight R %}
mytheme = theme(plot.background = element_rect(fill = "#0a1c40"),
        panel.background = element_rect(fill = "#0a1c40", colour = "#0a1c40",
                                size = 2, linetype = "solid"),
        plot.margin = margin(3, 3, 3, 3, "cm"),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank(),
        axis.title.y = element_text(colour = "white", family = "Archia", face = "bold", margin = margin(0,5,0,0), size = 16),
        axis.title.x = element_blank(),
        axis.text.x = element_text(colour = "white", family = "Archia", face = "bold", margin=margin(13,0,0,0)),
        axis.text.y = element_text(colour = "white", family = "Archia", face = "bold", margin=margin(0,0,0,0)),
        axis.ticks.x = element_line(colour = "white"),
        axis.ticks.y = element_line(colour = "white"),
        axis.line = element_line(color = 'white'),
        plot.title = element_text(family = "Archia",
                                  face = "bold",
                                  colour = "white",
                                  size = 16,
                                  lineheight = 1.3,
                                  hjust = 0,
                                  margin=margin(15,0,15,0)),
        plot.caption = element_text(family = "Archia",
                                    colour = "white",
                                    size = 19,
                                    hjust = 0,
                                    margin=margin(0,0,0,0)))
{% endhighlight %}

# Lorem ipsum dolor sit amet
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
## Lorem ipsum dolor sit amet
# Lorem ipsum dolor sit amet
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
## Lorem ipsum dolor sit amet
# Lorem ipsum dolor sit amet
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
## Lorem ipsum dolor sit amet
