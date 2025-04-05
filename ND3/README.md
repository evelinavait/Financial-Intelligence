# Financial-Intelligence ND3
[English below]

## 3. Prekybinės strategijos parašymas Python aplinkoje
Šiame aplankale pateikiama Python programinis kodas bei duomenys. Įgyvendinama prieškryptinė strategija (mean reversion) - Bollinger Bands indikatorius, t. y. sukuriama prekybos sistema bei simuliacija, įtraukiant visus prekybos kaštus, taip pat atliekama optimizacija - randami geriausi parametrų rinkiniai.

Galutinis prieškryptinės strategijos variantas realizuojamas, naudojant:

```python
def calculate_bollinger_bands(df, window, std_dev, transaction_costs)
```

Prekybos sandoriams nustatyti, naudojama funkcija `determine_trades`:

```python
def determine_trades(df, stop_loss)
```

Vizualizavimui naudojama funkcija `plot_bollinger_bands`.

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/b31fcf136ffb3268d956c6d9a51f448472f947d8/ND3/images/bollinger_bands_strategy.png" width="800"/>

### Optimizavimas
Pilnas perrinkimas (brute force) - išbandoma visų parametrų visos kombinacijos ir ieškoma su kuriomis jis duoda geriausią rezultatą pagal numatytą kriterijų - kuo geresnis būtų sharpe santykis.

Sharpe santykis apskaičiuojamas:

```python
def calculate_sharpe_ratio(returns, N=252): # N - dienu skaicius per metus per kurias prekiaujama (pagal nutylejima)
    sharpe_ratio = np.sqrt(N) * (returns.mean() / returns.std())
    return sharpe_ratio
```

Brute force optimizavimas:

```python
for window in window_range:
    for std_dev in std_dev_range:
        for transaction_costs in transaction_costs_range:
            df = data_pd[['Close']].copy()
            rez = calculate_bollinger_bands(df, window, std_dev, transaction_costs)
            df = determine_trades(df, stop_loss)
            cumulative_profit = df['total_profit'].cumsum()
            returns = df['total_profit']
            sharpe_ratio = calculate_sharpe_ratio(returns)
            if sharpe_ratio > best_sharpe_ratio:
                best_sharpe_ratio = sharpe_ratio
                optimal_params = {'window': window, 'std_dev': std_dev, 'transaction_costs': transaction_costs}
                optimal_cumulative_profit = cumulative_profit
```

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/b31fcf136ffb3268d956c6d9a51f448472f947d8/ND3/images/optimized_nonoptimized_profits.png" width="800"/>

-------------
## 3. Writing a trading strategy in Python
This folder contains Python code and data. Implementing a mean reversion strategy - Bollinger Bands indicator, i.e. creating a trading system and simulation, including all trading costs, and optimising it by finding the best parameter sets.

The final version of the mean reversion strategy is implemented using:

```python
def calculate_bollinger_bands(df, window, std_dev, transaction_costs)
```

To determine the trades, the function `determine_trades` is used:

```python
def determine_trades(df, stop_loss)
```

The function `plot_bollinger_bands` is used for visualisation ([📁 images](https://github.com/evelinavait/Financial-Intelligence/blob/b31fcf136ffb3268d956c6d9a51f448472f947d8/ND3/images) `bollinger_bands_strategy.png`)

### Optimisation
Brute force - testing all combinations of all parameters to find the best combination that gives the best result according to a given criterion, i.e. the best sharpe ratio.

The sharpe ratio is calculated:

```python
def calculate_sharpe_ratio(returns, N=252): # N - dienu skaicius per metus per kurias prekiaujama (pagal nutylejima)
    sharpe_ratio = np.sqrt(N) * (returns.mean() / returns.std())
    return sharpe_ratio
```

Brute force optimisation ([📁 images](https://github.com/evelinavait/Financial-Intelligence/blob/b31fcf136ffb3268d956c6d9a51f448472f947d8/ND3/images) `optimized_nonoptimized_profits.png`):
```python
for window in window_range:
    for std_dev in std_dev_range:
        for transaction_costs in transaction_costs_range:
            df = data_pd[['Close']].copy()
            rez = calculate_bollinger_bands(df, window, std_dev, transaction_costs)
            df = determine_trades(df, stop_loss)
            cumulative_profit = df['total_profit'].cumsum()
            returns = df['total_profit']
            sharpe_ratio = calculate_sharpe_ratio(returns)
            if sharpe_ratio > best_sharpe_ratio:
                best_sharpe_ratio = sharpe_ratio
                optimal_params = {'window': window, 'std_dev': std_dev, 'transaction_costs': transaction_costs}
                optimal_cumulative_profit = cumulative_profit
```
