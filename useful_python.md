# Useful Python Snippets

### Iterate on Files in Directory

```py
import os

import pandas as pd

data_path = r'C:\Users\Jeremy\Downloads'

for filename in os.listdir(data_path):
    if filename.endswith('.csv'):
        table_name = filename.replace('.csv', '')
        print(table_name)
        df = pd.read_csv(os.path.join(data_path, filename))
```