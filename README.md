# CMF_AHF
## Work on a project "Researching of Algorithmic hedge fund" in the Center of Mathematical Finances.

## Contents:
- [What will be done](#what-will-be-done)
- [Proposal](#proposal)
- [Data](#sources)
- [Article Pipeline](#article-pipeline)
- [Model results](#model-results)
- [Additional materials](#additional-materials)

### What will be done
- Existing strategies need to be explored first.
  - Choosing a article
  - Writing proposal
  - Collecting the data used in article(We are here)
- Analyze historical data using statistical methods. 
- Try to make some hypotheses about price patterns, market inefficiencies, etc. 
- Defining of trading rules. 
- Historical data backtesting. 
- Real-time testing with broker. 
- Production and impovement of running strategies.

### Proposal
#### Current situation
The task of predicting crude oil prices has been and will continue to be relevant. In this project, we will try to show that Lasso and ElasticNet cope well with this task and even outperform some algorithms in many ways, especially in success ratio.

#### Suggestions
- Collect the data
- Compare models with each other
- Find out why Lasso and ElasticNet outperform their competitors
- See what features Lasso and ElasticNet rely on in their predictions
- Try several windows of data (last 50%, 40%,30%, etc) for evaluating optimal Lasso and ElasticNet coefficients.

### Sources
What data do we need:
- [Spot price of West Texas Intermediate crude oil from EIA](https://www.eia.gov/dnav/pet/hist/LeafHandler.ashx?n=PET&s=RWTC&f=M)
- [Consumer price index from FRED](https://fred.stlouisfed.org/series/CPIAUCSL)
- Macroeconomic variables from EIA and FRED
  - [Treasury bill rate: interest rate on a three-month Treasury bill (secondary market).](https://fred.stlouisfed.org/series/DTB3)
  - [Long-term yield: long-term government bond yield.](https://fred.stlouisfed.org/series/IRLTLT01USM156N)
  - [Inflation: calculated from the U.S. CPI for all urban consumers](https://fred.stlouisfed.org/series/CPIAUCSL).
  - [Stock return variance: sum of squared daily returns on the S&P 500 index.](https://towardsdatascience.com/calculate-and-plot-s-p-500-daily-returns-2ce359e014d6)
  - [Economic policy uncertainty: calculated from the monthly economic policy uncertainty index for the U.S.](https://www.policyuncertainty.com/)
  - [Kilian’s index: the real global economic activity index from Kilian (2009).](https://www.dallasfed.org/research/igrea)
  - [Growth of crude oil production: calculated as the first difference of the log production of crude oil.](https://www.eia.gov/dnav/pet/hist/LeafHandler.ashx?n=PET&s=WCRFPUS2&f=W)
  - [Growth of crude oil stock: calculated as the first difference of the log U.S. ending stocks of crude oil.](https://www.eia.gov/dnav/pet/hist/LeafHandler.ashx?n=PET&s=WCRSTUS1&f=W)
  - [Growth of crude oil import: calculated as the first difference of the log U.S. imports of crude oil.](https://www.eia.gov/dnav/pet/pet_move_wkly_dc_NUS-Z00_mbblpd_w.htm)
  - [Money supply: calculated as the first difference of the log U.S. M2 money stock.](https://fred.stlouisfed.org/series/M2SL)
  - Industrial production index: calculated as the first difference of the log industrial production index for crude oil.
  - [Unemployment rate: calculated as the first difference of the U.S. civilian unemployment rate.](https://fred.stlouisfed.org/series/UNRATE)
  - [The Chicago Fed’s national activity index.](https://www.chicagofed.org/research/data/cfnai/current-data#:~:text=The%20Chicago%20Fed%20National%20Activity,end%20of%20each%20calendar%20month.)
  - [Capacity utilization: the capacity utilization for manufacturing.](https://fred.stlouisfed.org/series/MCUMFN)

- [The U.S. refiner’s acquisition cost for crude oil imports (RAC) from EIA](https://www.eia.gov/dnav/pet/pet_pri_rac2_dcu_nus_m.htm)
- [Macro database called FRED-MD](https://research.stlouisfed.org/econ/mccracken/fred-databases/)

### Article Pipeline
#### How we fit and evaluate the models?
1) Fit on a train dataset
2) Evaluate on a out-of-sample dataset

Why we want to use out-of-sample dataset? Because out-of-sample test avoids the in-sample over-fitting issue and is more relevant for assessing
genuine return predictability in real time. To avoid the look-ahead bias, we should only use the information available up to 𝑡 to
generate the out-of-sample forecast at 𝑡+1
#### What metrics we will use?
1) <strong>R<sup>2</sup><sub>OS</sub></strong> = <strong>1 - <sup>MSPE<sub>M</sub></sup>&frasl;<sub>MSPE<sub>B</sub></sub></strong>

Where <strong>MSPE<sub>M</sub> = <sup>1</sup>&frasl;<sub>q</sub>*Σ<sup>q</sup><sub>i=1</sub>(r<sub>m+i</sub>-&#345;<sub>m+i</sub>)<sup>2</sup></strong> denotes the mean squared prediction error (MSPE) of the forecasting model of interest

And <strong>MSPE<sub>B</sub> = <sup>1</sup>&frasl;<sub>q</sub>*Σ<sup>q</sup><sub>i=1</sub>(r<sub>m+i</sub>-&#345;<sub>B,m+i</sub>)<sup>2</sup></strong> denotes the MSPE of the benchmark model(Historical average)

<strong>r<sub>m+i</sub>, ̂&#345;<sub>m+i</sub>, and ̂&#345;<sub>B,m+i</sub></strong> are the actual oil return, the oil
return predicted by the forecasting models, and the benchmark forecast, respectively, at month m+i, and m and q
are the length of the in-sample estimation period and the out-of-sample evaluation period, respectively.

This is R<sup>2</sup> statistic but for out-of-sample dataset

2) Success ratio

#### Pipeline
We always fit our models on data from January 2 1997 to February 28 2020.
out-of-sample dataset starting from March 3 2020 and to the end(March 31, 2021), in one point validation will begin earlier
We always study on the entire dataset(macro features and technical features) unless otherwise written

1) Fitting and validation, nothing different from the default parameters
2) Fitting with feature selection, ElasticNet selects features for ElasticNet, Lasso selects features for Lasso, we look at non-zero coefficients (we first fit and look at coefficients, and then we fit using features with non-zero coefficients)
3) Fitting when two sets of features(macro and technical) are used separately
4) Fitting with economic constraints. An economic constraint that a rational investor will rule out a negative stock return forecast and therefore set the forecast to zero whenever it is negative
5) Fit and check metrics on out-of-sample high- and low-sentiment periods
6) Fit using five different window sizes (30%, 35%, 40%, 45%, and 50% of estimation sample) to estimate LASSO parameters  
7) FIt ElasticNet and Lasso with a fixed number of selected predictors. Аnd we also use a different value of the alpha parameter(0.3, 0.5, 0.7) for ElasticNet
8) TBA
9) Out-of-sample dataset now starts from 2007(To be fixed)
10) In this subsection, we will further consider another prevailing indicator of crude oil prices, namely, the cost of the purchase of crude oil imports by an American oil refining company (hereinafter referred to as RAC). Out-of-sample dataset now starts again from March 3 2020
11) Forecasting nominal prices of crude oil and RAC
12) Fitting using FRED

### Model results

| Pipeline points  | R<sub>2</sub>| MSE    |
|------------------|--------------|--------|
|1.Lasso           |-18.76        |3463    |
|1.ElasticNet      |-16.85        |3128    |
|2.Lasso           |-18.68        |3449    |
|2.ElasticNet      |-16.86        |3131    |
|3.Lasso Macro     |-18.76        |3463    |
|3.ElasticNet Macro|-16.82        |3123    |
|3.Lasso tech      |-0.86         |327     |
|3.ElasticNet tech |-0.86         |326     |



#### Bonus
If we have time: use the extracted features from the lasso and build neural network (for example, LSTM) and compare results.


#### The article we will use
[Forecasting crude oil prices with a large set of predictors: Can LASSO select powerful predictors?](https://sci-hub.ru/10.1016/j.jempfin.2019.08.007)
#### Additional materials
[The Elements of Statistical Learning Data Mining, Inference, and Prediction](https://hastie.su.domains/Papers/ESLII.pdf)


