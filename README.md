# IPL
This repo contains an EDA of the IPL dataset, analyzing player and team performances. It includes visualizations of "Man of the Match" awards, team wins, batting strategies, and more using libraries like pandas, matplotlib, and seaborn. Run the script to explore the data!

### **IPL Data Analysis and Visualization**

This repository contains an exploratory data analysis (EDA) of the Indian Premier League (IPL) dataset. The dataset includes detailed information about IPL matches, including match results, player performances, toss winners, and more. The analysis provides insights into various aspects of IPL matches, such as top performers, team performances, and trends over the seasons.

#### **Key Features:**

* **Data Preprocessing**: Clean and preprocess the dataset by handling missing values, converting data types, and dropping unnecessary columns.
* **Player Performance Analysis**: Identify the top players based on 'Man of the Match' awards.
* **Team Performance Insights**: Explore how teams perform in different scenarios (batting first vs. bowling first) and which teams have the most wins in each case.
* **Data Visualization**: Use visualizations (bar plots, histograms, pie charts) to represent the analysis results and better understand trends, such as:

  * Top players with the most "Man of the Match" awards
  * Distribution of match outcomes based on runs or wickets
  * Teams with the most wins after batting first or second
* **Season-wise and City-wise Insights**: Analyze the number of matches played in each season and the cities where the matches are most commonly held.
* **Advanced Visualizations**: Detailed plots such as pie charts, bar charts, and histograms to visually compare the performances of players and teams.

#### **Data Source:**

The analysis is performed on the IPL dataset, which can be obtained from various online sources like Kaggle or IPL's official data. The dataset used here includes key columns such as `match_id`, `date`, `team1`, `team2`, `winner`, `player_of_match`, and more.

#### **Libraries Used:**

* `pandas`: For data manipulation and analysis.
* `matplotlib`: For creating static, animated, and interactive visualizations in Python.
* `seaborn`: For statistical data visualization.
* `numpy`: For numerical computations and operations.

#### **Output:**

The analysis outputs multiple visualizations, including:

* Bar plots showcasing the top players with the most "Man of the Match" awards.
* Histograms representing the distribution of wins by runs and wickets.
* Pie charts showing the proportion of wins for teams batting second.

#### **How to Use:**

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/your-username/ipl-eda.git
   ```

2. **Install Dependencies**:

   * Make sure you have Python installed (version 3.7 or higher).
   * Install the required libraries using pip:

   ```bash
   pip install pandas matplotlib seaborn numpy
   ```

3. **Run the Script**:

   * Place the IPL dataset (`matches.csv`) in the same directory as the Python script.
   * Run the script to see the EDA and visualizations:

   ```bash
   python ipl_eda.py
   ```

---

Let me know if you need to modify or add anything specific to this!

