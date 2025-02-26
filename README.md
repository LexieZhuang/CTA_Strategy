# CTA Strategy for Natural Gas Futures: Leveraging Carry and Momentum Factors

## Project Overview
This project develops a **CTA strategy for Natural Gas Futures using carry and momentum factors**. The approach constructs carry signals from futures price differences, computes technical indicators for momentum analysis, and dynamically combines signals based on historical performance. The strategy undergoes full-sample and recent-period backtesting to assess robustness. We also developed a **flexible backtesting framework for in-depth analysis**. his project is the final project for course FRE-7841 Hedge Fund Strategies, Prof. James Conklin, NYU. Shout out to Prof. James Conklin for his support and help. 

## Methodology
### Carry Signal Construction
- Measures cost of holding inventories based on storage costs and convenience yields.
- Methods:
  - Price Difference (NG1-NG2)
  - Rate Difference (Normalized by Interval)
- Transformation:
  - Moving averages for noise reduction
  - Quantile scaling over historical windows
  - Mapping to (-1,1) using a linear function


### Technical Signal Construction
- Trend Indicators: SMA, SMA Crossover, DEMA, MACD
- Momentum Indicators: Rate of Change (ROC), Relative Strength Index (RSI)
- Channel Indicators: Keltner Channel, Bollinger Bands

### Signal Combination Strategy
- Uses Carry (NG1-NG2) and SMA Crossover signals
- Softmax weighting function based on 6-month historical returns
- Weights adjusted every 22 days

## Backtesting & Results
### Full-Sample Backtesting (2006-2024)
- Holding for 1, 5, or 10 days
- Stable returns, low volatility, minimal drawdowns
- Low turnover for cost efficiency

### Recent-Period Backtesting (2019-2024)
- Outperformed benchmark in 59% of months
- Consistent positive returns in different market conditions
- Post-2020 Sharpe Ratio: 1.1
- Low transaction cost impact (0.16% per trade)


### Code Structure
| Script | Function |
|--------|----------|
| `TechnicalSignal.ipynb` | Generate technical indicators |
| `CarrySignal.ipynb` | Construct carry signals |
| `SelectCombine.ipynb` | Combine signals dynamically |
| `Strategy_Backtesting.ipynb` | Backtesting framework |

## Conclusion
### Key Findings
- Carry Signal worked best before 2022 in stable market conditions.
- SMA Crossover outperformed in volatile markets post-2022.
- Dynamic weighting provides consistent profitability.

## References
Bouchouev, I. (2023). *Virtual Barrels: Systematic Risk Premia Strategies* (Chapter 5). Springer Texts in Business and Economics.

