Explanation for everything found in the supplied R environment.
Using one of the function might create new values, these are not explained here.
---------------------------------------------------------------------------------------------------------------------------------------------------------------
DATA

IC/ICend/ICsinglestart/ICstart: Information Criteria for VAR
data: Original data for gold and Bitcoin prices (however weekends and public holidays already excluded), further data for the Weekend Dummies
resid
---------------------------------------------------------------------------------------------------------------------------------------------------------------
VALUES

ChowValues: Chow statistic values used for the estimation of the break point
D[...]:Time series of the dummy variables for the weekend spikes (same data as in "data")
StrucBreakDummy: Dummy for the break point found with the Chow values
dltsbitcoin: diff(log(data$Bitcoin))
dltsbitcoinend: data after the breakpoint for dltsbitcoin
dltsbitcoinstart: data before the break point for dltsbitcoin
dltsgold: diff(log(data$Gold))
dltsgoldend: data after the breakpoint for dltsgold
dltsgoldstart: data before the break point for dltsgold
extract: Bitcoin series extract showing a weekend spikes
ltsbitcoin/trendltsbitcoin: logarithmized bitcoin prices --> detrended (for investigation of trend stationarity)
z=StrucBreakDummy*dltsbitcoin
---------------------------------------------------------------------------------------------------------------------------------------------------------------
FUNCTIONS

The prediction functions should be self-explanatory. They are used to make predictions for several data points and always reestimate the coefficients
The used variables are:
tseries: series to predict
n: how many datapoints to be predicted (the last n points)
stepahead: forecast horizon
ar, Iorder, ma: ARIMA orders
exo: exogenous data series needed for the forecast

laggedresid: a function to lag data series (move it back and forth), used in prediction functions
ChowTestStrucChange: tests for a structural change in the Distributed Lag model between data points z1 and z2
