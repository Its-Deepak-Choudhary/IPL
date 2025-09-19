# Exploratory Data Analysis (EDA) on the IPL Dataset
---
Hello Friends! I have completed my project on the Indian Premier League (IPL) dataset, where I performed Exploratory Data Analysis (EDA) to uncover key insights from the data. This dataset contains information on IPL matches, including details such as teams, toss results, match results, player performances, and match venues across various seasons. By using Python libraries like Pandas, Matplotlib, and Seaborn, I analyzed patterns related to match outcomes, player of the match awards, and seasonal trends. Through visualizations such as bar charts, scatter plots, and histograms, I gained valuable insights into team performances, the influence of batting or bowling first, and the impact of various factors on the match results. The project not only provided a deep dive into IPL data but also helped in identifying significant trends and patterns that could be useful for predictive modeling in the future.

### 1. **Dataset Overview:**

* **Total Rows and Columns:** The dataset contains a total of 30 rows and 17 columns.
* **Features:** The dataset includes features such as:

  * **team1** and **team2**: Represent the two competing teams in each match.
  * **result**: Indicates whether the match was won by runs or wickets.
  * **player\_of\_match**: Lists the player awarded for the best performance in each match.
  * **toss\_winner** and **toss\_decision**: Indicate which team won the toss and whether they chose to bat or field.
  * **win\_by\_runs** and **win\_by\_wickets**: Show the margin by which the winning team won.
  * **venue**: Indicates the stadium where the match took place.

### 2. **Data Cleaning and Preprocessing:**

* **Missing values:** During my analysis, I found no missing values in the dataset. All the columns had complete data.
* **Outliers:** I did not detect any significant outliers in numerical features such as **win\_by\_runs** and **win\_by\_wickets**.
* **Data types:** I converted the **date** column to a datetime format to ensure proper handling of time-related data. Other columns were correctly identified with their respective data types, including categorical features like **team1**, **team2**, and **player\_of\_match**, which were handled as object types.

### 3. **Statistical Summary:**

* **Numerical Features:**

  * **win\_by\_runs** has values ranging from 0 to 97, with an average value of 27.2, indicating the typical margin by which teams win by runs.
  * **win\_by\_wickets** has values from 0 to 10, suggesting the number of wickets by which the match was won.
  * The average **win\_by\_wickets** is 3.5, with a standard deviation of 2.8, meaning most wins are by a margin of around 3 wickets.

* **Categorical Features:**

  * The most frequent **player\_of\_match** awards went to players such as **Yuvraj Singh**, **SPD Smith**, and **CA Lynn**, with each player receiving multiple accolades.
  * The **result** values showed a split between wins by runs and wins by wickets, with wins by wickets being more frequent.

### 4. **Visual Analysis:**

* **Distribution of Key Variables:**

  * **Bar plots** revealed that **Yuvraj Singh** had the highest number of **player\_of\_match** awards, followed by **SPD Smith** and **CA Lynn**.
  * **Histograms** for **win\_by\_runs** showed that most matches were won by a margin of 0-20 runs.
  * **Distribution of wickets** showed that most matches were won by a smaller number of wickets, typically between 3-5 wickets.

* **Correlation:** The correlation heatmap I generated showed no significant correlation between **win\_by\_runs** and **win\_by\_wickets**, suggesting that these two outcomes (winning by runs or wickets) are largely independent.

* **Categorical Insights:**

  * **Bar charts** indicated that teams such as **Mumbai Indians**, **Sunrisers Hyderabad**, and **Royal Challengers Bangalore** were more likely to win when batting first.
  * **Pie charts** I generated revealed that **Mumbai Indians** and **Delhi Daredevils** were the teams with the most wins when batting second.

### 5. **Key Findings:**

* **Player Performance:** I found that players like **Yuvraj Singh** and **CA Lynn** frequently received **Player of the Match** awards, indicating consistent individual performances.

* **Team Performance:** Teams like **Mumbai Indians**, **Delhi Daredevils**, and **Sunrisers Hyderabad** performed better when batting first, suggesting a strategic advantage for these teams when they set the target.

* **Seasonal Trends:** I observed that some teams had consistent winning streaks across seasons, indicating strong team dynamics or well-established strategies.
---

This summary reflects the work that I have done on exploratory data analysis (EDA) for the IPL dataset, including data cleaning, statistical analysis, and visualizations that uncover meaningful insights.

# Code  
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
# Remove the unwanted columns
# Dropping the "ID" and "Date" columns for descriptive analysis
Data_Frame.drop(columns=['id', 'date'], inplace=True)
Data_Frame.head()
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/6.png)

### Bar-Plot
```python
# Getting the Top 5 Players with most 'Man of the Match' awards
colors=['#0867ac', '#ac0867', '#ac6708', '#67ac08', '#6708ac'] # Custom colors
# Making a Bar-Plot 
plt.figure(figsize=(6,4)) # set the figure size
plt.title('Top 5 Players with the Most Man of the Match Awards',color="#ac0867", fontsize=10,fontweight='bold') # Title of the plot
plt.bar(Data_Frame['player_of_match'].value_counts()[0:5].keys(),Data_Frame['player_of_match'].value_counts()[0:5], color=colors)
plt.xlabel('Players', color="#0867ac", fontsize=8,fontweight='bold')
plt.ylabel('Number of Awards', color="#0867ac", fontsize=8,fontweight='bold')
plt.xticks(color="#ac0808", fontsize=8, fontweight='bold')
plt.yticks(color="#055f0a", fontweight='bold')
for i, v in enumerate(Data_Frame['player_of_match'].value_counts()[0:5]):
    plt.text(i - 0.15, v + 0.15, str(v), color='black', fontweight='bold')
plt.show()
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/7.png)

```python
# Getting the frequency of the 'Result' column
Data_Frame['result'].value_counts()
```
```python
# Finding out the number of toss winner teams
Data_Frame['toss_winner'].value_counts()
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/8.png)

```python
# Extracting the records where a team won batting first
# Filter rows where the 'win_by_runs' column is non-zero (indicating a win by batting first)
Batting_First = Data_Frame[Data_Frame['win_by_runs'] != 0]  
Batting_First.head()  
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/9.png)

### Histogram-Plot
```python
# Histogram for the 'win_by_runs' column
plt.figure(figsize=(4, 4))  # Set the size of the plot
plt.title('Distribution of Runs', color='blue', fontsize=15, fontweight='bold')  # Set the title of the plot
plt.hist(Batting_First['win_by_runs'], bins=10, color="#06d433", edgecolor='black')  # Plot a histogram of 'win_by_runs' with 10 bins, green bars, and black edges
plt.xlabel('Runs', color="#ac0808", fontsize=12, fontweight='bold')  # Label the x-axis as 'Runs'
plt.ylabel('Number of Matches', color="#ac0808", fontsize=12, fontweight='bold')  # Label the y-axis as 'Number of Matches'
plt.xticks(color="#ac0808", fontweight='bold')  # Set x-axis tick color and font weight
plt.yticks(color="#055f0a", fontweight='bold')  # Set y-axis tick color and font weight
plt.show()  # Display the plot
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/10.png)

### Bar-Plot
```python
# Making Bar-Plot for Teams with most wins after batting First
# Finding out the number of win records where a team won batting First
Batting_First = Data_Frame['winner'].value_counts()  # Count the number of wins for each team
team_abbr = {  # Define team abbreviations for consistency
    'Sunrisers Hyderabad': 'SRH', 'Mumbai Indians': 'MI',
    'Gujarat Lions': 'GL','Rising Pune Supergiant': 'RPS', 'Rising Pune Supergiants': 'RPS', 'Royal Challengers Bangalore': 'RCB','Kolkata Knight Riders': 'KKR','Delhi Daredevils': 'DD',
    'Delhi Capitals': 'DC','Kings XI Punjab': 'KXIP','Punjab Kings': 'PBKS', 'Chennai Super Kings': 'CSK','Rajasthan Royals': 'RR','Deccan Chargers': 'DCG',
    'Kochi Tuskers Kerala': 'KTK','Pune Warriors': 'PW'
}
colors = ["#4adb07", "#311023", "#061494", "#4a4b48", "#cf0000ae"]  # Color palette for the bars
plt.figure(figsize=(4, 4))  # Set the plot size
plt.title('Teams with most wins batting first', color='#850650', fontsize=10, fontweight='bold')  # Set the title of the plot
plt.bar(Batting_First.index[0:5].to_series().replace(team_abbr), Batting_First.values[0:5], color=colors)  # Bar plot for top 5 teams
plt.xlabel('Teams', color="#0867ac", fontsize=12, fontweight='bold')  # X-axis label
plt.ylabel('Number of Wins', color="#0867ac", fontsize=12, fontweight='bold')  # Y-axis label
plt.xticks(color="#ac0808", fontweight='bold')  # X-axis tick styling
plt.yticks(color="#055f0a", fontweight='bold')  # Y-axis tick styling
for i, v in enumerate(Batting_First.values[0:5]):  # Annotate bars with values
    plt.text(i - 0.1, v + 0.50, str(v), color='black', fontweight='bold')  # Place text on top of bars
    
plt.tight_layout()  # Adjust layout for better fit
plt.show()  # Display the plot
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/11.png)

### Bar-Plot
```python
top_3_batting_first = Data_Frame['winner'].value_counts()[0:3]  # Get top 3 teams with most wins batting first
plt.figure(figsize=(4, 4))  # Set the figure size
colors = ["#0aa2adc8", "#055C33", "#179C0B"]  # Custom color palette for the bars
plt.bar(top_3_batting_first.index.to_series().replace(team_abbr), top_3_batting_first.values, color=colors)  # Bar plot for top 3 teams
plt.title('Top 3 Teams with most wins batting first', color="#1e6109", fontsize=10, fontweight='bold')  # Title of the plot
plt.xlabel('Teams', color='#000000', fontsize=10, fontweight='bold')  # X-axis label
plt.ylabel('Number of Wins', color='#000000', fontsize=10, fontweight='bold')  # Y-axis label
for i, v in enumerate(top_3_batting_first.values):  # Add text labels on top of the bars
    plt.text(i - 0.1, v + 0.80, str(v), color='black', fontweight='bold')  # Display number of wins above each bar
plt.show()  # Display the plot
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/12.png)

### Histogram-Plot
```python
# Filter matches where 'win_by_wickets' is non-zero (indicating a win by batting second)
batting_second_wins = Data_Frame[Data_Frame['win_by_wickets'] != 0].value_counts()
```
```python
# Extracting the records where a team won bowling First
plt.figure(figsize=(4, 4))  # Set the figure size
plt.title('Distribution of Wickets', color='blue', fontsize=15, fontweight='bold')  # Set the title of the plot
plt.hist(Data_Frame[Data_Frame['win_by_wickets'] != 0]['win_by_wickets'], bins=30, color="#01e297", edgecolor='black')  # Plot histogram for wins by wickets
plt.xlabel('Wickets', color="#ac0808", fontsize=12, fontweight='bold')  # Label x-axis as 'Wickets'
plt.ylabel('Number of Matches', color="#ac0808", fontsize=12, fontweight='bold')  # Label y-axis as 'Number of Matches'
plt.xticks(color="#ac0808", fontweight='bold')  # Set x-axis tick color and font weight
plt.yticks(color="#055f0a", fontweight='bold')  # Set y-axis tick color and font weight
plt.show()  # Display the plot
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/13.png)

### Bar-Plot
```python
# Bar Chart for teams with most wins batting second
batting_second_win = Data_Frame[Data_Frame['win_by_wickets'] != 0]['winner'].value_counts()  # Count wins for teams batting second
# Create a figure for the bar chart
plt.figure(figsize=(4, 4))  # Set figure size
# Get top 3 teams and their values
top_3_batting_second = batting_second_win[0:3]
top_3_labels = top_3_batting_second.index.to_series().replace(team_abbr)
# Bar plot
plt.bar(top_3_labels, top_3_batting_second.values, color=["red", "green", "blue"])  # Bar chart
# Title and labels
plt.title('Top 3 Teams with most wins Batting Second', color='#850650', fontsize=10, fontweight='bold')  # Title for the bar chart
plt.xlabel('Teams', color='#0867ac', fontsize=8, fontweight='bold')  # X-axis label
plt.ylabel('Number of Matches', color='#ac5208', fontsize=8, fontweight='bold')  # Y-axis label
# Add text labels on top of the bars
for i, v in enumerate(top_3_batting_second.values):
    plt.text(i - 0.1, v + 0.50, str(v), color='black', fontweight='bold')  # Annotate bars
# Show the bar plot
plt.show()
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/14.png)

### Pie-Plot
```python
# Pie Chart for teams with most wins batting second
batting_second_win = Data_Frame[Data_Frame['win_by_wickets'] != 0]['winner'].value_counts()  # Count wins for teams batting second
top_3_batting_second = batting_second_win[0:5]
# Create a figure for the pie chart
plt.figure(figsize=(4, 4))  # Set figure size
# Pie chart
plt.pie(
    top_3_batting_second.values,  # Values for the pie chart
    labels=top_3_batting_second.index.to_series().replace(team_abbr),  # Labels for teams
    colors=["#c3d806", "#0B8B65", "#46D603"],  # Pie chart colors (3 colors for 3 teams)
    autopct='%0.1f%%',  # Display percentage on the pie slices
    startangle=140,  # Start angle for the pie chart
    textprops={'color':"black", 'fontweight':'bold'}, 
    wedgeprops={'width': 0.7, 'edgecolor': 'white'}  
)
# Title for the pie chart
plt.title('Teams with most wins Batting Second', color='#850650', fontsize=10, fontweight='bold')
# Show the pie chart
plt.show()
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/15.png)

```python
# In which city are the matches being held
Data_Frame['city'].value_counts()
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/16.png)

```python
# Count the number of matches played in each season
Data_Frame['season'].value_counts()
```
```python
# Finding out how many times each team has won matches
win_count = np.sum(Data_Frame['toss_winner']==Data_Frame['winner'])
win_count
```
![](https://github.com/Its-Deepak-Choudhary/IPL/blob/master/images/17.png)

# Conclusion:

Teams like Mumbai Indians, Kolkata Knight Riders, and Chennai Super Kings are strong contenders both in toss wins and match outcomes.
Chris Gayle, AB de Villiers, and MS Dhoni have consistently performed well and made a significant impact on match results.
While most matches are concluded with a winner, the presence of ties and no-results is low.
The dataset also shows certain missing values, which could be addressed if needed for more granular analysis.
Overall, there is a wealth of insights available for deeper statistical analysis, like win percentages based on toss decisions, team performance across seasons, and individual player contributions.
