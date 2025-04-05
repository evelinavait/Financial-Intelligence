# Financial-Intelligence ND2
[English below]

## 2. Indikatorių programavimas
Šiame aplankale pateikiama Python programinis kodas bei duomenys. Manipuliuojama duomenimis sudėtingesniais metodais ir suprogramuojami žinomi duomenų analizės algoritmai / indikatoriai.

Python programiniame kode `Finansinis_intelektas_ND2_E_Vaitkeviciute.ipynb` įgyvendinta:
  
**Dalis A** – indikatoriai Yahoo Finance ir TradingView platformoje;

**Dalis B** – indikatorių (Chaikin Volatility (CV), Mass Index (MI), Money Flow Index) programavimas Python.

Chaikin Volatility (CV), Mass Index (MI) indikatorių vizualizavimui naudojama funkcija:

```python
def plot_stock_analysis(data, dates, indicator_values, period, label, indicator_name)
```

Suprogramuotų indikatorių pavyzdžiai pateikti aplankale [📁 images](https://github.com/evelinavait/Financial-Intelligence/tree/789fee38fdc33c2543fe473a90d04b7bcab4ff89/ND2/images);

### Chaikin Volatility (CV) (kintamumo indikatorius)
Funkcija, skirta apskaičiuoti eksponentinį slenkamąjį vidurkį (angl. *Exponential Moving Average*):

```python
def ema_custom(data, window) # data - duomenys; window - laikotarpis
```

Funkcija, skirta apskaičiuoti Chaikin Volatility (CV) kintamumo indikatorių:

```python
def chaikin_volatility(df, window=14)
```

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/789fee38fdc33c2543fe473a90d04b7bcab4ff89/ND2/images/AAPL_Chaikin_Volatility.png" width="800"/>

### Mass Index (MI) (kintamumo indikatorius)
Funkcija, skirta apskaičiuoti Mass Index (MI) kintamumo indikatorių:

```python
def mass_index(data, period=25, ema_period=9, high_col='High', low_col='Low')
```

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/789fee38fdc33c2543fe473a90d04b7bcab4ff89/ND2/images/AAPL_MI.png" width="800"/>

### Money Flow Index
Funkcija, skirta apskaičiuoti Money Flow Index indikatorių:

```python
def money_flow_index(data, period=14, high_col='High', low_col='Low', close_col='Close', volume_col='Volume'):
```

Indikatoriaus Money Flow Index vizualizavimui naudojama funkcija:

```python
def plot_mfi(data, label)
```

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/789fee38fdc33c2543fe473a90d04b7bcab4ff89/ND2/images/AAPL_MFI.png" width="800"/>

-------------
## 2. Programming indicators

This folder contains Python code and data. Data is manipulated using more complex methods and known data analysis algorithms/indicators are programmed.

The Python code `Finansinis_intelektas_ND2_E_Vaitkeviciute.ipynb` implements:

**Part A** - indicators on Yahoo Finance and TradingView platform;

**Part B** - programming the indicators (Chaikin Volatility (CV), Mass Index (MI), Money Flow Index) in Python.

Function used to visualise Chaikin Volatility (CV), Mass Index (MI) indicators:

```python
def plot_stock_analysis(data, dates, indicator_values, period, label, indicator_name)
```

Examples of the indicators programmed are available in [📁 images](https://github.com/evelinavait/Financial-Intelligence/tree/789fee38fdc33c2543fe473a90d04b7bcab4ff89/ND2/images);

### Chaikin Volatility (CV) (volatility indicator)
Function to calculate the exponential moving average (*Exponential Moving Average*):

```python
def ema_custom(data, window) # data - data; window - period
```

Function to calculate the Chaikin Volatility (CV) volatility indicator:

```python
def chaikin_volatility(df, window=14)
```

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/493c72a252fd0ab5c51497b833eae75585b38f0b/ND2/images/TESLA_Chaikin_Volatility.png" width="800"/>

### Mass Index (MI) (variability indicator)
Function to calculate the Mass Index (MI) variability indicator:

```python
def mass_index(data, period=25, ema_period=9, high_col='High', low_col='Low')
```

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/493c72a252fd0ab5c51497b833eae75585b38f0b/ND2/images/TESLA_MI.png" width="800"/>

### Money Flow Index
Function to calculate the Money Flow Index indicator:

```python
def money_flow_index(data, period=14, high_col='High', low_col='Low', close_col='Close', volume_col='Volume'):
```

Function used to visualise the Money Flow Index:

```python
def plot_mfi(data, label)
```

<img src="https://github.com/evelinavait/Financial-Intelligence/blob/493c72a252fd0ab5c51497b833eae75585b38f0b/ND2/images/TESLA_MFI.png" width="800"/>

