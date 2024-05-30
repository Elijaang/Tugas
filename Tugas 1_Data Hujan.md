---
## SOAL
  1. Lakukan Filtering data hujan CHIRPS dari file "Data_hujan_multi_harian.csv" hanya pada tahun kelahiran anda. Lalu resample berdasarkan minggu. Di bulan dan minggu ke berapa hujan akumulasi paling besar terjadi?
  2. Visualisasi box plot per bulan berdasarkan data PERSIANN. Bulan apa yang memiliki nilai hujan bulanan tertinggi dan terendah?
  3. Plotkan grafik contoh hubungan hujan debit pada _range_ tanggal kelahiran anda (seminggu sebelum hingga seminggu setelah) berdasarkan data GPM!  
---
## 1. Pengertian Pandas
Pandas (Python Data Analysis Library) adalah sebuah library Python yang menyediakan alat analisis dan pengolahan data, diantaranya adalah membaca file data seperti Excel

# SOAL NO 1
## Langkah Pertama
Meng Import seluruh library yang diperlukan.

```{python}
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```
## Langkah Kedua 
Mengubah bagian kolom tanggal menjadi index

```{python}
# SOAL NO 1
# Membuat DataFrame dengan index datetime
df = pd.read_csv("Data_hujan_multi_harian.csv")

# Mengubah kolom tanggal menjadi tipe datetime
df['Date'] = pd.to_datetime(df['Date'])
df = df.dropna()

# Menjadikan kolom tanggal sebagai indeks
df.set_index('Date', inplace=True)
```

## Langkah Ketiga
Membuat data hujan terbaca hanya pada tahun kelahiran saya

```{phyton}
# Filtering data berdasarkan tanggal
filtered_df = df.loc['2005-01-01':'2005-12-30']
```

## Langkah Keempat


```{pyhton}
# Berdasarkan per minggu
weekly_accumulation = filtered_df['CHIRPS'].resample('W').sum()

# Mencari bulan dan minggu dengan hujan akumulasi paling besar
bulan_max = weekly_accumulation.idxmax()
hujan_max = weekly_accumulation.max()
```

## Langkah Kelima
Lakukan print( untuk memunculkan data output di program yang sudah dibuat

```{python}
print("\nData Mingguan :")
print(weekly_accumulation)
print('\nData CHIRPS')
print("Bulan:", bulan_max.month_name())
print("Minggu ke:", bulan_max.week)
print("Total Hujan Akumulasi:", hujan_max, "mm")
```
## Hasil Program

```{python}
# -*- coding: utf-8 -*-
"""
Created on Tue May 28 01:49:06 2024

@author: Gilang
"""

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# SOAL NO 1
# Membuat DataFrame dengan index datetime
df = pd.read_csv("Data_hujan_multi_harian.csv")

# Mengubah kolom tanggal menjadi tipe datetime
df['Date'] = pd.to_datetime(df['Date'])
df = df.dropna()

# Menjadikan kolom tanggal sebagai indeks
df.set_index('Date', inplace=True)

# Filtering data berdasarkan tanggal
filtered_df = df.loc['2005-01-01':'2005-12-30']

# Berdasarkan per minggu
weekly_accumulation = filtered_df['CHIRPS'].resample('W').sum()

# Mencari bulan dan minggu dengan hujan akumulasi paling besar
bulan_max = weekly_accumulation.idxmax()
hujan_max = weekly_accumulation.max()

print("\nData Mingguan :")
print(weekly_accumulation)
print('\nData CHIRPS')
print("Bulan:", bulan_max.month_name())
print("Minggu ke:", bulan_max.week)
print("Total Hujan Akumulasi:", hujan_max, "mm")
