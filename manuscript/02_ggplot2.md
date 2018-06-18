# Introduction to ggplot2

R was initially developed for statisticians, who often are interested in generating plots or figures to visualize their data. As such, a few basic plotting features were built in when R was first developed. These are all still available; however, over time, a new approach to graphing in R was developed. This new approach implemented what is known as the [grammar of graphics](http://vita.had.co.nz/papers/layered-grammar.pdf), which allows you to develop elegant graphs flexibly in R. Making plots with this set of rules requires the R package `ggplot2`. To get started using ggplot2 requires you to install and load the package into R.

```r
install.packages("ggplot2")
library(ggplot2)
```

### The basics

The grammar of graphics implemented in `ggplot2` is based on the idea that you can build *any* plot as long as you have a few pieces of information. To start building plots in ggplot2, we'll need some data and to know the type of plot we want to make. The type of plot you want to make in `ggplot2` is referred to as a geom. This will get us started, but the idea behind ggplot2 is that every new concept we introduce will be layered on top of the information you've already learned. In this way, ggplot2 is *layered* - layers of information add on top of each other as you build your graph. In code written to generate a `ggplot2` figure, you will see each line is separated by a plus sign (`+`). Think of each line as a different layer of the graph. We're simply adding one layer on top of the previous layers to generate the graph. You'll see exactly what we mean by this throughout each section in this lesson.

To get started, we'll start with the two basics (data and a geom) and build additional layers from there. 

As we get started plotting in `ggplot2`, plots will take the following general form:

```r
ggplot(data = DATASET, aes(VARIABLE(S))) + 
  geom_PLOT_TYPE()
```

After installation and loading `ggplot2` in, you will always begin by calling the `ggplot()` function. You'll then specify your dataset. Within the `ggplot()` function, you'll also specify what variables in your dataset you're interested in plotting. Before making your plot you will also have to specify what geom type you're interested in plotting. We'll focus on a few basic geoms in the next section and give examples of each plot type (geom), but for now we'll just work with a single geom: `geom_point`.  `geom_point` is most helpful for creating scatterplots. As a reminder from an earlier lesson, scatterplots are useful when you're looking at the relationship between two numeric variables.

### Example dataset: `diamonds`

To build your first plot in `ggplot2` we'll make use of the fact that there are some datasets already available in R. One frequently-used data set is known as `diamonds`. This data set contains prices and other attributes of 53,940 diamonds, with each row containing information about a different diamond. If you look at the first few rows of data, you can get an idea of what data are included in this dataset. 

![diamonds dataset](images/02_ggplot2/02_dataviz_ggplot2-2.png)

### Scatterplots: `geom_point`

In `ggplot2` we specify these by defining `x` and `y` in the `aes()` argument. The `x` argument defines which variable will be along the bottom of the plot. `y` refers to which variable will be along the left side of the plot. If we wanted to understand the relationship between the number of carats in a diamond and that diamond's price, we may do the following:

```r
ggplot(data = diamonds, aes(x = carat, y = price)) + 
  geom_point()
```
![diamonds scatterplot](images/02_ggplot2/02_dataviz_ggplot2-3.png)

In this plot, we see that, in general, the larger the diamond is (or the more carats it has), the more expensive the diamond is (price), which is probably what we would have expected. However, now, we have a plot that definitively supports this conclusion. 

### Aesthetics

What if we wanted to alter the size, color or shape of the points? Probably unsurprisingly, these can all be changed within the aesthetics argument. After all, something's aesthetic refers to how something looks. Thus, if you want to change the look of your graph, you'll want to play around with the plot's aesthetics. For now, we'll focus on arguments within `aes()` that change how the points on the plot look. Later, we'll return to `aes()` for other aesthetic changes we may want to make!

#### Point color

In the scatterplot we just generated, we saw that there was a relationship between carat and price, such that the more carats a diamond has, generally, the higher the price. But, it's not a perfectly linear trend. What we mean by that is that not all diamonds that were 2 carats were exactly the same price. And, not all 3 carat diamonds were exactly the same price. What if we were interested in finding out a little bit more about why this is the case?

Well, we could look at the clarity of the diamonds to see whether or not that affects the price of the diamonds? To add clarity to our plot, we could change the color of our points to differ based on clarity:

```r
ggplot(data = diamonds, aes(x = carat, y = price, color = clarity) + 
  geom_point()
```

![changing point colors helps us better understand the data](images/02_ggplot2/02_dataviz_ggplot2-4.png)

Here we see that not only are the points now colored by clarity, ggplot2 has also automatically added a legend for us with the various classes and their corresponding point color. 

#### Point size




#### Point Shape

### Geoms



This code follows the format discussed above. We first see the data argument and the aesthetics argument (aes). Then, we add on a layer to the graph to specify how we want the data displayed. We define that we want to use the `geom_point` geom to generate a scatterplot.

Note that the overall format of the code is the same as it was for the histogram; however, we've defined `x=carat` and `y=price` and changed `geom_histogram` to `geom_point`.





![First 12 rows of diamonds dataset](images/02_ggplot2/02_dataviz_ggplot2-2.png)

Here you see a lot of numbers and can get an idea of what data are available in this data set. For example, in looking at the column names across the top, you can see that we have information about how many carats each diamond is (`carat`), some information on the quality of the diamond cut (`cut`), the color of the diamond from J (worst) to D (best) (`color`), along with a number of other pieces of information about each diamond.

We will use this data set to better understand how to generate plots in R, using `ggplot2`. While we will be generating basic plots here, know that we will be discussing how to change font size, color, and graph appearance in detail later.

##### Histograms

As discussed in the first lesson in this course, histograms are helpful in displaying information about a single set of numbers. For example, if we wanted to see what the distribution of carats was for these data, we could to the following.

```r
ggplot(data = diamonds, aes(carat)) + 
  geom_histogram()
```

Note, we specified in the code above that we would be using the `diamonds` dataset, that we were interested in plotting information about the diamonds' `carat` in the plot, and that the geom we were interested in plotting was a histogram (`geom_histogram`).

![diamonds histogram](images/02_ggplot2/02_dataviz_ggplot2-3.png)


##### Scatterplots

Scatterplots show the relationship between two numeric variables. 
##### Barplots

Barplots show the relationship between a set of numbers and a categorical variable. In the diamonds data set, we may be interested in knowing how many diamonds there are of each cut of diamonds. There are five categories for cut of diamond. If we make a barplot for this variable, we can see the number of diamonds in each category.

```r
ggplot(data = diamonds, aes(cut)) + 
  geom_bar()
```

Again, the changes to the code are minimal. We are now interested in plotting the categorical variable `cut` and state that we want a bar plot, by including `geom_bar()`. 

![diamonds barplot](images/02_ggplot2/02_dataviz_ggplot2-5.png)

##### Boxplots

Boxplots provide a summary of a numerical variable across categories. For example, if you were interested to see how the price of a diamond (a numerical variable) changed across different diamond color categories (categorical variable), you may want to use a boxplot.

```r
ggplot(data = diamonds, aes(x=color, y=price)) + 
  geom_boxplot()
```

In the code, we see that again, we only have to change what variables we want to be included in the plot the type of plot (or geom) we want (here, `geom_boxplot()`) to get a basic boxplot.

![diamonds box](images/02_ggplot2/02_dataviz_ggplot2-6.png)

In the figure itself we see that the median price (the black horizontal bar in the middle of each box represents the median for each category) increases as the diamond color increases from the worst category (J) to the best (D).


##### Other plots

While we've reviewed basic code to make a few common types of plots, there are a number of other plot types that can be made in `ggplot2.` These are listed in the [online reference material for ggplot2](http://ggplot2.tidyverse.org/reference/) or can be accessed through RStudio directly. To do so, you would type `?geom_` into the Console in RStudio. A list of geoms will appear. You can hover your cursor over any one of these to get a short description. 

![?geom in Console](images/02_ggplot2/02_dataviz_ggplot2-7.png)

Or, you can select a geom from this list and click enter. After selecting a geom, such as geom_abline and hitting 'Enter,' the help page for that geom will pop up in the 'Help' tab at bottom right. Here, you can find more detailed information about the selected geom.

[geom_abline help page](images/02_ggplot2/02_dataviz_ggplot2-8.png)


### Additional reources:
* [R For Data Science by Hadley Wickham](http://r4ds.had.co.nz/data-visualisation.html#introduction-1)
* [ggplot2](http://ggplot2.tidyverse.org/)
* [ggplot2 reference](http://ggplot2.tidyverse.org/reference/)

### Slides and Video
  
![Introduction to ggplot2](UPDATE LINK)
  
  * [Slides](https://docs.google.com/presentation/d/1WRfoVxRU_dRcbMGtsha5zSokBRoAFIirm32Wq6bZuEc/edit?usp=sharing)
  
  
{quiz, id: quiz_02_ggplot2}
  
### Introduction to ggplot2
  
? When you've spent a lot of time perfecting the details of your plot, what type of plot have you created?
  
a) exploratory
B) explanatory

? Which of these is NOT required when plotting in `ggplot2`?

a) ggplot() function call
b) the geom you want to plot
c) the variable you want to plot
D) the color you want to use

{choose-answers: 4)
? Which geom would you specify to generate a scatterplot? 

C) geom_point
o) geom_histogram
o) geom_scatterplot
o) geom_scatter
o) geom_abline
o) geom_bar
o) geom_blank
o) geom_scatter

{choose-answers: 4)
? Which geom would you specify if you wanted to know how many individuals in a data set fell into each level of a categorical variable?

C) geom_bar
o) geom_boxplot
o) geom_scatterplot
o) geom_abline
o) geom_smooth
o) geom_density
o) geom_curve

{/quiz}