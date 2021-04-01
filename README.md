# Master_thesis
R code for Causalities


This file contains R code for my master thesis Detection of causality in time seriesusing extreme values. It contains mainly two functions. 

Function CTC(x, lag=3, v=0.4, both_ways=FALSE, derivative=FALSE) computes causal tail coefficient for time series with the given lag. 
Number $v$ represents a function k=n^v, where n is number of data, and k is the number of extremal values from which we compute this statistic.
Parameters both_ways represents if we want to compute the both-way statistic, not only positive extremes. 
Parameter derivative represents, if we want to consider derivative of our time series, not original series. 

Function CTC_bootstrap(x, number_of_blocks=15, number_of_resampling=50, lag=5,  v=0.4) computes confidence intervals and p-value of causal tail coefficient with stationary bootstrap method. 
Number_of_blocks represents number of blocks used for bootstrap
Number_of_resampling represents a number how many times do we want to repeat the bootstrap. 
Lag and $v$ remains the same as in CTC. 

Data x needs to be 2*n dimensional data.frame imput





















