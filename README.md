### **Exploratory Data Analysis (EDA) on IPL Dataset**

This analysis performs an in-depth **Exploratory Data Analysis (EDA)** on the IPL dataset, focusing on various aspects of the Indian Premier League. The goal is to uncover insights related to match outcomes, player performances, team statistics, and trends over the seasons.

#### Key areas explored include:

* **Data Preprocessing**: The dataset was cleaned and formatted, with conversion of the `date` column to the correct datetime type.

* **Player Performance**: The analysis identifies the top players based on the number of **"Man of the Match"** awards, with visualizations highlighting the top 5 players.

* **Team Performance**: The dataset was examined for team performances in different scenarios. The number of wins for teams batting first and second was analyzed, with bar plots showing the top teams in both categories.

* **Match Outcomes**: The distribution of match results by **runs** and **wickets** was analyzed through histograms. Teams with the most wins after batting first and second were also visualized using bar plots.

* **Toss Insights**: The frequency of **toss winners** was examined, with further exploration into how toss outcomes may impact match results.

* **City and Season Insights**: The analysis reveals where matches are most commonly held (by city) and tracks the number of matches played in each season.

* **Advanced Visualizations**: The analysis includes detailed **pie charts** showing the proportion of wins for teams batting second, as well as customized **bar charts** and **histograms** to visualize performance trends in the IPL.

The insights gained from this EDA help to better understand IPL match dynamics, player and team performances, and how certain factors, like batting order or toss wins, might influence the outcome of games.


# Code: 
```python
# Add important Library
import pandas as pd  # Import pandas library for data manipulation
from matplotlib import pyplot as plt  # Import pyplot for data visualization
import seaborn as sns  # Import seaborn for advanced statistical data visualization
import numpy as np
```

```python
# Load the dataset
Data_Frame = pd.read_csv('matches.csv')  # Load data from 'matches.csv' into a pandas DataFrame
```

```python
# See the first 3 rows of the dataset
Data_Frame.head(3)  # Displays the first 3 rows of the DataFrame to preview the data
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/1.png)

```python
# Displays summary information about the DataFrame, including data types and non-null counts
Data_Frame.info()  
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/2.png)

```python
# Convert the datatype of the column 'date' to datetime, handling mixed formats and assuming day-first
Data_Frame['date'] = pd.to_datetime(Data_Frame['date'], format='mixed', dayfirst=True)  
Data_Frame.info()  # verify the changes
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/3.png)

```python
# Looking for the number of rows and columns in this dataset
Data_Frame.shape
```
```python
# Getting the frequency of most 'Man of the Match' awards 
Data_Frame['player_of_match'].value_counts()
```
```python
# Getting the top 10 players with most 'Man of the Match' awards 
Data_Frame['player_of_match'].value_counts()[0:10]
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/4.png)

```python
# Getting the names of the top 10 players with most 'Man of the Match' awards
Data_Frame['player_of_match'].value_counts()[0:10].keys()
```
```python
# Describe the dataset
Data_Frame.describe()
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/5.png)

```python

```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/2.png)

```python

```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/2.png)

```python

```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/2.png)

```python

```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/2.png)

```python

```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/2.png)

```python

```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/2.png)

```python

```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/2.png)
