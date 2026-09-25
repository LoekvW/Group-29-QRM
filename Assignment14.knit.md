---
title: "QRM II Graded Assignment (14)"
subtitle: "Period 1, 2026"
author: "group 29: Thea von Sydow, Loek van Wijk, Thomas Dop, Anastasios Goudras and Tim de Marez Oyens" 
date:  "25-09-2026"
output:
  pdf_document:
    number_sections: true
  html_document:
    df_print: paged

header-includes:
- "\\setcounter{section}{-1}"
- |
  \usepackage{fvextra}
  \DefineVerbatimEnvironment{Highlighting}{Verbatim}{
    showspaces = false,
    showtabs = false,
    breaklines,
    commandchars=\\\{\}
  }
format:
  html:
    code-overflow: wrap
---


# Introduction

This assignment is to be completed in groups of 4-5. Further, all students in your group need to be assigned to the same R tutorial group (Friday's tutorial). You can sign yourself up for a group on Canvas. Please do so \textbf{before the start of your first R tutorial on Friday September 4th.} You can use the Discussion Board in Canvas if you do not have a group yet or if your group is incomplete.

The assignment has 5 parts, and each part corresponds to the course material of that week (with the exclusion of week 6, for which there is no R programming material). 

You are supposed to hand in these assignments on Canvas at the following dates:

  - **Deadline 1** *Sunday September 27th, at 23:59pm*: you are supposed to hand in weeks 1, 2, and 3 of this assignment.   This will determine 18\% of your overall course grade
  - **Deadline 2** *Sunday October 11th, at 23:59pm*: you are supposed to hand in weeks 4, and 5 of this assignment. This will determine 12\% of your overall course grade 

The R tutorials (each Friday) will consist of two halves. During the first half, you will discuss the tutorial exercises. These can be downloaded separately from Canvas. During the second half, you can work on this graded assignment within your own group. The purpose is that you find out how to work with R for doing statistical analyses by yourself. The tutorial exercises are meant to teach you basic commands to get you started, but to answer the problem sets in this assignment, you might need to research your own solutions, and use functions and commands not described in the tutorial exercises. Learning how to solve your own research problems is integral part of learning R. When you and your group get stuck on how to approach an exercise, the hierarchy in finding your way is as follows:

-	use the concepts from the tutorial exercises;
- use the cheat sheets available on Canvas;
-	use Google, YouTube, StackOverflow, or another website;
- ask the teacher.

The use of generative AI is \textbf{not} permitted and may result in a grade of 0. See the AI protocol in the course manual for details.

To answer the assignment, you can simply fill out this R markdown document. There are designated places which you can fill with R code. There are also designated spaces for you to answer each question. Often, the structure of an answer will be as follows. First, you type the R code in the designated box. This will show how you analyzed the data to get the answer to the question. Below the box for the R code, you will then summarize your answer to the question, i.e. what are the conclusions that you draw from the data analysis? 

When handing in, you are supposed to submit this .Rmd file, and a knitted version of this document. You can knit this document to pdf, word, or html. Knitting to pdf requires you to have a .tex distribution installed on your computer. Knitting to Word requires you to have Word installed. 

The exercises are designed such that you should be able to finish the majority of them during the tutorial each week. If you are not able to finish them fully during that time, you are expected to work on it in your own time using the computers on campus or your own device. It is best to meet as a group in-person when working together. If you want to work remotely, github is a good platform to guarantee smooth collaboration. Alternatively, you can email this .Rmd file back and forth to one another as a group, but this is not recommended as it is more cumbersome.

We encourage you to keep your code blocks, printing statements, and final answers, as short as possible. In any case, there is a page limit of 6 pages per week, which encompasses the total length of this document which consists of the questions, your coding lines, and your answers. When your answers to questions of the respective week exceed this page limit, they will not be graded, resulting in zero points.

Each week consists of 1, 2, or 3 subquestions. The total amount of points you can earn per week is 20 points. 

# Week 1 

1.  Find the dataset “movies1.tsv” on Canvas. Describe your data set: How many observations does it have. How many variables are there? How many subjects?   What consists of a subject? \textbf{[4 points]}


``` r
library(readr)
movies1 <- read_tsv("movies1.tsv")
```

```
## Rows: 505 Columns: 19
## -- Column specification --------------------------------------------------------
## Delimiter: "\t"
## chr   (8): keywords, original_language, title, genre, first_actor, first_act...
## dbl  (10): index, budget, popularity, revenue, runtime, vote_average, vote_c...
## date  (1): release_date
## 
## i Use `spec()` to retrieve the full column specification for this data.
## i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

``` r
nrow(movies1)
```

```
## [1] 505
```

``` r
ncol(movies1)
```

```
## [1] 19
```

**Your Answer:**

Write your response here.
it has 19 variables
it has 505 subjects
it has 

2. Which of the following types of variables are present in your data set? (i) nominal; (ii) ordinal; (iii); interval; (iv) ratio. If present, name one example of such a variable present in your data set. \textbf{[4 points]}


``` r
str(movies1)
```

```
## spc_tbl_ [505 x 19] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
##  $ index              : num [1:505] 1773 2540 1174 3262 4324 ...
##  $ budget             : num [1:505] 2.70e+07 1.50e+07 4.00e+07 0.00 0.00 1.20e+08 2.80e+07 7.00e+07 1.25e+07 4.00e+07 ...
##  $ keywords           : chr [1:505] "fbi island serial killer series of murders" "fire winter santa claus snow storm christmas tree" "police sequel police officer brother-in-law brother-in-law relationship black men" "masseuse thanksgiving party romance mother daughter relationship" ...
##  $ original_language  : chr [1:505] "en" "en" "en" "en" ...
##  $ title              : chr [1:505] "Mindhunters" "Krampus" "Ride Along 2" "Enough Said" ...
##  $ popularity         : num [1:505] 17.194 31.565 25.136 14.969 0.148 ...
##  $ release_date       : Date[1:505], format: "2004-05-07" "2015-11-26" ...
##  $ revenue            : num [1:505] 2.11e+07 6.15e+07 1.25e+08 2.53e+07 0.00 ...
##  $ runtime            : num [1:505] 106 98 102 93 97 130 108 99 100 99 ...
##  $ vote_average       : num [1:505] 6.3 5.9 6.1 6.6 6 6.2 5.5 4.4 6 6.2 ...
##  $ vote_count         : num [1:505] 333 584 555 348 9 597 640 533 210 371 ...
##  $ genre              : chr [1:505] "Thriller" "Comedy" "Comedy" "Drama" ...
##  $ release_year       : num [1:505] 2004 2015 2016 2013 2006 ...
##  $ release_month      : num [1:505] 5 11 1 9 10 3 2 1 2 9 ...
##  $ release_day        : num [1:505] 7 26 14 18 27 15 4 10 14 29 ...
##  $ first_actor        : chr [1:505] "LL Cool" "Adam Scott" "Kevin Hart" "Julia Louis-Dreyfus" ...
##  $ first_actor_gender : chr [1:505] NA "male" "male" "female" ...
##  $ director_first_name: chr [1:505] "Renny" "Michael" "Tim" "Nicole" ...
##  $ director_gender    : chr [1:505] "male" "male" "male" "female" ...
##  - attr(*, "spec")=
##   .. cols(
##   ..   index = col_double(),
##   ..   budget = col_double(),
##   ..   keywords = col_character(),
##   ..   original_language = col_character(),
##   ..   title = col_character(),
##   ..   popularity = col_double(),
##   ..   release_date = col_date(format = ""),
##   ..   revenue = col_double(),
##   ..   runtime = col_double(),
##   ..   vote_average = col_double(),
##   ..   vote_count = col_double(),
##   ..   genre = col_character(),
##   ..   release_year = col_double(),
##   ..   release_month = col_double(),
##   ..   release_day = col_double(),
##   ..   first_actor = col_character(),
##   ..   first_actor_gender = col_character(),
##   ..   director_first_name = col_character(),
##   ..   director_gender = col_character()
##   .. )
##  - attr(*, "problems")=<pointer: 0x0000019fbeaffd50>
```

``` r
summary(movies1)
```

```
##      index          budget               keywords   original_language
##  Min.   :   0   Min.   :        0   Length   :505   Length   :505    
##  1st Qu.:1056   1st Qu.:        0   N.unique :447   N.unique : 13    
##  Median :2283   Median : 15000000   N.blank  :  0   N.blank  :  0    
##  Mean   :2335   Mean   : 31694006   Min.nchar:  3   Min.nchar:  2    
##  3rd Qu.:3581   3rd Qu.: 45000000   Max.nchar:129   Max.nchar:  2    
##  Max.   :4796   Max.   :250000000   NAs      : 53                    
##                                                                      
##        title       popularity         release_date           revenue         
##  Length   :505   Min.   :2.386e-03   Min.   :1990-01-19   Min.   :0.000e+00  
##  N.unique :505   1st Qu.:4.759e+00   1st Qu.:2002-04-12   1st Qu.:0.000e+00  
##  N.blank  :  0   Median :1.414e+01   Median :2007-06-01   Median :1.948e+07  
##  Min.nchar:  3   Mean   :2.283e+01   Mean   :2006-11-25   Mean   :9.482e+07  
##  Max.nchar: 62   3rd Qu.:2.985e+01   3rd Qu.:2012-05-25   3rd Qu.:1.043e+08  
##                  Max.   :2.037e+02   Max.   :2016-08-02   Max.   :2.788e+09  
##                                                                              
##     runtime     vote_average     vote_count            genre      release_year 
##  Min.   :  0   Min.   :0.000   Min.   :    0.0   Length   :505   Min.   :1990  
##  1st Qu.: 94   1st Qu.:5.600   1st Qu.:   47.0   N.unique : 13   1st Qu.:2002  
##  Median :103   Median :6.200   Median :  255.0   N.blank  :  0   Median :2007  
##  Mean   :107   Mean   :6.043   Mean   :  802.9   Min.nchar:  5   Mean   :2006  
##  3rd Qu.:118   3rd Qu.:6.800   3rd Qu.:  914.0   Max.nchar: 11   3rd Qu.:2012  
##  Max.   :276   Max.   :8.100   Max.   :11800.0   NAs      :  5   Max.   :2016  
##  NAs    :1                                                                     
##  release_month     release_day       first_actor  first_actor_gender
##  Min.   : 1.000   Min.   : 1.00   Length   :505   Length   :505     
##  1st Qu.: 4.000   1st Qu.: 8.00   N.unique :405   N.unique :  2     
##  Median : 8.000   Median :15.00   N.blank  :  0   N.blank  :  0     
##  Mean   : 6.968   Mean   :15.29   Min.nchar:  6   Min.nchar:  4     
##  3rd Qu.:10.000   3rd Qu.:23.00   Max.nchar: 23   Max.nchar:  6     
##  Max.   :12.000   Max.   :31.00   NAs      :  8   NAs      : 23     
##                                                                     
##  director_first_name  director_gender
##  Length   :505       Length   :505   
##  N.unique :266       N.unique :  2   
##  N.blank  :  0       N.blank  :  0   
##  Min.nchar:  2       Min.nchar:  4   
##  Max.nchar: 14       Max.nchar:  6   
##  NAs      :  6       NAs      : 35   
## 
```

``` r
head(movies1)
```

```
## # A tibble: 6 x 19
##   index  budget keywords original_language title popularity release_date revenue
##   <dbl>   <dbl> <chr>    <chr>             <chr>      <dbl> <date>         <dbl>
## 1  1773  2.70e7 fbi isl~ en                Mind~     17.2   2004-05-07    2.11e7
## 2  2540  1.5 e7 fire wi~ en                Kram~     31.6   2015-11-26    6.15e7
## 3  1174  4   e7 police ~ en                Ride~     25.1   2016-01-14    1.25e8
## 4  3262  0      masseus~ en                Enou~     15.0   2013-09-18    2.53e7
## 5  4324  0      christi~ en                Fait~      0.148 2006-10-27    0     
## 6   214  1.20e8 u.s. ai~ en                The ~     25.8   2000-03-15    3.26e8
## # i 11 more variables: runtime <dbl>, vote_average <dbl>, vote_count <dbl>,
## #   genre <chr>, release_year <dbl>, release_month <dbl>, release_day <dbl>,
## #   first_actor <chr>, first_actor_gender <chr>, director_first_name <chr>,
## #   director_gender <chr>
```

**Your Answer:**

Write your response here.
All four data types are present
Nominal - genre
ordinal - release_month
interval - release_date
ratio - budget


3. A movie studio wants to know which types of movies give maximal profit. Perform the following steps to provide the movie studio with an analysis which corresponds to their request:

a. Create the variable profits as the revenue of a movie minus its budget. Report its mean, median, maximum, and minimum. \textbf{[2 points]}

b. Which movie has the highest profits in your data set and how much are these profits. Which movie has the lowest and how much are its profits? If multiple movies have the exact same highest or lowest profits, give only one example. \textbf{[2 points]}

c. Create a boxplot of the variable profits. Make sure it has an appropriate title, and appropriate titles and labels for the x- and y-axis. Give Q1, Q2, Q3, and Q4. What does this tell you about the nature of making money in the movies industry? \textbf{[2 points]}

d. Add a new variable to your data set the log of profits. When creating this variable, what happens to movies for which profits is zero or negative? What then happens when you calculate the mean of log of profits? \textbf{[2 points]}

e. For movies that have a profit of zero or less, replace log of profits with "NA". What is now the mean of log of profits? Create a boxplot for log of profits, again with an appropriate title, x- and y-axis labels. How does it compare to the boxplot you made under c.)? \textbf{[2 points]}

f. Create a scatterplot of with the runtime of movies on the x-axis and the average vote of movies on the y-axis. What do you conclude from the scatterplot? Are movies with a longer runtime considered worse or better by the audience, or does the audience not have a preference? Why do you think this is the case? \textbf{[2 points]}  

For each step, you should provide first all the code you used to answer the question and then formulate an answer using full sentences.

*Step a*


``` r
library(readr)

movies1 <- read_tsv("movies1.tsv", show_col_types = FALSE)

movies1$profits <- movies1$revenue - movies1$budget

mean(movies1$profits)
```

```
## [1] 63121475
```

``` r
median(movies1$profits)
```

```
## [1] 1900000
```

``` r
max(movies1$profits)
```

```
## [1] 2550965087
```

``` r
min(movies1$profits)
```

```
## [1] -9e+07
```

**Your Answer: After creating profits as revenue minus budget, the average profit across the 505 movies is $63,121,475, but the median is only $1,900,000. Profits range from a low of -$90,000,000 (a loss) up to a high of $2,550,965,087. The big gap between the mean and median already suggests the data is skewed, since a few really successful movies are dragging the average up while most movies make much less.

*Step b*


``` r
movies1$profit <- movies1$revenue - movies1$budget

highest_profit_movie <- movies1[which.max(movies1$profit), ]
highest_profit_movie[, c("title", "profit")]
```

```
## # A tibble: 1 x 2
##   title      profit
##   <chr>       <dbl>
## 1 Avatar 2550965087
```

``` r
lowest_profit_movie <- movies1[which.min(movies1$profit), ]
lowest_profit_movie[, c("title", "profit")]
```

```
## # A tibble: 1 x 2
##   title               profit
##   <chr>                <dbl>
## 1 Mighty Joe Young -90000000
```

**Your Answer:**

The highest profit is Avatar, which has a profit of 2,550,965,087 dollars
The lowest profit is Mighty Joe Young, which has a loss of 90,000,000 dollars

*Step c*


``` r
library(ggplot2)
movies1$profit <- movies1$revenue - movies1$budget
quantile(movies1$profit, na.rm = TRUE)
```

```
##         0%        25%        50%        75%       100% 
##  -90000000          0    1900000   60514050 2550965087
```

``` r
ggplot(movies1, aes(x = "", y = profit)) +
  geom_boxplot(fill = "gray", color = "black", outlier.color = "red") +
  labs(
    title = "Distribution of Movie Profits",
    x = "Movies",
    y = "Profit"
  ) +
  theme_minimal()
```

![](Assignment14_files/figure-latex/unnamed-chunk-5-1.pdf)<!-- --> 

**Your Answer:**
The movie industry is very high risk high reward, whilst most movies either break even or make a small profit, or a small loss, only a low amount of movies actually make a large profit

*Step d*


``` r
movies1$logprofits <- log(movies1$profits)
```

```
## Warning in log(movies1$profits): NaNs produced
```

``` r
mean(movies1$logprofits)
```

```
## [1] NaN
```

**Your Answer:**

When we take the log of profits, movies with a profit of exactly zero end up as -Inf, since the log of zero is undefined and trends toward negative infinity. Movies with negative profits (losses) turn into NaN, because you can't take the log of a negative number at all. R even throws a warning about this, saying "NaNs produced." Since 116 of the 505 movies in the data set have profits of zero or less, all of these rows get one of these problematic values instead of a real number.

Because of this, when we calculate the mean of logprofits, the result is NaN. R can't average a column that contains undefined values like NaN and -Inf alongside normal numbers, so the whole calculation breaks down, even though most of the individual values are perfectly fine..

*Step e*


``` r
movies1$profit <- movies1$revenue - movies1$budget
movies1$log_profit <- log(movies1$profit)
```

```
## Warning in log(movies1$profit): NaNs produced
```

``` r
movies1$log_profit[movies1$profit <= 0] <- NA
mean_log_profit <- mean(movies1$log_profit, na.rm = TRUE)
mean_log_profit
```

```
## [1] 17.38094
```

``` r
ggplot(movies1[!is.na(movies1$log_profit), ], aes(x = "", y = log_profit)) +
  geom_boxplot(fill = "gray", color = "black", outlier.color = "red") +
  labs(
    title = "Distribution of log-transformed movie profits",
    x = "Profitable movies",
    y = "Log of profit"
  ) +
  theme_minimal()
```

![](Assignment14_files/figure-latex/unnamed-chunk-7-1.pdf)<!-- --> 

**Your Answer:**

The boxplot in C had a lot of massive outliers, whilst this one is a bit more centered arount its median.
plus the boxplot in C had a lot more movies, since we deleted all the once making a loss or breaking even

*Step f*


``` r
plot(movies1$runtime, movies1$vote_average,
     main = "Runtime vs Average Vote",
     xlab = "Runtime (minutes)",
     ylab = "Average Vote")
```

![](Assignment14_files/figure-latex/unnamed-chunk-8-1.pdf)<!-- --> 

``` r
cor(movies1$runtime, movies1$vote_average, use = "complete.obs")
```

```
## [1] 0.3211682
```

This gives a correlation of about 0.32 between runtime and average vote.
Looking at the scatterplot, most movies cluster between about 90 and 130 minutes with average votes somewhere between 5 and 7.5, and there's a mild upward trend running through the cloud of points. Longer movies do tend to get slightly higher ratings on average, but the relationship is pretty weak, since a correlation of 0.32 means runtime only accounts for a small part of the variation in how movies get rated.
So overall, audiences seem to have a slight preference for longer movies, but it's not a strong effect. A likely reason is that longer runtimes often go along with bigger productions, more developed stories, and higher budgets, things like epics or dramas that studios invest more time and money into tend to run longer, and that extra effort may translate into somewhat better reception.

# Week 2 
1 Is your dataset movies1.tsv the full population, or is it a sample of a larger population? If the latter, how would you describe the full population? \textbf{[4 points]}

**Your Answer:**

It is a sample of a larger population, the full population would include every single movie made globally, and since this dataset only includes 505 movies, it is a sample.

2
a.  For which actor in your data set do you observe the most movies? \textbf{[2 points]} 
b.  What is the average revenue of the movie in which this actor plays and does the revenue lie above or below the revenue of an average movie according to your data set? \textbf{[2 points]}  
c.  How trustworthy do you consider your conclusion to answer 2b? Use the term "law of large numbers" in your explanation. \textbf{[2 points]} 

*step a*


``` r
library (dplyr)
```

```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

``` r
movies1 %>%
  filter(!is.na(first_actor)) %>%
  count(first_actor, sort = TRUE) %>%
  head(1)
```

```
## # A tibble: 1 x 2
##   first_actor      n
##   <chr>        <int>
## 1 Bruce Willis     7
```

**Your Answer:**
The actor with the most movies (in this sample) is Bruce Willis who has 7 movies (in this sample).

*step b*


``` r
movies_bruce <- subset(movies1, first_actor == "Bruce Willis")
Average_revenue_Bruce <- mean(movies_bruce$revenue, na.rm = TRUE)

Average_Revenue <- mean(movies1$revenue, na.rm = TRUE)
```

**Your Answer:**

The average revenue for a Bruce Willis film is 116,280,089.57 U.S. Dollars
The average revenue for all the movies is 94,815,481.64 U.S. Dollars

This means that the average Bruce Willis movie generates more revenue than the average movie from this sample.

*step c*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**


It is not very trustworthy since this sample is only a small percentage of all movies made.
According to the law of large numbers, the more movies you add to the sample, the closer you would get to the 'true mean'. 
And since we are only analyzing 505 movies and 7 Bruce Willis movies, the possibility is very large that the answer is distorted. (e.g. there could be one massive outlier which manipulates the outcome)



3 For this question, you will assume that your data set is the full population. 

a. Recode profits such that it is expressed in millions. What is the variance of the variable profits (in millions) in your data set? \textbf{[2 points]}
b. Create a new data set, called movies_sample. Make sure that it is a random sample of your data set of 25 movies. What is the variance of profits in this random sample? How does it compare to the variance of profits in 2a? \textbf{[2 points]}
c. In a for loop, create 100 different samples of 25 movies, as in b, and estimate the variance within each sample. Save the variance of each sample in a vector called sample_vars. So the first position of the vector would have the variance of the first sample, the second position the variance of the second sample, etc. Print the start of this vector. \textbf{[2 points]}
d. Summarize and make a histogram of sample_vars. What is the mean, standard deviation and shape of its distribution? \textbf{[2 points]}
e. In your opinion, is a sample of 25 movies sufficient to get a reliable estimate of the population variance of profits, using the sample variance? Explain? \textbf{[2 points]}

*step a*


``` r
movies1$profits <- movies1$revenue - movies1$budget
movies1$profits_millions <- movies1$profits / 1e6 

n <- nrow(movies1)
pop_var <- var(movies1$profits_millions, na.rm = TRUE) * (n - 1)/n 
pop_var
```

```
## [1] 30402.8
```

**Your Answer:**
After recoding profits into millions and treating the dataset as the full population, the population variance of profits is 30,402.8 (million dollars squared). This gives a standard deviation of about $174 million, which is large compared to the mean profit of roughly $63 million. This makes sense given the skewed nature of the data, since a small number of blockbuster movies like Avatar generate profits far above the typical movie, which pulls the variance up a lot.


*step b*


``` r
set.seed(123)
movies_sample<- movies1[sample(nrow(movies1), 25),]

sample_var <- var(movies_sample$profits_millions, na.rm = TRUE)
sample_var
```

```
## [1] 5156.149
```

**Your Answer:**

The variance of profits in the random sample of 25 movies is 5156.149 (million dollars squared), which is much lower than the population variance of 30,402.8 found in 2a. This difference is likely because the profits distribution is highly skewed, with a small number of blockbuster movies driving up the variance in the full population. A sample of just 25 movies has a good chance of missing these extreme outliers entirely, which would make the sample variance look much smaller than the true population variance. This shows that with such a skewed variable, small samples can give quite unreliable estimates of the population variance, just by chance.

*step c*


``` r
sample_vars <- numeric(100)

for (i in 1:100) {
sample_i <- movies1[sample(nrow(movies1), 25), ]  
sample_vars[i] <- var(sample_i$profits_millions, na.rm=TRUE)
}
head(sample_vars)
```

```
## [1]  3141.213  2110.105  3441.955 20740.620  1686.073  3680.152
```

**Your Answer:**

The first six values are 1467.470, 4811.677, 23420.599, 20283.804, 3148.406, and 26480.444. These values already show a lot of variation from sample to sample, which reflects how sensitive the variance estimate is to which movies happen to end up in a small sample of 25, especially given how skewed the underlying profits distribution is.

*step d*


``` r
library(ggplot2)
mean_var <- mean(sample_vars)
sd_var <- sd(sample_vars)

mean_var
```

```
## [1] 24755.5
```

``` r
sd_var
```

```
## [1] 43528.21
```

``` r
df_vars <- data.frame(sample_vars = sample_vars)

ggplot(df_vars, aes(x = sample_vars)) +
  geom_histogram(bins = 30, fill = "blue", color = "black", alpha = 0.7) +
  labs(
    title = "title = Distribution of variances sample",
    x = "sample variances",
    y = "frequency"
  ) +
  theme_minimal()
```

![](Assignment14_files/figure-latex/unnamed-chunk-15-1.pdf)<!-- --> 

**Your Answer:**

the mean of sample_vars is equal to the population variance of the movie population, which is approximately 3.05 x 10^16.

The standard deviation of sample_vars is 5.54 x 10^16

The Histogram is extremely right tailed

*step e*

**Your Answer:**

no, a sample size of 25 is not sufficient. 
This is because a single mega hit amongst those 25 can extremely influence the variance of the sample 

**Your answer here**

# Week 3 

For the next part of the assignment, assume that the movies in your data frame are a random sample of a larger population of movies. 

1

a. Create a new data set that only includes movies that are of the genre "Thriller". For these thriller movies, give a 99 percent confidence interval for the variable *runtime*. Interpret the result. \textbf{[2 points]}
b. Now, assume that the variance of *runtime* amongst thriller movies in your data is exactly the same as the variance of *runtime* in the population. Under this assumption, give a 99 percent confidence interval for the variable *runtime* among thriller movies. Interpret the result. Is you confidence interval wider or less wide than the one you found under question 1a? Why is that the case? \textbf{[2 points]}

*step a*


``` r
thrillers <- subset(movies1, genre == "Thriller")
xbar  <- mean(thrillers$runtime, na.rm = TRUE)
s     <- sd(thrillers$runtime, na.rm = TRUE)
n     <- sum(!is.na(thrillers$runtime))
se    <- s / sqrt(n)
tcrit <- qt(0.995, df = n - 1)
c(xbar - tcrit * se, xbar + tcrit * se)
```

```
## [1]  99.94343 111.01042
```

**Your Answer:**

We're 99% confident the true mean runtime of all thriller movies lies between 99.94 and 111.01 minutes.

*step b*


``` r
zcrit <- qnorm(0.995)
c(xbar - zcrit * se, xbar + zcrit * se)
```

```
## [1] 100.1081 110.8457
```

**Your Answer:**

The 99% confidence interval is [100.11, 110.85]. It is narrower than in part a. This is because we now assume the population variance is known, so we use the z (normal) distribution instead of the t distribution. Its critical value is smaller, which gives a narrower interval.

2

a. Using an appropriate five-step procedure, set up a test for the null hypothesis that the variance of runtime equals $500$. Clearly state your null hypothesis, alternative hypothesis your test statistic, your critical value, and your conclusion. \textbf{[2 points]}
b. For the validity of your test in 2a, what assumption about the distribution of runtime needs to hold? Make an appropriate plot to test this assumption. What do you conclude? \textbf{[2 points]}

*step a*


``` r
x  <- na.omit(movies1$runtime)
n  <- length(x)
s2 <- var(x)
chi2 <- (n - 1) * s2 / 500
crit <- qchisq(c(0.025, 0.975), df = n - 1)
pval <- 2 * min(pchisq(chi2, n - 1), 1 - pchisq(chi2, n - 1))
round(c(n = n, s2 = s2, chi2 = chi2, crit_low = crit[1], crit_high = crit[2], p = pval), 3)
```

```
##         n        s2      chi2  crit_low crit_high         p 
##   504.000   483.097   485.996   442.750   567.037     0.602
```

1. **Hypotheses:** $H_0: \sigma^2 = 500$ versus $H_1: \sigma^2 \neq 500$ (two-sided).
2. **Significance level:** $\alpha = 0.05$.
3. **Test statistic:** $\chi^2 = (n-1)s^2/\sigma_0^2$, which under $H_0$ follows a $\chi^2$ distribution with $n-1 = 503$ degrees of freedom. With $n = 504$ movies (one has a missing runtime) and $s^2 = 483.10$, we get $\chi^2 = 503 \cdot 483.10/500 = 486.00$.
4. **Critical values:** reject $H_0$ if $\chi^2 < 442.75$ or $\chi^2 > 567.04$.
5. **Conclusion:** $\chi^2 = 486.00$ lies between the two critical values (p = 0.60), so we do not reject $H_0$. At the 5% level there is no evidence that the population variance of runtime differs from 500.

*step b*


``` r
par(mfrow = c(1, 2))
hist(x, breaks = 40, freq = FALSE, main = "Histogram of runtime",
     xlab = "Runtime (minutes)")
curve(dnorm(x, mean = mean(x), sd = sd(x)), add = TRUE, col = "red", lwd = 2)
qqnorm(x, main = "Normal Q-Q plot of runtime")
qqline(x, col = "red", lwd = 2)
```

![](Assignment14_files/figure-latex/unnamed-chunk-19-1.pdf)<!-- --> 

``` r
par(mfrow = c(1, 1))
```

**Your Answer:**

The question says revenue, but the test is about runtime. The $\chi^2$ test for a variance is only valid if runtime is normally distributed in the population, and unlike tests on the mean it stays sensitive to this even in large samples. The histogram shows that runtime is not normal: it is right-skewed, with a long upper tail (up to 276 minutes) and a few values of 0 that look like missing data. In the Q-Q plot the points bend away from the line in both tails, most clearly in the upper tail. The normality assumption is therefore violated, so the conclusion in 2a should be treated with caution.

3. There is an argument going on in the movie studio. *Bob* claims that they should make higher-quality movies, as this will bring in more profits. *Chantal* disagrees. She tells Bob that mediocre movies bring in the most profits. You are asked to advise on who is right.

a. Create a new variable called vote_average_rounded. Make sure this variable is the same as vote_average, but without any decimals (i.e., a 6.3 becomes a 6, a 8.7 an 8, etc.). Display a histogram of vote_average_rounded. \textbf{[2 points]}
b. Create a scatter plot with vote_average_rounded on the x axis and the mean of profits within each category of vote_average_rounded on the y-axis. Make sure it has an appropriate title, and appropriate titles and labels for the x- and y-axis. At which rating of movies are profits the highest? \textbf{[3 points]}
c. Recreate the scatter plot with year on the x axis and mean_profits on the y-axis, but now add bars around each point, indicating the 95\% confidence interval. \textbf{[3 points]}
d. Write an advice to settle the argument between Bob and Chantal. \textbf{[4 points]}

*step a*


``` r
movies1$vote_average_rounded <- floor(movies1$vote_average)
hist(movies1$vote_average_rounded, breaks = seq(-0.5, 10.5, by = 1),
     main = "Histogram of rounded-down vote average",
     xlab = "Vote average (rounded down)", ylab = "Number of movies")
```

![](Assignment14_files/figure-latex/unnamed-chunk-20-1.pdf)<!-- --> 

**Your Answer:**

We use `floor()`, which drops the decimals (6.7 becomes 6), rather than `round()` (which would turn 6.7 into 7). Most movies have a rating of 5 (142 movies) or 6 (222), followed by 7 (83) and 4 (36). High ratings are rare: only 5 movies score 8 and none score 9 or 10. The 8 movies with a rating of 0 all have zero votes, so their 0 is really a missing rating.

*step b*



``` r
mean_profits <- aggregate(profits ~ vote_average_rounded, data = movies1, FUN = mean)
plot(mean_profits$vote_average_rounded, mean_profits$profits / 1e6, pch = 19,
     main = "Mean profit by movie rating",
     xlab = "Vote average (rounded down)", ylab = "Mean profit (millions of $)")
```

![](Assignment14_files/figure-latex/unnamed-chunk-21-1.pdf)<!-- --> 


**Your Answer:**


Mean profits are highest for movies rated 8, at about \$168.7 million, followed by movies rated 7 (\$144.1 million). Profits rise steadily with the rating: movies rated 5 and 6 make on average \$43.1 and \$56.5 million, and movies rated 4 or lower make close to nothing.

*step c*


``` r
ci <- do.call(data.frame, aggregate(profits ~ vote_average_rounded, data = movies1,
        FUN = function(v) c(mean = mean(v), sd = sd(v), n = length(v))))
names(ci) <- c("rating", "mean", "sd", "n")
ci$lower <- (ci$mean - qt(0.975, ci$n - 1) * ci$sd / sqrt(ci$n)) / 1e6
ci$upper <- (ci$mean + qt(0.975, ci$n - 1) * ci$sd / sqrt(ci$n)) / 1e6
ci$mean  <- ci$mean / 1e6
plot(ci$rating, ci$mean, pch = 19, ylim = range(c(ci$lower, ci$upper)),
     main = "Mean profit by movie rating with 95% confidence intervals",
     xlab = "Vote average (rounded down)", ylab = "Mean profit (millions of $)")
arrows(ci$rating, ci$lower, ci$rating, ci$upper, angle = 90, code = 3, length = 0.05)
```

![](Assignment14_files/figure-latex/unnamed-chunk-22-1.pdf)<!-- --> 

``` r
round(ci[, c("rating", "n", "mean", "lower", "upper")], 1)
```

```
##   rating   n  mean  lower upper
## 1      0   8   0.0    0.0   0.0
## 2      2   4   0.2   -1.1   1.6
## 3      3   5  -2.9   -8.7   3.0
## 4      4  36  11.8   -0.3  23.9
## 5      5 142  43.1   23.7  62.6
## 6      6 222  56.5   40.1  72.9
## 7      7  83 144.1   72.9 215.3
## 8      8   5 168.7 -231.6 569.1
```

**Your Answer:**

We interpret "year" in the question as vote_average_rounded, since the question asks to recreate the plot from 3b. The intervals are narrow for ratings 5 and 6 (\$23.7–62.6 million and \$40.1–72.9 million), where there are many movies. For rating 7 the interval is \$72.9–215.3 million, which lies entirely above the intervals of ratings 5 and 6. The interval for rating 8 is extremely wide (–\$231.6 to \$569.1 million) because it is based on only 5 movies, so its high mean is very uncertain.

*step d*

**Your Answer:**

The data support Bob rather than Chantal. Mediocre movies (ratings 5–6) earn on average \$43–56 million, while good movies rated 7 earn about \$144 million, and the 95% confidence intervals of these groups do not overlap. Movies rated 8 have the highest mean profit, but with only 5 such movies this estimate is too uncertain to rely on. There is no evidence that mediocre movies are the most profitable.

We would still add two caveats. First, this is a correlation, not proof that quality causes profit: better-rated movies may also have bigger budgets, famous casts, franchises or more marketing, and popular movies may attract higher ratings rather than the other way around. Second, many movies in the data have a budget or revenue of 0, which is probably missing data and distorts the profit figures. Our advice is that the studio should aim for well-received (7+) movies, and confirm the effect of quality with an analysis that controls for budget and genre.



``` r
library(tinytex)
library(knitr)
```





# Week 4 

1. There is another argument going on in the movie studio. *Bob* claims that production budgets are getting out of hand, and that the studio should focus on making cheaper movies. *Chantal* disagrees. She tells Bob that ``Every dollar we spend on movie production is more than offset by the increase in movie profits''. 

a. Set up a regression model to test Chantal's claim, and estimate it. That is, estimate: $$\text{Profits}_i=\beta_0+\beta_1 \text{Budget}_i +\varepsilon_i.$$ Print a summary of your estimated model. \textbf{[2 points]}
b. What is the estimated value of $\beta_1$ and how do you interpet it? \textbf{[2 points]}
c. Test for the null hypothesis that $\beta_1 \geq 0$. Report the p-value and state your conclusion. \textbf{[2 points]} 
d. Next, estimate the model $$\text{Log Profits}_i=\beta_0+\beta_1 \text{Log Budget}_i +\varepsilon_i.$$ When creating the variables Log Profits and Log Budget, make sure that movies with a Revenue or Budget of zero are assigned the value "NA". Print a summary of your estimated model \textbf{[2 points]}
e. What is the estimated value of $\beta_1$ and how do you interpet it? \textbf{[2 points]}
f. Which model has better fit? The level-level model or the log-log model? Explain. \textbf{[2 points]}
g. Who do you think is correct? Bob or Chantal? What would you advise the movie studio to do? \textbf{[2 points]}

*step a*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

*step b*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

*step c*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

*step d*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

*step e*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

*step f*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

*step g*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

2

a. Make a plot with a 95% confidence interval with the mean log of budget on the y-axis, and whether the first actor of the movie is male or female on the x-axis. What do you conclude? \textbf{[2 points]} 
b. Estimate the following simple OLS model: $log(budget)_i=\beta_0+\beta_1 \text(FirstActorMale)_i + \varepsilon_i.$ Is the estimated coefficient for $\beta_1$ significantly different from zero? How do you interpret its estimate, and how does this relate to your conclusion in 2a? \textbf{[2 points]}
c. Now, have a close look at your data frame. Can you find any instances of male first actors who are wrongly labeled as being female, or vice versa? What would such mislabelling mean for the coefficient you estimated under 2b? \textbf{[2 points]}

*step a*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

*step b*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

*step c*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

# Week 5

a. Create a plot of the mean profits by month of release. Do you see any indication that month of release matters to the profits of the movie? \textbf{[2 points]}
b. Estimate an OLS model which has as dependent variable the log of profits of a movie, and as independent variable the log of budget, a dummy for whether the movie was released in english or not, and a linear term for the month of release. Show a summary of the resulting model and interpret each coefficient. \textbf{[4 points]}
c. Test for the hypothesis that the coefficient that belongs to month of release is zero. \textbf{[2 points]} 
d. Based on your plot in a.) do you consider the choice that month of release enters the model linearly under b.) reasonable? Estimate a specification that allows for a more flexible curve. In this new specification, test for the null hypothesis that month of release does not impact profits. This might require testing multiple terms at once. \textbf{[4 points]}

e. One executive at the studio wants to time the release of the movie to a specific month of the year such that they can maximize revenue. Based on your model under d.), What would you advise the movie studio regarding the timing of the release of the movie?  \textbf{[2 points]}

The movie studio that you work at is releasing a new movie in 2026. It will be an English-spoken Thriller movie with a budget of 40,000,0000. 

f. Estimate a model that is able to predict the revenue of this movie. Give its predicted revenue and include a 99% prediction interval.  \textbf{[6 points]}


*step a*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

*step b*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

*step c*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

*step d*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

*step e*


``` r
#WRITE YOUR CODE HERE
```

**Your Answer:**

Write your formulated response here.

*step f*



``` r
#WRITE YOUR CODE HERE
```

