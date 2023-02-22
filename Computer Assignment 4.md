# Computer Assignment 4
Names:

## Part A

### Code
```R
SRS <- 1000 #the number of repeats (not to be changed)
# n: the number of columns that are being averaged over. This changes for 
#    each run.
n <- 15 # CHANGE

# I strongly suggest that you change the titles to include the distribution.
# The number of columns that are being averaged over will automatically
# be updated if you use the following code.
title <- paste("Normal distribution: averaged over", n) #CHANGE

# calculate the average data – change the function in data.vec that 
#   corresponds to the distribution that you are using.
data.vec <- rnorm(SRS*n, mean = 0, sd = 1) #creates random normal data # CHANGE
data.mat <- matrix(data.vec, nrow = SRS) #separates the data into rows 

#apply(your data table/matrix, row/column index, function):
# The apply() function can apply the function of your choice to each row or 
#     each column of your data table/matrix.  
# Use 1 for the second argument ("row/column index") to apply the function to
#     each row; and use 2 for each column.
avg <- apply(data.mat, 1, mean) #performs the averaging – do not change

# histogarm, qq plot, mean, sd
library(ggplot2)
xbar <- mean(data.vec)
s <- sd(data.vec)
xbar
s
ggplot(data.frame(data.vec=data.vec), aes(x=data.vec)) + 
  geom_histogram(aes(y=..density..),bins = sqrt(length(data.vec))+2,
                 fill = "grey",col = "black") +
  geom_density(col = "red", lwd = 1) +
  stat_function(fun=dnorm, args=list(mean=xbar, sd=s), col="blue", 
                lwd = 1) +
  ggtitle(title) +
  xlab("Data") +
  ylab("Proportion") 

ggplot(data.frame(data.vec=data.vec), aes(sample=data.vec)) +
  stat_qq() +
  geom_abline(slope = s, intercept = xbar) +
  ggtitle(title)
```

### Histogram and Normal Probability Plots
![[normal, 1, hist.png|300]]

![[normal, 1, qq.png|300]]

![[normal, 3, hist.png|300]]

![[normal, 3, qq.png|300]]

![[normal, 7, hsit.png|300]]

![[normal, 7, qq.png|300]]

![[normal, 15, hist.png|300]]

![[normal, 15, qq.png|300]]

### Summary
|n|Experimental Mean|Theoretical Mean|Experimental Standard Deviation|Theoretical Standard Deviation|
|---|---|---|---|---|
|1|0.03039396|0.03039396|1.02001|1.02001|
|3|0.03518086|0.03518086|1.011688|1.011688 / sqrt(3) = 0.584098|
|7|0.01634966|0.01634966|1.004476|0.379656|
|15|0.005557436|0.005557436|0.9923302|0.256219|

## Part B

### Code 
```R
SRS <- 1000 #the number of repeats (not to be changed)
 # n: the number of columns that are being averaged over. This changes for 
 #    each run.
 n <- 15
 # I strongly suggest that you change the titles to include the distribution.
 # The number of columns that are being averaged over will automatically
 # be updated if you use the following code.
 title <- paste("Uniform distribution: averaged over", n)
 # calculate the average data – change the function in data.vec that 
 #   corresponds to the distribution that you are using.
 data.vec <- runif(SRS*n, min = -10, max = 50) #creates Uniform normal data
 data.mat <- matrix(data.vec, nrow = SRS) #separates the data into rows 
 #apply(your data table/matrix, row/column index, function):
 # The apply() function can apply the function of your choice to each row or 
 #     each column of your data table/matrix.  
 # Use 1 for the second argument ("row/column index") to apply the function to
 #     each row; and use 2 for each column.
 avg <- apply(data.mat, 1, mean) #performs the averaging – do not change
 meanData <- mean(data.vec)
 sdData <- sd(data.vec)
 meanData
[1] 19.87118
 sdData
[1] 17.37138
 library(ggplot2)
 ggplot(data.frame(data.vec=data.vec), aes(x=data.vec)) + 
   geom_histogram(aes(y=..density..),bins = sqrt(length(data.vec))+2,
                  fill = "grey",col = "black") +
   geom_density(col = "red", lwd = 1) +
   stat_function(fun=dnorm, args=list(mean=(meanData), sd=sdData), col="blue", 
                 lwd = 1) +
   ggtitle(title) +
   xlab("Data") +
   ylab("Proportion") # Need to use proportion with density curves
 #
 #Normal Probability Plot (AKA: QQ Plot)
 # We need the sample mean and standard deviation to plot the line. 
 #    We will use the values already calculated.
 ggplot(data.frame(data.vec=data.vec), aes(sample=data.vec)) +
   stat_qq() +
   geom_abline(slope = sdData, intercept = meanData) +
   ggtitle(title)
```

### Histogram and Normal Probability Plots

![[hist1.png|300]]

![[dot1.png|300]]

![[hist3.png|300]]

![[dot3.png|300]]

![[hist5.png|300]]

![[dot5.png|300]]

![[hist15.png|300]]

![[dot15.png|300]]

### Summary

## Part C

### Code
```R
SRS <- 1000
n <- 1

#Weibull

title <- paste("Weibull Distribution: avergaged over", n)

data.vec <- rweibull(SRS*n, shape = 40, scale = 20)
data.mat <- matrix(data.vec, nrow = SRS)

avg <- apply(data.mat, 1, mean)

RandomData <- data.vec
title <- "Weibull Distribution"

library(ggplot2)
xbar <- mean(RandomData)
s <- sd(RandomData)

# histogram
ggplot(data.frame(RandomData = RandomData), aes(x = RandomData)) + geom_histogram(aes(y = ..density..), bins = 30, fill = "grey", col = "black") + geom_density(col = "red", lwd = 1) + stat_function(fun = dnorm, args = list(mean = xbar, sd = s), col = "blue", lwd = 1) +ggtitle(title) + xlab("Data") + ylab("Proportion")

# QQ Plot
ggplot(data.frame(RandomData = RandomData), aes(sample = RandomData)) + stat_qq() + geom_abline(slope = s, intercept = xbar) + ggtitle(title)
```

### Histogram and Normal Probability Plots

### Summary

## Part D

### Code

### Histogram and Normal Probability Plots

### Summary

## Part E

### Code

### Histogram and Normal Probability Plots

### Summary
