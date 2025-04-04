# Financial-Intelligence ND1
[English below]
## Finansinis intelektas ND1

Šiame aplankale pateikiama Python programinis kodas bei duomenys.

Python programiniame kode `Finansinis_intelektas_ND1_E_Vaitkeviciute.ipynb` įgyvendinta:
  
- Smulkių užduočių atlikimas, naudojant `numpy` ir `pandas` bibliotekas;

- Tikinių duomenų `'EURUSD-2023-04.csv'` ir dieninių duomenų `'daily_data_AAPL.csv'` atvaizdavimas, naudojant funkciją `read_data`:

```python
read_data('EURUSD-2023-04.csv')
read_data('daily_data_AAPL.csv', header=0)
```

- Minutinių duomenų atvaizdavimas, naudojant funkciją `minute_data`:

```python
def minute_data(symbol, start_date, end_date, output_file, date_format='%Y-%m-%d %H:%M:%S%z')

minute_data("AAPL", "2024-02-13", "2024-02-14", "minute_data_AAPL.csv")
```

- Atsitiktinių duomenų generavimas ir atvaizdavimas - generuojami ir atvaizduojami duomenys, kurie vizualiai būtų panašūs į rinkos kainų kitimo duomenis;

```python
def generate_data(num_points):
    random = np.random.randn(num_points)
    data = np.abs(random.cumsum())
    return data
```

- Sudaromos sesijos iš minutinių, tikinių (E-Mini S&P 500 Mar 24 (ES=F)) duomenų 2024-02-13 – 2024-02-16 laikotarpiu:

<img src="https://github.com/user-attachments/assets/564676e1-6466-43ea-a253-bcf87c689c51" width="800"/>

- Iš kviečių/kukurūzų ar pan. kainų suskaičiuojama, kaip keičiasi kainos metų bėgyje (paimami 10 metų duomenys, uždedama kas metus vieną ant kito ir suskaičiuojama vidutiniškas kainų pokytis per metus skirtingomis dienomis):

<img src="https://github.com/user-attachments/assets/7efba5cc-94b5-40c1-bc39-3c284dab1331" width="700"/>

-------------
## Financial-Intelligence ND1
This folder contains Python code and data.

The Python code `Finansinis_intelektas_ND1_E_Vaitkeviciute.ipynb` implements:
  
- Performing simple tasks using the `numpy` and `pandas` libraries;

- Displaying the tick data `'EURUSD-2023-04.csv'` and the daily data `'daily_data_AAPL.csv'` using the `read_data` function:

```python
read_data('EURUSD-2023-04.csv')
read_data('daily_data_AAPL.csv', header=0)
```

- Displaying minute data using the `minute_data` function:

```python
def minute_data(symbol, start_date, end_date, output_file, date_format='%Y-%m-%d %H:%M:%S%z')

minute_data("AAPL", "2024-02-13", "2024-02-14", "minute_data_AAPL.csv")
```

- Random data generation and display - generating and displaying data that is visually similar to market price movements:

```python
def generate_data(num_points):
    random = np.random.randn(num_points)
    data = np.abs(random.cumsum())
    return data
```

- Sessions are created from minute, tick (E-Mini S&P 500 Mar 24 (ES=F)) data for the period 2024-02-13 - 2024-02-16 ([📁 images](https://github.com/evelinavait/Financial-Intelligence/tree/76480a4fa3dc1609179c899a7eb0b64abf95c1fa/ND1/images) `trading_sessions.png`);
- From the prices of wheat/corn or similar, it is calculated how prices change over the year (10 years of data are taken, each year is superimposed on the other and the average price change over the year on different days is calculated) ([📁 images](https://github.com/evelinavait/Financial-Intelligence/tree/76480a4fa3dc1609179c899a7eb0b64abf95c1fa/ND1/images) `wheat_futures.png`).

