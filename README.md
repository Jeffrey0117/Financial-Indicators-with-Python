# Python Financial Strategy Development

The focus is on **practical, hands-on development** of data acquisition, indicator construction, backtesting, and automation tools — all in Python.

## Learning Scope

### 1. Development Basics

* Virtual environment setup and management
* Using `requirements.txt`
* Integration with VS Code
* Accessing and managing example code from GitHub

### 2. Data Acquisition

* Web scraping concepts and anti-bot techniques
* Scraping Taiwan stock lists with `requests` + `pandas`
* Retrieving market quotes via HTML parsing (`BeautifulSoup`)
* Gathering financial news headlines, dates, and content
* Accessing TWSE institutional investor daily reports through APIs and JSON

### 3. Market Helpers & Stock Screening

* Historical data retrieval with `yfinance`
* Creating technical indicators with `ta` and `pandas`
* Basic charting: candlestick, Bollinger Bands, volume plots
* Email notifications with attachments
* Securely managing credentials (encryption/decryption)
* Trading day checks (holiday handling)
* Example helper scripts:

  * Follow institutional investors
  * High dividend yield + low price screening
  * Sharp price drop + news correlation
* Automation with Windows Task Scheduler

### 4. Indicator-Based Strategy Writing & Evaluation

* Strategy analysis with `pyfolio`
* Backtesting with `backtrader`
* Example strategies:

  * 5MA cross 60MA entry/exit
  * Breakout entry with scaling and stop-loss/take-profit
  * MACD + MA multi-condition entry

### 5. AI, Big Data, and Finance

* Applying AI and NLP for market analysis
* Case study: financial news relation extraction
* End-to-end workflow: data, feature selection, modeling, prediction, deployment

## Structure

```
.
├── data/              # Sample datasets
├── notebooks/         # Step-by-step exercises in Jupyter
├── src/               # Scripts organized by topic
│   ├── scraping/
│   ├── indicators/
│   ├── strategies/
│   └── utils/
└── README.md
```

## Environment Setup

```bash
python -m venv venv
source venv/bin/activate   # or venv\Scripts\activate on Windows
pip install -r requirements.txt
```

## Notes

* This repository is for **educational purposes** only.
* Code examples are simplified for learning clarity; adapt them for production use.
* Always comply with data source terms of service when scraping or automating requests.
