# Other Examples: Markov Chain In Financial Market Risk
--- Part 3 ---

Other than the market directionality, like in the [previous examples](https://github.com/handiko/Markov-Chain-UpDown-Day/blob/main/README.md), in this article, I'd like to measure the market risk in terms of volatility using Markov chain analysis. Instead of an up or down day, we'll see a sequence of High or Low volatility days preceding a High or Low volatility day.

## Basic Understanding of Market Volatility
My definition of market volatility is as simple as: **"How large is the distance between the high of the day and the low of the day?"**. In other words, volatility is **the price range of the day**. (at least in my definition).
It could be measured in percent, pips, standard deviation, or any units that are suitable for each case.

My definition of today's volatility is **"the price distance between the high of the day and the low of the day, compared to the open price of the day, measured in percent"**.

$$
V = 100 \frac{{P_H - P_L}}{P_O}
$$

The understanding of market volatility is mostly used in terms of risk assessment. A high volatility day could make the running trade go haywire, as the wild price movement could trigger the stop loss and reverse back to the previous profitable price area (a price whipsaw). In this case, one can reduce the market exposure, move the stop loss into the profitable level (trailing stop), close the position, or use another trade management mechanism. For me personally, I'd like to trade in a low volatility environment as the price would likely move to either take profit or stop loss level smoothly.
Other trading strategies could be profitable on this highly volatile day instead. Therefore, volatility assessment could be used for a trading strategy filter or confirmation as well.

## High Order Markov Chain of Market Volatility
In this article, I use a sequence of **three preceding days** to analyze the next day's volatility probability. A high volatility day would be represented as an $H$, and a low volatility day would be represented as an $L$.
Therefore, the possible list of Markov chain transitions that could occur in this case is as follows:
* $LLL \to L$
* $LLL \to H$
* $LLH \to L$
* $LLH \to H$
* $LHL \to L$
* $LHL \to H$
* $LHH \to L$
* $LHH \to H$
* $HLL \to L$
* $HLL \to H$
* $HLH \to L$
* $HLH \to H$
* $HHL \to L$
* $HHL \to H$
* $HHH \to L$
* $HHH \to H$

16 possible cases could occur in the market.
As in the previous examples, we want to know the probability of each Markov chain transition as per the table below:
|                       | Next day is H | Nex day is L |
|-----------------------|---------------|--------------|
| Previuos days are LLL |               |              |
| Previuos days are LLH |               |              |
| Previuos days are LHL |               |              |
| Previous days are LHH |               |              |
| Previous days are HLL |               |              |
| Previous days are HLH |               |              |
| Previous days are HHL |               |              |
| Previous days are HHH |               |              |

## MQL5 Code to Analyze the Markov Chain Transition Probability
In the [MQL5 folder](https://github.com/handiko/Other-Examples-Markov-Chain-In-Financial-Market-Risk/tree/main/MQL5%20Code) included in this article, I provided a simple use code that shows the use case of Markov Chain analysis to assess market volatility risk, by extracting the transition probability.
Also, as an example, I would use the code in the BTC-USD market (Bitcoin) as an example in this article.

Code: [Relative Volatility Study - 3 Candle.mq5](https://github.com/handiko/Other-Examples-Markov-Chain-In-Financial-Market-Risk/blob/main/MQL5%20Code/Relative%20Volatility%20Study%20-%203%20Candle.mq5)
Market: BTC-USD, Daily Timeframe
