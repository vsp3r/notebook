---
Strategy outputs target position:==x==
Compare it to current position:==y== at all times
Introduce **buffer parameter**:==b==

###### Rules:
if y < x - b "If current pos less than target - buffer, then trade until current = target - buffer"
If y > x + b, "If current pos greater than target + buffer, then trade until current = x + b"

This introduces a ==no trade region== where you shouldn't be trading. ie, **don't trade in an interval width of 2b around your target position**

To pick b:
1. Optimize in a backtest (eg to maximize net sharpe ratio)
2. Pick one to target a particular turnover, eg. if your forecast hoizon is 10 days, and you hope to turn over ~20% fo your book per day, pick a b to achieve this.
3. Or pick a sensibel value based on max pos size, eg. 5-25% of max pos size

###### Danger:
Main danger is if your edge is overestimated, so your optimization will pick a b value that is too low, so you should be conservative and double the "best" value of b.
