---
## SOAL
  1. Ditahun berapa hujan harian maksimum (HMT) tertinggi tercatat (berdasarkan 4 sumber data hujan tersebut). Apakah 4
     summber data tersebut menunjukkan hasil yang identik?
  2. Berapa rerata HMT sepanjang tahun 2001-2022 untuk masing-masing sumber data hujan?
  3. Sumber data apa yang menunjukkan tendensi nilai HMT yang lebih rendah dan tinggi dibandingkan dengan data lain?

---

```{python}
import pandas as pd
import matplotlib.pyplot as plt
import calendar
import os,glob
