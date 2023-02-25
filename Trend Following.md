---
via @Macrocephalopod on Twitter 
https://twitter.com/macrocephalopod/status/1587591552691765251?s=20

### Considerations
1. Universe Selection
	1. Diversified and uncorrelated markets (adding breadth scales roughly sqrt(breadth)) -> ie. trending S&P and Nas, then add NatGas futures
	2. Typically trade through 60-80 futures markets, wehreas bigger fund may use 300-400
	3. Larger funds also use FX forwards, NDFs, interest rate swaps, CDS indicies
2. Trend Detection (Signal)
	1. Most common is MA crossovers -> fast moving average of log(price) minuse a slow moving average, likely **normalized by volaility**.
		1. Generally simple and hard to overfit. Low pass filters on noise
	2. **Horizons**: 1 month to 1 year, ==average around 3-6 months==. Possible to capitalize on **intraday** trends as well, but need to be across multiple markets
3. Mapping from trend strength to desired position
	1. Need to turn trend signal strength into ==target risk allocation==
	2. 2 common approahces are sigmoid function or x \* exp(-x^2)
	3. These both are meant to ensure that you cap out capital allocation or unwind as trend overextends
	4. 
4. Sector / Asset class weights
	1. You can also add a bias to markets which tend to go up on average (equities, credit, fixed income)
	2. **Need to consider**: ratio between current exposure and desired weighting
	3. Can do simple equal weighting, complex pca-based methods.
	4. Bucketing into broad asset class groups and trying to have roughly equal vol in each asset class is also good.
5. Portfolio risk targeting [[Portfolio Management]]
	1. ==Position Sizing==
		1. Most common way - make them inversely proportional to a market-specific volatility forecast
	2. [[Volatility Forecasting]] - best way is blend of steady-state long term vol (estimated over 10 years) and a short-term realized vol (30-60 days)
	3. ==Can size up positions when there are few trends, and size down when there are many== -> helps you stay close to target risk level, which increases sharpe ratio
6. Trading Rules
	1. Don't want to trade on every change in signal or vol forecast, bc would churn volume and cost lots of commission and slippage -> can use [[Buffering]] https://twitter.com/macrocephalopod/status/1373216917058682881?s=61&t=FliRN69qyM3HlTDarFGI4w
	2. Can also use an [[Optimization]], but this can introduce some difficulties if you do it incorrectly, so heuristics might be better
7. Execution

[[Momentum Signals]]