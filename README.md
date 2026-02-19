# Algorithmic Trading Strategies

[![Python](https://img.shields.io/badge/Python-3.13+-3776AB?logo=python&logoColor=white)](https://python.org)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.54+-FF4B4B?logo=streamlit&logoColor=white)](https://streamlit.io)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?logo=docker&logoColor=white)](https://hub.docker.com/r/tertiaryinfotech/automated-quant-trader)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

An automated quantitative trading simulator with 7 built-in algorithmic strategies, real-time backtesting, and optional AI-powered analysis via Gemini 2.0 Flash.

![Automated Quant Trader Dashboard](algorithmic-trading.png)

## Features

- **7 Trading Algorithms** — SMA Crossover, EMA Crossover, SMA Long Only, RSI, Bollinger Bands, MACD, and Stochastic Oscillator
- **Backtesting Engine** — Vectorized backtesting with configurable initial capital, trade quantities, and simulation date ranges
- **Performance Metrics** — Sharpe Ratio, Max Drawdown, Annualized Return, Volatility, and strategy vs. Buy & Hold comparison
- **Interactive Charts** — Plotly-powered visualizations with buy/sell signal markers and equity curve overlays
- **AI Insights (Optional)** — Gemini 2.0 Flash generates technical analysis reports on strategy performance and optimization tips
- **Trade Log** — Detailed execution log of all automated buy/sell actions

## Architecture

```
algorithmics-trading-strategies/
├── app.py                 # Streamlit dashboard (main entry point)
├── main.py                # CLI runner for quick backtests
├── config.yaml            # Default strategy configuration
├── src/
│   ├── data.py            # Market data fetching via yfinance
│   ├── strategy.py        # Signal generation for all 7 algorithms
│   ├── backtest.py        # Vectorized backtesting engine
│   ├── metrics.py         # Performance metric calculations
│   └── utils.py           # Plotly + matplotlib visualization
├── Dockerfile             # Container deployment
└── pyproject.toml         # Dependencies (managed with uv)
```

## Getting Started

### Prerequisites

- Python 3.13+
- [uv](https://docs.astral.sh/uv/) (recommended) or pip

### Installation

```bash
git clone https://github.com/alfredang/algorithmics-trading-strategies.git
cd algorithmics-trading-strategies
uv sync
```

### Run the Dashboard

```bash
uv run streamlit run app.py
```

Then open http://localhost:8501 in your browser.

### Run via CLI

```bash
uv run python main.py
```

Uses the parameters defined in `config.yaml`.

### Docker

Pull the pre-built image:

```bash
docker pull tertiaryinfotech/automated-quant-trader:latest
docker run -p 8501:8501 tertiaryinfotech/automated-quant-trader:latest
```

Or build locally:

```bash
docker build -t automated-quant-trader .
docker run -p 8501:8501 --env-file .env automated-quant-trader
```

## AI Insights (Optional)

To enable Gemini 2.0 AI-powered strategy analysis, create a `.env` file:

```ini
GEMINI_API_KEY=your_gemini_api_key_here
```

The app runs fully without it — AI insights are an optional enhancement.

## Tech Stack

| Component | Technology |
|---|---|
| Dashboard | [Streamlit](https://streamlit.io/) |
| Market Data | [yfinance](https://github.com/ranaroussi/yfinance) |
| Computation | [Pandas](https://pandas.pydata.org/), [NumPy](https://numpy.org/) |
| Visualization | [Plotly](https://plotly.com/), [Matplotlib](https://matplotlib.org/) |
| AI Analysis | [Google Gemini 2.0](https://ai.google.dev/) |
| Package Manager | [uv](https://docs.astral.sh/uv/) |

## License

MIT
