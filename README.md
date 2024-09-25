# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the student study hours marks data set.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Create the dataset
df = pd.read_csv('score.csv')

# Since we don't have actual time data, we will create a pseudo-time index for the dataset
df['Index'] = range(1, len(df) + 1)
df.set_index('Index', inplace=True)

# Plot the Scores
plt.figure(figsize=(10, 6))
plt.plot(df['Scores'], label='Scores')
plt.title('Scores over Pseudo-Time (Index)')
plt.xlabel('Index (Pseudo-Time)')
plt.ylabel('Scores')
plt.legend()
plt.show()

# Perform seasonal decomposition using the 'Index' as a pseudo-time component
# We can assume additive decomposition here for illustration
decomposition = seasonal_decompose(df['Scores'], model='additive', period=4)

# Plot the decomposed components
decomposition.plot()
plt.show()

# Accessing components
trend = decomposition.trend
seasonal = decomposition.seasonal
residual = decomposition.resid

# Display the trend, seasonality, and residuals
print("Trend:\n", trend.dropna())  # dropna to remove any missing values
print("Seasonal:\n", seasonal.dropna())
print("Residual:\n", residual.dropna())
```

### OUTPUT:
![download](https://github.com/user-attachments/assets/09c1d8a4-77bf-4ef6-8941-90b6d36df63c)
![download](https://github.com/user-attachments/assets/0dd4200e-6c1f-4238-b74e-a1954fd31c7c)
Trend:
 Index
3     43.625
4     41.375
5     45.625
6     51.375
7     55.875
8     62.875
9     63.125
10    63.000
11    58.250
12    55.375
13    49.000
14    44.625
15    47.375
16    43.750
17    47.750
18    50.750
19    47.500
20    51.250
21    51.000
22    47.875
23    55.750
Name: trend, dtype: float64
Seasonal:
 Index
1     -7.805208
2    -17.430208
3      2.865625
4     22.369792
5     -7.805208
6    -17.430208
7      2.865625
8     22.369792
9     -7.805208
10   -17.430208
11     2.865625
12    22.369792
13    -7.805208
14   -17.430208
15     2.865625
16    22.369792
17    -7.805208
18   -17.430208
19     2.865625
20    22.369792
21    -7.805208
22   -17.430208
23     2.865625
24    22.369792
25    -7.805208
Name: seasonal, dtype: float64
Residual:
 Index
3    -19.490625
4     11.255208
5     -7.819792
6    -13.944792
7     29.259375
8    -25.244792
9     25.680208
10   -20.569792
11    23.884375
12   -15.744792
13    -0.194792
14    14.805208
15   -33.240625
16    28.880208
17    -9.944792
18    -9.319792
19    16.634375
20    -4.619792
21   -13.194792
22    23.555208
23   -23.615625
Name: resid, dtype: float64


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
