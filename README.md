# Master_thesis
R code for Causalities


This file contains R code for my master thesis Detection of causality in time series using extreme values. It contains mainly two functions, CTC and CTC_bootstrap. 

Function CTC(x, lag=3, v=0.5, both_ways=FALSE, derivative=FALSE) computes causal tail coefficient for time series with the given lag. 
Number $v$ represents a function k=n^v, where n is number of data, and k is the number of extremal values from which we compute this statistic.
Parameters both_ways represents if we want to compute the both-way statistic, not only positive extremes. 
Parameter derivative represents, if we want to consider derivative of our time series, not original series. 

Function CTC_bootstrap(x, number_of_blocks=15, number_of_resampling=50, lag=5,  v=0.5) computes confidence intervals and p-value of causal tail coefficient with stationary bootstrap method. 
Number_of_blocks represents number of blocks used for bootstrap
Number_of_resampling represents a number how many times do we want to repeat the bootstrap. 
Lag and $v$ remains the same as in CTC. 

Data x needs to be 2*n dimensional data.frame imput


Example:
library(EnvStats)

n=1000
epsilon_a=rpareto(n, 1,1)
epsilon_b=rpareto(n, 1,1)

b=rep(0, n);a=rep(0, n);

for (i in 10:n) {
  a[i]=0.5*a[i-1] +epsilon_a[i]
  b[i]=0.5*b[i-1]  +0.5*a[i-5]+epsilon_b[i]
}
x=data.frame(a,b)


plot(x[,1], type="l", col="blue", xlab="", ylab="")
par(new=TRUE)
plot(x[,2], type="l",col="red", xlab="", ylab="", yaxt = "n");axis(4)
legend("topright", c("Cause", "Efect"), col = c("blue","red"), lty = 1)



CTC(x, lag=5)

CTC_bootstrap(x, lag=5) #this can take a minute



















