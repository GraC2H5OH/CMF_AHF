# CMF_AHF
## Work on a project "Researching of Algorithmic hedge fund" in the Center of Mathematical Finances.

## Contents:
- [What will be done](#what-will-be-done)
- [Proposal](#proposal)
- Soon
- Soon
- Soon
- [Additional materials](#additional-materials)

### What will be done
- Existing strategies need to be explored first.
  - Choosing a article
  - Writing proposal(We are here)
  - Collecting the data used in article
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

#### Sources
What data do we need:
- Spot price of West Texas Intermediate crude oil from EIA
- Consumer price index from FRED
- Macroeconomic variables from EIA and FRED
- The U.S. refiner’s acquisition cost for crude oil imports (RAC) from EIA
- Macro database called FRED-MD

#### Bonus
If we have time: use the extracted features from the lasso and build neural network (for example, LSTM) and compare results.


#### The article we will use
[Forecasting crude oil prices with a large set of predictors: Can LASSO select powerful predictors?](https://sci-hub.ru/10.1016/j.jempfin.2019.08.007)
#### Additional materials
[The Elements of Statistical Learning Data Mining, Inference, and Prediction](https://hastie.su.domains/Papers/ESLII.pdf)
