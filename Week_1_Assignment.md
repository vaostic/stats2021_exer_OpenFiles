# Getting Started

## Introduction:

If you’re reading this you have successfully installed R and RStudio.
Good job!

This assignment is written as an Rmarkdown file and can be used to
generate formatted output. One of the advantages of this output is it
includes the code with the output. If you ever need to recreate an
analysis in the future, it’s probably more important to have a record of
the code used than the actual output. (Always save your code with your
data file(s).)

There are several different output formats available.You can see a list
at <https://rmarkdown.rstudio.com/lesson-9.html>

We’ll be using the output for markdown documents which display nicely on
GitHub. You can see the output type specified in the header section of
this assignment. (Scroll back to the top to see it.)

## Directions:

Complete each step of the assignment below.

## Package management in R

``` r
# keep a list of the packages used in this script
packages <- c("tidyverse","rio","jmv")
```

This next code block has eval=FALSE because you don’t want to run it
when knitting the file. Installing packages when knitting an R notebook
can be problematic.

``` r
# check each of the packages in the list and install them if they're not installed already
for (i in packages){
  if(! i %in% installed.packages()){
    install.packages(i,dependencies = TRUE)
  }
  # show each package that is checked
  print(i)
}
```

``` r
# load each package into memory so it can be used in the script
for (i in packages){
  library(i,character.only=TRUE)
  # show each package that is loaded
  print(i)
}
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ ggplot2   3.5.1     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.4     ✔ tidyr     1.3.1
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

    ## [1] "tidyverse"
    ## [1] "rio"
    ## [1] "jmv"

A note about working with packages and functions in R: When installing
packages you may see notifications that SomePackage::function() masks
OtherPackage::function(). What that means is that two different packages
used the same function name. The functions may or may not do the same
thing, but for whatever reason the pogrammers of each package happened
to choose the same name for a function in their respective package. The
last package installed will be the version of that function that will be
used if only the function name is used in your R code. The
SomePackage::function() notation with the colons in it means to use the
function named function() from the package named SomePackage. I think I
have decided when I write R code that I will always try to stick to that
notation. That way it’s very clear which package a desired function
comes from and there will be no problems with masking if different
packages used the same function name.

## Open a csv data file

CSV files can be opened using the menus in RStudio or by executing code.
Open your data file by using the menu (File - Import Dataset) or
executing the code block below to open the Week1.csv file. If you use
the menus, make sure to select From Text (readr)… We will use Tidyverse
packages as much as possible in this class. The readr package is a
Tidyverse package. The rio packages tries to make data import and export
simple. The following code block uses the rio import() function. When
you open the dataset, notice that a new Data object appears in the
Environment pane in the top right window of RStudio. (If the Environment
pane isn’t showing, click on the Environment tab.) You can see the
variables in the dataset by clicking on the circle with the triangle in
it next to the name of the data object. You can see the data in a
spreadsheet like window by clicking on the name of the data object.
Click on the tab with this assignment to come back to it after looking
at the dataset pane. Try both of them out.

``` r
# https://cran.r-project.org/web/packages/rio/vignettes/rio.html
library(rio)
csvdataset <- rio::import(file.choose())
```

## Open an Excel workbook

Excel files can be opened using the menus in RStudio or by executing
code. Open your data file by using the menu (File - Import Dataset) or
executing the code block below to open the Week1.xlsx file. The rio
packages tries to make data import and export simple. The following code
block uses the rio import() function. When you open the dataset, notice
that a new Data object appears in the Environment pane in the top right
window of RStudio. (If the Environment pane isn’t showing, click on the
Environment tab.) You can see the variables in the dataset by clicking
on the circle with the triangle in it next to the name of the data
object. You can see the data in a spreadsheet like window by clicking on
the name of the data object. Click on the tab with this assignment to
come back to it after looking at the dataset pane. Try both of them out.

``` r
# https://cran.r-project.org/web/packages/rio/vignettes/rio.html
library(rio)
xlsdataset <- rio::import(file.choose())
```

## Open an SPSS data file (.sav file)

SPSS data files can be opened using the menus in RStudio or by executing
code. Open your data file by using the menu (File - Import Dataset) or
executing the code block below to open the Week1.xlsx file. The rio
packages tries to make data import and export simple. The following code
block uses the rio import() function. When you open the dataset, notice
that a new Data object appears in the Environment pane in the top right
window of RStudio. (If the Environment pane isn’t showing, click on the
Environment tab.) You can see the variables in the dataset by clicking
on the circle with the triangle in it next to the name of the data
object. You can see the data in a spreadsheet like window by clicking on
the name of the data object. Click on the tab with this assignment to
come back to it after looking at the dataset pane. Try both of them out.

``` r
# https://cran.r-project.org/web/packages/rio/vignettes/rio.html
library(rio)
savdataset <- rio::import(file.choose())
```

## Datasets in R

R has a number of data set included with it. One of those datasets is
the cars dataset. Try executing the code chunk below by clicking the
*Run* button within the chunk or by placing your cursor inside it and
pressing *Ctrl+Shift+Enter*.

``` r
plot(cars)
```

![](Week_1_Assignment_files/figure-markdown_github/unnamed-chunk-7-1.png)

## Add a new code block

Add a new code chunk below this line by clicking the *Insert Chunk*
button on the toolbar or by pressing *Ctrl+Alt+I*.

``` r
View(cars)
```

## Save your output.

Save this assignment as a markdown file by following these steps:

1.  Click the preview or knit button at the top of this window.
    -   RStudio will execute each block of code and save the results to
        create the output. You may need to select each file like you did
        when you ran the code blocks one at a time.
    -   A popup should appear with all the output for the assignment.
    -   Or a page should appear in the Viewer pane in the bottom right
        corner of RStudio.
    -   If the button said knit, a new file should appear in the same
        folder as your .Rmd file with the same name. you can submit that
        file for your assignment.(You can check that by clicking on the
        Files tab to see if a new html file is in the folder. Click on
        the Viewer tab to go back to the output viewer.)
    -   If the button said Preview, you probably need to continue on to
        the next steps.
2.  Click the Open in Browser button or Show in New Window button at the
    top of that window.
    -   Your output should open up in your web browser.
3.  Save the page in the web browser.
    -   Usually you can right click and select save as…
    -   Or select save as from the browser menu

## Submit your assignment.

Submit the output you just saved for your assignment.
