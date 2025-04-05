# Financial-Intelligence ND4
[English below]

## 4. Portfelio kūrimas iš kelių instrumentų
Šiame aplankale pateikiama Python programinis kodas `Finansinis_intelektas_ND4_E_Vaitkeviciute.ipynb` bei duomenys. Sukuriamas portfelis iš įvairių šaltinių ir pademonstruojamas supratimas apie faktorius, darančius įtaką portfelio kokybei.

Funkcija, skirta duomenų (keli skirtingi finansiniai instrumentai - 10 skirtingų akcijų) įkėlimui:
```python
def download_stock_data(symbol, start_date="2010-01-01", end_date="2020-01-01"):
    data = yf.download(symbol, start=start_date, end=end_date)
    return data

data_AAPL = download_stock_data("AAPL")
data_AMZN = download_stock_data("AMZN")
data_BP = download_stock_data("BP")
data_GLD = download_stock_data("GLD")
data_GOOGL = download_stock_data("GOOGL")
data_MSFT = download_stock_data("MSFT")
data_NDAQ = download_stock_data("NDAQ")
data_SPOT = download_stock_data("SPOT")
data_TSLA = download_stock_data("TSLA")
data_BKNG = download_stock_data("BKNG")
```

Sukuriama prieškryptinė Bollinger Bands strategija. Ji realizuojama, naudojant:

```python
def calculate_bollinger_bands(df, window, std_dev, transaction_costs)
```

Prekybos sandoriams nustatyti, naudojama funkcija determine_trades:

```python
def determine_trades(df, stop_loss)
```

Strategija Bollinger Bands panaudojama su keliais skirtingais finansiniais instrumentais (su 10 skirtingų akcijų):

```python
data_list = [data_AAPL, data_AMZN, data_BP, data_GLD, data_GOOGL, data_MSFT, data_NDAQ, data_SPOT, data_TSLA, data_BKNG]
dfs = []
stop_loss = 0.02

for ticker in data_list:
    df = ticker[['Close']].copy()
    df = calculate_bollinger_bands(df, window, num_std_dev, transaction_costs)
    df = determine_trades(df, stop_loss)
    dfs.append(df)
```
<img src="https://github.com/evelinavait/Financial-Intelligence/blob/35496c9675b0c5caa738aada73524e9ae6f6538a/ND4/images/stocks_bollinger_bands_strategy.png" width="1200"/>

### Optimizavimas
Strategijai optimizuoti taikoma `optimize_strategy` funkcija. Surandamas geriausias parametrų rinkinys kiekvienam instrumentui.

```python
def optimize_strategy(data, window_range, std_dev_range, transaction_costs_range, stop_loss)
```

Toliau, lyginamos ir grafiškai vizualizuojamos optimizuotos ir neoptimizuotos strategijos:

```python
def plot_strategy_comparison(data_list, tickers, all_optimal_params, all_sharpe_ratios, all_cumulative_profits)
```
<img src="https://github.com/evelinavait/Financial-Intelligence/blob/35496c9675b0c5caa738aada73524e9ae6f6538a/ND4/images/stocks_optimized_nonoptimized_profits.png" width="1200"/>

### Portfelis, sujungtas pelnas
Strategijų rezultatai sudedami į portfelį ir parodomas sujungta pelno (ne viso turto) kreivė viename grafike:

```python
def combine_position_values(*args, tickers):
    position_values = pd.concat([df['Position value'] for df in args], axis=1)
    position_values.columns = tickers
    return position_values
```
<img src="https://github.com/evelinavait/Financial-Intelligence/blob/35496c9675b0c5caa738aada73524e9ae6f6538a/ND4/images/total_portfolio_value.png" width="600"  height="350"/>

### Koreliacijų matricos
Pagal turimų akcijų kainų pokyčius suskaičiuojamos koreliacijos:

```python
def calculate_returns(tickers, data)
returns.corr()
```

Vaizduojama koreliacijos matrica tarp skirtingų strategijų prekybos rezultatų/komponentų (funkcija `plot_heatmap`):

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/35496c9675b0c5caa738aada73524e9ae6f6538a/ND4/images/correlation_matrix_returns.png" width="500"/>

Koreliacijų matrica pagal dienines strategijų grąžas:

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/35496c9675b0c5caa738aada73524e9ae6f6538a/ND4/images/correlation_matrix_daily_returns.png" width="500"/>

-------------
## 4. Creating a multi-instrument portfolio
This folder contains Python code `Finansinis_intelektas_ND4_E_Vaitkeviciute.ipynb` and data. A portfolio is created from various sources and an understanding of the factors that influence the quality of the portfolio is demonstrated.

A function for uploading data (several different financial instruments - 10 different shares):

```python
def download_stock_data(symbol, start_date="2010-01-01", end_date="2020-01-01"):
    data = yf.download(symbol, start=start_date, end=end_date)
    return data

data_AAPL = download_stock_data("AAPL")
data_AMZN = download_stock_data("AMZN")
data_BP = download_stock_data("BP")
data_GLD = download_stock_data("GLD")
data_GOOGL = download_stock_data("GOOGL")
data_MSFT = download_stock_data("MSFT")
data_NDAQ = download_stock_data("NDAQ")
data_SPOT = download_stock_data("SPOT")
data_TSLA = download_stock_data("TSLA")
data_BKNG = download_stock_data("BKNG")
```

A mean reversion Bollinger Bands strategy is created. It is implemented using:

```python
def calculate_bollinger_bands(df, window, std_dev, transaction_costs)
```

To determine the trades, the function `determine_trades` is used:

```python
def determine_trades(df, stop_loss)
```

The Bollinger Bands strategy is used with several different financial instruments (with 10 different stocks):

```python
data_list = [data_AAPL, data_AMZN, data_BP, data_GLD, data_GOOGL, data_MSFT, data_NDAQ, data_SPOT, data_TSLA, data_BKNG]
dfs = []
stop_loss = 0.02

for ticker in data_list:
    df = ticker[['Close']].copy()
    df = calculate_bollinger_bands(df, window, num_std_dev, transaction_costs)
    df = determine_trades(df, stop_loss)
    dfs.append(df)
```

### Optimisation
The `optimize_strategy` function is used to optimise the strategy. The best set of parameters for each instrument is found.

```python
def optimize_strategy(data, window_range, std_dev_range, transaction_costs_range, stop_loss)
```
Following this, the optimised and non-optimised strategies are compared and graphically visualised:

```python
def plot_strategy_comparison(data_list, tickers, all_optimal_params, all_sharpe_ratios, all_cumulative_profits)
```

### Total portfolio value
The results of the strategies are aggregated into a portfolio and the combined profit (not total assets) curve is shown on one graph:

```python
def combine_position_values(*args, tickers):
    position_values = pd.concat([df['Position value'] for df in args], axis=1)
    position_values.columns = tickers
    return position_values
```

### Correlation matrices
The correlations are calculated based on the changes in the prices of the available shares:

```python
def calculate_returns(tickers, data)
returns.corr()
```

The plots above and additional ones can be found in the [📁 images](https://github.com/evelinavait/Financial-Intelligence/tree/35496c9675b0c5caa738aada73524e9ae6f6538a/ND4/images) folder.
