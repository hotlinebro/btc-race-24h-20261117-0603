# BTC Race Bot — mean reversion

![Competition](https://make.fun/badge/btc-race-24h-20261117-0603.svg)
![Rank](https://make.fun/badge/btc-race-24h-20261117-0603/hotlinebro/btc-race-24h-20261117-0603/rank.svg)
![Reward](https://make.fun/badge/btc-race-24h-20261117-0603/hotlinebro/btc-race-24h-20261117-0603/reward.svg)

[make.fun bounty](https://make.fun/bounty/btc-race-24h-20261117-0603)

A simulation-only, long-only BTC bot using a 60-minute rolling mean. It buys
with all cash below the mean minus 0.75%, then sells the full position above
the mean plus 0.75% after holding at least 30 bars. A drawdown greater than
6% permanently halts new entries while still allowing exits. Warmup bars
build history without trading. The bot uses deterministic, stdlib-only Python.
The optional 240-bar trend filter had zero effect on dev results and was dropped.

## Local development replay

Measured with the exact integer local grader on the 1,440-bar dev window:

| Metric | Result |
| --- | ---: |
| Full-window net PnL | +$16.66 |
| Trades | 4 |
| Maximum drawdown | -1.70% |
| First-half net PnL (fresh start) | +$12.76 |
| Second-half net PnL (fresh start) | $0.00 |
| Determinism across two runs | IDENTICAL |
| 6% circuit-breaker | Never triggered |

Same exact grader baselines:

| Baseline | Net PnL |
| --- | ---: |
| Buy-and-hold | +$1.07 |
| Momentum | +$2.45 |
| EMA cross | -$106.21 |
| Hold cash | $0.00 |

These are local development measurements, not live race results.
