# Financial-Intelligence ND5
[English below]

## 5. Pair Trading
Šiame aplankale pateikiama Python programinis kodas `Finansinis_intelektas_ND5_E_Vaitkeviciute.ipynb`.

**Dalis A** – analizuojamos kointegruotos poros: `'KO'` - Coca-Cola Co; `'PEP'` - PepsiCo Inc.

**Dalis B** – analizuojamos kointegruotos poros: `'META'` -  Meta Platforms Inc., `'NVDA'` - NVIDIA Corp

### Dalis A
Analizuojamos kointegruotos poros, turinčios didelį teigiamą koreliacijos koeficientą: 'KO' - Coca-Cola Co; 'PEP' - PepsiCo Inc.

Naudojant `calculate_spread` atliekamas stacionarumo testas, o funkcija `generate_signals` generuojami prekybos signalai.

```python
def generate_signals(spread, ko_data, pep_data, spread_mean, spread_std, upper_threshold, lower_threshold)
```

Prekybos signalams generuoti naudojamos dviejų akcijų kainų santykio z-score ir nustatomos viršutinė ir apatinė ribos. Tai parodo, kaip toli kaina yra nuo vidutinės vertės.

```python
def zscore(series):
    return (series - series.mean()) / np.std(series)
```

Funkcija, reikalinga apskaičiuoti pelną (angl. *profit*):

```python
def calculate_profit(signals, ko_data, pep_data)
```

Kainų ir stacionarumo (spread) grafikai vaizduojami, naudojant `plot_price_and_spread`:

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/8df5b9a673a818f8ca022fcacaf4bce19eb568a4/ND5/images/pairs_trading_strategy_KO_PEP.png" width="800"/>

Pelno grafikas vaizduojamas, naudojant `plot_cumulative_profit`:

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/8df5b9a673a818f8ca022fcacaf4bce19eb568a4/ND5/images/cumulative_profits_pairs_trading_strategy_KO_PEP.png" width="800"/>

### Dalis B
Toliau buvo atllikta tokia pati analizė kointegruotoms poroms `'META'` -  Meta Platforms Inc. ir `'NVDA'` - NVIDIA Corp. Gauti rezultatai, pavaizduoti žemiau pateiktuose grafikuose:

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/bc227a52113a27b1ccc3f297a5d6df9ae8707abb/ND5/images/pairs_spread_META_NVDA.png" width="750" height="350"/>

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/bc227a52113a27b1ccc3f297a5d6df9ae8707abb/ND5/images/pairs_trading_strategy_META_NVDA.png" width="850"/>

Visi aukščiau pateikti ir papildomi grafikai patalpinti aplanke [📁 images](https://github.com/evelinavait/Financial-Intelligence/tree/bc227a52113a27b1ccc3f297a5d6df9ae8707abb/ND5/images).

-------------
## 5. Pair Trading
This folder contains Python code `Finansinis_intelektas_ND5_E_Vaitkeviciute.ipynb`.

**Part A** - cointegrated pairs are analysed: `'KO'` - Coca-Cola Co; `'PEP'` - PepsiCo Inc.

**Part B** - analysis of the cointegrated pairs: `'META'` - Meta Platforms Inc.; `'NVDA'` - NVIDIA Corp.

### Part A
The integrated pairs that affect the positive correlation coefficient are analyzed: `'KO'` - Coca-Cola Co; `'PEP'` - PepsiCo Inc.

`calculate_spread` is used for the stationarity test, and the `generate_signals` function generates trading signals.

```python
def generate_signals(spread, ko_data, pep_data, spread_mean, spread_std, upper_threshold, lower_threshold)
```

To generate trading signals, the z-scores of the ratio of the prices of the two stocks are used and the upper and lower limits are set. This shows how far the price is from the average value.

```python
def zscore(series):
    return (series - series.mean()) / np.std(series)
```

Function to calculate profit:

```python
def calculate_profit(signals, ko_data, pep_data)
```

The price and spread plots are visualised using function `plot_price_and_spread`.

### Part B
The same analysis was applied to the cointegrated pairs `'META'` - Meta Platforms Inc. and `'NVDA'` - NVIDIA Corp. The results are shown in the plots above and are placed in the [📁 images](https://github.com/evelinavait/Financial-Intelligence/tree/bc227a52113a27b1ccc3f297a5d6df9ae8707abb/ND5/images) folder.
