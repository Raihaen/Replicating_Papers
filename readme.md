
# Replicating Lit

This is a logbook for a small project where I try to replicate some methods mentionned in the literature.

Projects I plan to work on (in order of priority) :

- Optimal option market making and volatility arbitrage (Lucic and Tse 2024)
- Savine's differential ML
- Valuation & hedging of crypto inverse options (Lucic and Sepp 2024 - seemed fun).

# Optimal option market making and volatility arbitrage

## By Lucici and Tse

Our aim is to replicate a strategy that can encompass the trader's view on underlying volatility vs the market's implied volatility.

We will construct bid and ask levels depending on $\mathbb{E}(P_{\sigma_{arb})}$ and then, as a second part, take into account additional features (positional limits, multi options...)

The model presented is based on Avellaneda and Stoikov (2008)$^1$ where the arrival of option market orders is moddeled by a Cox process which intensity deprends on the MM's posted spreads, in this modeling approach, we will be using the market's $IV$ as an input.

## The baseline model

### Model assumptions

- Small MM time.
- Dividend & interest rates are assumed to be zero (acceptable since MM time is small).
- We assume $\sigma_{imp}$ to be constant throught the MM horizon.

### Model Definitions

- We define $Q_t = Y^b_t - Y^a_t$ as the MM's option inventory at time t. With &Y^a_t$ options sold and &Y^b_t$ options bought in the interval $(0,t)$.
- The MM's spread level is $\delta^b_t$ and $\delta^a_t$. So the bid and ask prices are $O_t - \delta^b_t$ and $O_t + \delta^a_t$ respectively. With $O_t$ being the call's price at time $t$.
- We model $Y^a_t$ and $Y^b_t$ as Cox processes, with state dependent intensites $\lambda^i_t(\delta^i_t)$

### Refferences

1- Avellaneda and Stoikov (2008)
