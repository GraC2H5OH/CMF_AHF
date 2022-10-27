# CMF_AHF
## Work on a project "Researching of Algorithmic hedge fund" in the Center of Mathematical Finances.

## Contents:
- [What will be done](#what-will-be-done)
- [Proposal](#proposal)
- [Data](sources)
- Soon
- Soon
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

#### Bonus
If we have time: use the extracted features from the lasso and build neural network (for example, LSTM) and compare results.


#### The article we will use
[Forecasting crude oil prices with a large set of predictors: Can LASSO select powerful predictors?](https://sci-hub.ru/10.1016/j.jempfin.2019.08.007)
#### Additional materials
[The Elements of Statistical Learning Data Mining, Inference, and Prediction](https://hastie.su.domains/Papers/ESLII.pdf)
