# Surfing the Bitcoin Waves: Comprehensive Trend Forecasting with Various Trader Types

[![Paper](https://img.shields.io/badge/Neural%20Computing%20and%20Applications-2025-1a5fb4)](https://doi.org/10.1007/s00521-025-11496-9)
[![DOI](https://img.shields.io/badge/DOI-10.1007%2Fs00521--025--11496--9-555)](https://doi.org/10.1007/s00521-025-11496-9)

Code and data for the paper

> Can Ali Ateş, Emre Çoban, Tugba Gurgen Erdogan.
> **Surfing the Bitcoin Waves: Comprehensive Trend Forecasting with Various Trader Types.**
> *Neural Computing and Applications* 37(26), 21931–21948, 2025.
> [doi:10.1007/s00521-025-11496-9](https://doi.org/10.1007/s00521-025-11496-9)

Hacettepe University, Department of Computer Engineering.

## Overview

Many traders try to follow the moves of successful investors, automated bots or "whale"
accounts. This work asks whether the behaviour of these trader groups carries information about
where the Bitcoin price is heading. We combine one year of Bitcoin price data with Binance
indicators of three groups (whales, top traders and bots) plus buy and sell volume, and compare
machine learning, classical time-series and deep learning forecasters on hourly and 15-minute data.

Research questions:

1. Which market indicators and trader behaviours influence Bitcoin price movements?
2. How well can machine learning and deep learning models forecast Bitcoin trends?
3. How can forecasts account for different trader types?

## Repository

```
SurfingBTC.ipynb   end-to-end notebook: data understanding, preparation, models, evaluation
data/              16 CSV files (8 indicators × hourly and 15-minute resolution)
Report.pdf         project report (earlier, pre-publication version of the paper)
requirements.txt   Python dependencies
```

## Data

All series cover **27 Apr 2023 – 21 Apr 2024** for BTC on Binance, at hourly (`*Hourly.csv`,
~8.6k rows) and 15-minute (`*15mins.csv`, ~34.5k rows) resolution.

| File prefix | Columns | Meaning |
|---|---|---|
| `klines` | `open, close, high, low` | Bitcoin price candles |
| `botTracker` | `estimatedBotCount` | Estimated bot activity from frequently repeated unique order sizes |
| `binanceGlobalAccounts` | `Long, Short, L/S` | Share of all Binance accounts holding long / short positions |
| `binanceTopTraderAccounts` | `Long, Short, L/S` | Same for top-trader accounts (top 20%) |
| `binanceTopTraderPositions` | `Long, Short, L/S` | Long / short split of top-trader positions (top 20%) |
| `binanceWhaleDelta` | `WhaleRetailPosition` | Long share of top traders ("whales") minus long share of global accounts ("retail") |
| `buyVolume` | `BuyingOrderQuantity` | Quantity of executed buy orders per period |
| `sellVolume` | `SellingOrderQuantity` | Quantity of executed sell orders per period |

## Models

| Family | Models |
|---|---|
| Machine learning | Linear Regression, Random Forest, XGBoost |
| Classical time series | SARIMAX (order selected with auto-ARIMA), Prophet |
| Deep learning | LSTM-FCN, FCN, Transformer encoder |

Models are trained on a chronological train / validation / test split of min-max scaled features
and evaluated with MSE, MAE and R².

## Getting started

```bash
git clone https://github.com/emrecobann/SurfingBTCWaves.git
cd SurfingBTCWaves
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook SurfingBTC.ipynb
```

The notebook reads the CSV files from `data/` and runs top to bottom. A GPU speeds up the
deep learning models but is not required.

## Citation

```bibtex
@article{ates2025surfing,
  title   = {Surfing the Bitcoin Waves: Comprehensive Trend Forecasting with Various Trader Types},
  author  = {Ate{\c{s}}, Can Ali and {\c{C}}oban, Emre and Gurgen Erdogan, Tugba},
  journal = {Neural Computing and Applications},
  volume  = {37},
  number  = {26},
  pages   = {21931--21948},
  year    = {2025},
  doi     = {10.1007/s00521-025-11496-9}
}
```

## Contact

Can Ali Ateş · canaliatess@gmail.com
Emre Çoban · emrecobann02@gmail.com
