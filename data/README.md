# Data

The analysis uses two historical cryptocurrency price files. Raw data are **not committed to this repository**.

## Required files

Place the following files in this directory before rendering the Quarto analysis:

```text
data/
├── ETH_1H.csv
└── coinbaseUSD_1-min_data.csv
```

### Ethereum

- File: `ETH_1H.csv`
- Frequency: hourly
- Source: [Gendo90/Crypto-Historical-Prices — Ethereum](https://github.com/Gendo90/Crypto-Historical-Prices/blob/master/Ethereum/ETH_1H.csv)

### Bitcoin

- File: `coinbaseUSD_1-min_data.csv`
- Frequency: one minute
- Source: [BTC and ETH 1-min Price History on Kaggle](https://www.kaggle.com/datasets/patrickgendotti/btc-and-eth-1min-price-history)

The Bitcoin file is several hundred megabytes, so excluding it from Git history keeps the repository lightweight and avoids GitHub's normal file-size limit.

## Data-quality treatment

Ethereum is already hourly. Returns crossing nonconsecutive hourly observations are excluded.

Bitcoin is aggregated from minute data using the final available price within each hour. Hours whose final observation occurs before minute 50 are excluded. Returns are then retained only when adjacent hourly timestamps are exactly one hour apart.
