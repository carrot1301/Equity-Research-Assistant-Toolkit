# Equity Research Assistant Toolkit

### A Research-Oriented Toolkit for Stock Analysis (Vietnam & Global Markets)

This project is a **research-oriented toolkit** designed to support:

* Equity Research
* Stock & Market Analysis
* Financial Analysis
* Writing equity research / financial reports

> This is **NOT** a trading bot and **NOT** an automated investment system.

---

## Project Objectives

Provide a **clean, reproducible, and research-friendly workflow** to:

* Collect stock and market price data
* Analyze stock performance vs market benchmark
* Compute key risk and performance metrics
* Summarize indicators commonly used in equity research reports

---

## Supported Markets & Data Sources

| Market                        | Source           | Purpose                        |
| ----------------------------- | ---------------- | ------------------------------ |
| 🇻🇳 Vietnam stocks & VNIndex | `vnstock3` (OOP) | Local market data for research |
| Global stocks & S&P 500    | `yfinance`       | International market benchmark |

---

## Who is this for?

* Equity Research Interns
* Finance / Data Science students
* Junior analysts

---

## Installation

### Option 1: Google Colab

```python
!pip install -U vnstock yfinance
```

### Option 2: Local Python Environment

```bash
pip install -U vnstock yfinance
```

---

## Workflow Overview

1. User inputs a stock ticker:

   * Vietnam: `FPT`, `VNM`, `HPG`, `VCB`, ...
   * Global: `AAPL`, `MSFT`, `NVDA`, ...

2. The system automatically:

   * Detects market type
   * Selects the appropriate data source
   * Downloads:

     * Stock price data
     * Market index price data

3. The system computes:

   * Returns
   * Volatility
   * Beta
   * Maximum drawdown

4. The system generates:

   * Key indicators for equity research reports

5. (Optional – Vietnam stocks only):

   * Loads financial statements and ratios via `vnstock3`

---

## Example Research Use Cases

### Example 1: Vietnam Stock (FPT)

```python
ticker = "FPT"
```

The system will:

* Use `vnstock3`
* Load:

  * FPT price history
  * VNIndex price history
* Produce:

  * Cumulative performance chart
  * Risk metrics
  * Summary indicators for research reports
  * Financial ratios (if requested)

Typical outputs:

* Current price
* 52-week high / low
* Volatility
* Beta vs VNIndex
* Maximum drawdown
* Total return

---

### Example 2: Global Stock (AAPL)

```python
ticker = "AAPL"
```

The system will:

* Use `yfinance`
* Load:

  * AAPL price data
  * S&P 500 index (`^GSPC`)
* Compute the same research metrics

---

## Key Metrics Generated (For Research Reports)

* Current Price
* 52-Week High / Low
* Average Daily Return
* Annualized Volatility
* Beta (vs market index)
* Maximum Drawdown
* Total Return over sample period

These metrics are commonly used in:

* Company initiation reports
* Periodic update reports
* Risk analysis sections
* Market comparison sections

---

## Financial Statement Data (Vietnam Only)

For Vietnam stocks, the project can also load:

```python
stock.finance.balance_sheet()
stock.finance.income_statement()
stock.finance.cash_flow()
stock.finance.ratio()
```

Example:

```python
ratios = stock.finance.ratio()
ratios.head()
```

These are useful for:

* Fundamental analysis
* Valuation modeling
* Writing company overview and business analysis sections

---

## Core Architecture (Simplified)

```python
from vnstock import Vnstock

vnstock = Vnstock()
stock = vnstock.stock(symbol="FPT", source="VCI")
vnindex = vnstock.stock(symbol="VNINDEX", source="VCI")

price_stock = stock.quote.history(start="2018-01-01")
price_index = vnindex.quote.history(start="2018-01-01")
```

---

## Design Philosophy

This project is **research-first, not trading-first**.

Focus on:

* Data quality
* Reproducibility
* Clarity and interpretability of results

> Final investment decisions must always be made by humans, not by this tool.

---

## Disclaimer

This project is for:

* Educational purposes
* Research purposes
* Analytical support only

It is **NOT investment advice**.

Author: Doan Nguyen Tri
Email: Doantri12343@gmail.com
