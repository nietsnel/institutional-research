R for institutional research
================
Jordan Prendez
2016-11-18

-   [Introduction to R for institutional Research.](#introduction-to-r-for-institutional-research.)
-   [Installation of R and Rstudio](#installation-of-r-and-rstudio)
-   [Basic R](#basic-r)
-   [R for Institutional Research](#r-for-institutional-research)

Introduction to R for institutional Research.
---------------------------------------------

R is a programming language that is the Lingua franca of statistics. One of the most cited benefits of R is that it can produce publication quality graphics that can highly modified. The base R language includes common statistical procedures, however, R's wide spread use is undoutably related to the the ever growing set of user created statistical packages. Finally, another *huge* benefit is **R is availible for free**. This is especially important in the era of decreasing support and tighter budgets in higher education.

While R was not made specifically for institutional research it can perform all of the same types of functions and manipulations you might be accustomed to in other statistical software packages. However, R's learning curve can be somewhat steep and this short presentation will help those not acquanted with R to understand how to install, import data, and perform basic manipulations and other procedures that are common in institutional research, including a few examples of R's graphing capability.

Installation of R and Rstudio
-----------------------------

R is maintained by the R foundation and can be downloaded from the following website. R is availible to Windows, OS X and and Linux. Click on the appropriate link and follow the instructions to install R. This guide is written for the windows version of R. If you have already installed R it is important to make sure you have the most updated version (some parts of this tutorial may not work with older versions of R.)

<https://cran.r-project.org/>

<img style="float: right" src="https://www.r-project.org/logo/Rlogo.svg" width="200" height="200"/>

Everything we do from this point onwards can be accomplished in base R (what we have installed so far) but I prefer and would recommend using the Rstudio environment. Rstudio is a user interface that keeps R organized and automates some of the written code into a point in click interface.

### Download the R studio interface from here

<https://www.rstudio.com/products/rstudio/download2/>

<!-- <img style="float: left" src="https://www.rstudio.com/wp-content/uploads/2014/07/RStudio-Logo-All-Gray.png" width="200" height="200" /> -->
Once this is installed you are ready to start using R!

This presentation can be opened in R and the code executed directly from the R scripting window. Rstudio can open traditional R scripts .R, in addition to Rmarkdown files .Rmd (this presentation) and other more interactive file types.

#### Rstudio

The Rstudio environment consists of four different panes of which

-   The script window and
-   Console window

are usually visible as the left two quadrants. The two panels on the right side change depending on need. Most of your work should be typed into the scripting window (where it can be saved) but also can be run live from the console.

### Additional pre-reqs: You must download the following files listed at the top of this github page if you wish to run these analysis yourself.

1.  **README.Rmd**
2.  **Both files located in the "Prerequisite files" folder**

*Once you have downloaded these files open the README.Rmd and follow along. You will need to rename the file paths to point to the two prerequisite files at the appropriate time.*

For those who are transisitioning from a point in click interface there are several graphical user interfaces (GUI) availible for R that might be useful for someone transitioning.

### Download and Install R commander

``` r
##We won't be focusing on R commander. For those interested here are the necessary lines of code to install and run the program. 

install.packages("Rcmdr") ##Run this to install R commander. (Only needs to be run once). ##Evaluate this, or any line in R, by highlighting it then using "Ctrl+R".
library(Rcmdr)  #Run this line 
Rcommander() #and execute this line to start R commander from the R console (or script window) each time you want to start R commander.
```

For more info about Rcmdr see the appropriate footnotes at the bottom of this page. [1] [2]

Basic R
-------

Practice executing code: R as a calculator. For this example, practice executing the following commands in the R console.

``` r
##Run these examples yourself. Try your own values.

10+12  ##Evaluate this, or any line in R, by highlighting it then using "Ctrl+R"

abs(-10-500)

sqrt(pi+2)
```

Executing the commands above, and others, will help give you practice in the Rstudio environment and demonstrate basic R functionality.

R for Institutional Research
----------------------------

The goal of this section is to provide concrete examples of tasks that are useful to the institutional researcher.

### Importing data

To import a dataset click on the import dataset button in the "Environment" tab (by default this can be found in the top right quadrant of Rstudio). Select a file to import, select the appropriate options, name the dataset and press "import" to import the dataset into R.

*Remember the file paths shown throughout this document are examples and must be changed to the actual location on your local machine.*

``` r
##We can also use the command line to perform the same function as the import dataset button in Rstudio.
original_dataset_name <- read.csv("C:/Users/jprendez/Desktop/c2015_a.csv")
```

### Basic R functions to memorize

There are a few basic functions that are very important to understand in R.

1.  Assigning variables
2.  How to view data
3.  Basic subsetting
4.  Exporting data from R. <!-- 5. Joining a dataset [coming soon] -->

#### Variable assignment

Assigning a variable

``` r
new_dataset_name <- original_dataset_name  # we can rename any variable or dataset in R to any other name using the assignment arrow " <- ". It is not a good idea to name your datasets, however, the same names as R functions (i.e. do not name your dataset mean, or lm, etc.)
```

#### Viewing data

To view a dataset use the "view" command.

``` r
##We can view our dataset using the "view" command. 

View(new_dataset_name) 

view(new_dataset_name) #Note, that R is case sensitive. So a lowercase "view" will not work.
```

#### Basic subsetting

The basic subsetting function in R is defined using the following form

*new\_dataset\_name\[row,column\]*

``` r
new_dataset_name[3,2]  ##this gives us the value corresponding to the third row, and second column of our dataset.

x <- new_dataset_name[3,2] ##we can assign this single value to a variable or..

y <- new_dataset_name[,2] ##by not defining the row, assign an entire column to a variable (or vice versa)
```

#### Exporting a file

``` r
write.table(x=new_dataset_name, file="C:/Users/jprendez/Desktop/name_of_exported_table.txt", sep=",") 
#Notice the first argument is the name of the variable in R, the second is the path we want to write the file to, and lastly, the type of delimeter.
```

In order to learn more about the write.table function or the View function (or any function), execute the function name with a question mark immediately before it

``` r
 ?View()
 ?write.table()

 #alternatively you can simply type in the funciton name into the help search bar. This tab is by default in the bottom right quadrant of Rstudio.
```

One of R's biggest strength is the large amount of packages written for it. A package is a user created set of functions that expand R functionality.

These are the commands to install the devtools package. We use this to install packages hosted on bitbucket, and github.

``` r
install.packages("devtools", repos="http://cran.us.r-project.org") #installs the devtools package - this should only be run once
library(devtools)  #attaches the devtools package - this must be run at the start of every R session (usually just place this at the beginning of your R script)
```

#### Install the inst.research package.

R does not come with a default way of assigning names to variables. I wrote a package called inst.research that includes the function called import\_lables that gives R this capability. First we need to install the package...

``` r
##Run these two lines of code to install the inst.research package
library(devtools)
devtools::install_bitbucket("nietsnel/inst.research", force=TRUE)
library(inst.research)
```

Remember, In R we can learn more about a particular package by typing the "?" before any particular function.

``` r
##For instance ?mean calls R documentation for the mean function (a base function in R)

?mean

##We can also view the code of the import_labels funtion which is part of the inst.research package. 

?import_labels
```

Once the inst.research package is installed We must attach it using the library function. We can then use the import\_labels to load a dataset for our next example

``` r
library(inst.research) ##attach the inst.research package

import_labels(dataset="C:/Users/jprendez/Desktop/c2015_a.csv", definitions="C:/Users/jprendez/Desktop/definitions_1.txt")
```

#### More tools for institutional research:

The dplyr and tidyr packages are two of the best packages for data wrangling. Here we will demonstrate some of their powerful and intuitive functionality.

``` r
  # To select a subset of the dataset above use


  install.packages("tidyr", repos="http://cran.us.r-project.org", dependencies = TRUE) #installs the tidyr package - this should only be run once
  install.packages("dplyr", repos="http://cran.us.r-project.org", dependencies = TRUE) #installs the dplyr package - this should only be run once

  install.packages("scales", repos="http://cran.us.r-project.org", dependencies = TRUE) #installs the dplyr package - this should only be run once. The scales packages is used in our graphing example. 


library(tidyr) ##then attach them
library(dplyr)
library(scales)
```

The following filters and commands should apply to "data\_set". See the RStudio cheatsheet on datawrangling for more info. Here is an example on how we can subset our loaded "dataset"

``` r
library(tidyverse)
```

    ## Loading tidyverse: ggplot2
    ## Loading tidyverse: tibble
    ## Loading tidyverse: tidyr
    ## Loading tidyverse: readr
    ## Loading tidyverse: purrr
    ## Loading tidyverse: dplyr

    ## Conflicts with tidy packages ----------------------------------------------

    ## filter(): dplyr, stats
    ## lag():    dplyr, stats

``` r
data_set2 <- data_set %>%  #the first line of code indicates that we want our subsetted dataset assigned to a new variable called "dataset2". 
  filter(MAJORNUM=="First major") %>% #select only records with the column MAJORNUM equal to "First major".
  filter(AWLEVEL!="Associate^s degree") %>% #select only records with the column AWLEVEL NOT equal to "Associate^s degree"
  mutate(my_new_var_name=CTOTALM+CTOTALW) %>%  #creates new variable based on existing variables and appends to dataframe
  select(UNITID, CIPCODE, MAJORNUM, AWLEVEL, CTOTALM, CTOTALW,  my_new_var_name) %>%  #selects only those columns listed (drops all others)
  rename(degree_level=AWLEVEL) #rename a column ("new name=old name")

# View(
library(knitr)
# library(dataset)
# table(data_set$MAJORNUM, data_set$CTOTALM)

glimpse(data_set2) ##Use "glimpse"" to obtain a summary of the dataset
```

    ## Observations: 209,389
    ## Variables: 7
    ## $ UNITID          <int> 100654, 100654, 100654, 100654, 100654, 100654...
    ## $ CIPCODE         <fctr> Agriculture, General, Animal Sciences, Genera...
    ## $ MAJORNUM        <fctr> First major, First major, First major, First ...
    ## $ degree_level    <fctr> Bachelor^s degree, Bachelor^s degree, Bachelo...
    ## $ CTOTALM         <int> 3, 0, 2, 2, 1, 2, 2, 1, 1, 3, 2, 3, 15, 3, 2, ...
    ## $ CTOTALW         <int> 0, 4, 7, 5, 1, 1, 4, 2, 0, 1, 7, 4, 12, 3, 1, ...
    ## $ my_new_var_name <int> 3, 4, 9, 7, 2, 3, 6, 3, 1, 4, 9, 7, 27, 6, 3, ...

### Combining datasets

Lets take a sample of the dataframe in memory called "data\_set" and name it "data\_set\_small".

``` r
data_set_small<- sample_frac(tbl=data_set, size=0.5, replace=FALSE)
```

Next, merge our new "data\_set\_small" to our dataframe that we named "data\_set".

``` r
in_common_dataset<- semi_join(x=data_set_small, y=data_set, by="UNITID")
```

This command gives us a new dataset called "in\_common\_dataset". The environment quadrant in the top right of Rstudio should show us that this new dataset contains the same number of records that have a match in the second dataset (i.e. the number that match a record in "data\_set").

There are many different types of ways to combine datasets. For a list of other useful commands including merges see the Rstudio cheatsheet for datawrangling [here](https://www.rstudio.com/wp-content/uploads/2015/02/data-wrangling-cheatsheet.pdf)

### Graphics in R

R produced high quality graphs. Here is an example of graphing using the popular ggplot2 package.

Practice...

1.  First import the file "cost\_of\_attend" .csv file.
2.  rename the file data using the assignment variable
3.  run the code below to generate graph

``` r
d_bg <- data[, -7]  # Background Data - full without the 5th column 
ggplot(data, aes(x = cost_attend, y = earnings)) +  #specifies which columns we want to graph
  # geom_point(data = d_bg, colour = "grey", alpha = .2) + #specifies which color we want the background data
  geom_point() + ##adds layer (we use this to add subsequent colors)
  # facet_wrap(~ AWLEVEL) +  #panels data by degree
  # guides(colour = FALSE) + #supresses default option for color legend
  theme_bw() + #changes background color from default grey to white
  ggtitle("Earnings by Degree") + #adds Main title
  xlab("Yearly cost of attendance") + #adds x lable
  ylab("5-year post-grad income") + #adds y lable
  scale_y_continuous(labels=dollar) + #indicates that the y variable is continuous and currency (scales package addon)
  scale_x_continuous(labels=dollar) #indicates that the x variable is continuous and currency (scales package addon)
```

<img src="README_files/figure-markdown_github/unnamed-chunk-20-1.png" style="display: block; margin: auto;" />

Here we can add color to each group while putting into the foreground the remaining groups. While the black and white version, above, is fairly clear, graphing with color can highlight group differences in a more realistic example.

``` r
d_bg <- data[, -7]  # Background Data - full without the 5th column 
ggplot(data, aes(x = cost_attend, y = earnings, colour = AWLEVEL)) +  #specifies which columns we want to graph. Note: colour=AWLEVEL here. This indicates that we are specifiying the colour by the degree level.
  geom_point(data = d_bg, colour = "grey", alpha = .2) + #specifies which color we want the background data
  geom_point() + ##adds layer (we use this to add subsequent colors)
  facet_wrap(~ AWLEVEL) +  #panels data by degree
  guides(colour = FALSE) + #supresses default option for color legend
  theme_bw() + #changes background color from default grey to white
  ggtitle("Earnings by Degree") + #adds Main title
  xlab("Yearly cost of attendance") + #adds x lable
  ylab("5-year post-grad income") + #adds y lable
  scale_y_continuous(labels=dollar) + #indicates that the y variable is continuous and currency (scales package addon)
  scale_x_continuous(labels=dollar) #indicates that the x variable is continuous and currency (scales package addon)
```

<img src="README_files/figure-markdown_github/unnamed-chunk-21-1.png" style="display: block; margin: auto;" /> Source [3]

We can also easily perform statistical analysis in R. Here we see we can see that it takes only two lines of code to perform a linear regression. (data for this regression is not included in HTML)

``` r
ans <- lm(dat$xvar ~ dat$yvar)  ##code to run a linear model on two variables within the "dat" dataset. We can access a variable within a data.frame using the "$". 
summary(ans)  ##Gives us the summary of the results -- shown below
```

    ## 
    ## Call:
    ## lm(formula = dat$xvar ~ dat$yvar)
    ## 
    ## Residuals:
    ##    Min     1Q Median     3Q    Max 
    ## -9.385 -2.411  1.441  2.649  7.820 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)   2.9557     1.8431   1.604 0.126187    
    ## dat$yvar      0.6267     0.1460   4.292 0.000438 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 4.659 on 18 degrees of freedom
    ## Multiple R-squared:  0.5058, Adjusted R-squared:  0.4784 
    ## F-statistic: 18.43 on 1 and 18 DF,  p-value: 0.0004384

``` r
  install.packages("ggplot2", repos="http://cran.us.r-project.org", dependencies = TRUE) #installs the dplyr package - this should only be run once. The scales packages is used in our graphing example. 

library(ggplot2)
```

We can then graph those results ...

``` r
library(ggplot2)

##credit http://www.cookbook-r.com/Graphs/Scatterplots_(ggplot2)/  
##^ great website for more graphing ideas. 

##this code block graphs that dataset

ggplot(dat, aes(x=xvar, y=yvar)) +
    geom_point(shape=1) +    # Use hollow circles
    geom_smooth(method=lm) +  # Add linear regression line -- (by default includes 95% confidence region)
    theme_bw() + #changes the background color
    ggtitle("Important research") + #adds a main title
    xlab("Temperature") + #adds a x lable
    ylab("Need for ice-cream")  #adds a y lable
```

<img src="README_files/figure-markdown_github/unnamed-chunk-25-1.png" style="display: block; margin: auto;" />

### Further Resources

1.  The Rstudio authored [cheat sheets](https://www.rstudio.com/resources/cheatsheets/)

2.  Google + Stackoverflow = [answer](http://bfy.tw/7E5L) (The let-me-google-that-for-you site is a bit snarky but the point is that it is easy to search for solutions in stack overflow using google)

------------------------------------------------------------------------

RStudio and Shiny are trademarks of RStudio, Inc.

[1] This Rcommander [intro](https://cran.r-project.org/doc/contrib/Karp-Rcommander-intro2.pdf) is a couple of years old and is less technical.

[2] For those wanting a more in depth and technical guide see the official cran [documentation](https://cran.r-project.org/web/packages/Rcmdr/Rcmdr.pdf) on Rcommander

[3] The code shown in this example is adapted from this site [site](http://buff.ly/2aOKpzY)
