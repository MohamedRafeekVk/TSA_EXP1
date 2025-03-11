# Ex.No: 01A PLOT A TIME SERIES DATA
###  Date: 11/03/2025
## Reg.no: 212224220063


# AIM:
To Develop a python program to Plot a time series data (population/ market price of a commodity
/temperature.
# ALGORITHM:
1. Import the required packages like pandas and matplot
2. Read the dataset using the pandas
3. Calculate the mean for the respective column.
4. Plot the data according to need and can be altered monthly, or yearly.
5. Display the graph.
# PROGRAM:
```
import numpy as np
import pandas as pd


import os
for dirname, _, filenames in os.walk('/kaggle/input'):
    for filename in filenames:
        print(os.path.join(dirname, filename))

import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns
import warnings
warnings.filterwarnings('ignore')

df = pd.read_csv("/Users/admin/ODI Cricket Data new.csv")

df.head()

df.tail()

df.count

df.info()

df.describe()

df.isnull().sum()

df.duplicated()

df.corr

cols_to_convert = ['strike_rate', 'average', 'percentage']
for col in cols_to_convert:
    df[col] = df[col].str.replace(',', '').str.replace('%', '').str.strip()
    df[col] = pd.to_numeric(df[col], errors='coerce')

missing = df.isnull().sum()

print(missing[missing > 0])
df = df.dropna().reset_index(drop=True)
print('DataFrame shape after dropping missing values:', df.shape)
df['total_contribution'] = df['total_runs'] + df['total_wickets_taken']

numeric_columns = df.select_dtypes(include=[np.number]).columns.tolist()

df.columns

sns.set_style("darkgrid")
plt.rcParams["figure.figsize"] = (10, 5)


plt.figure()
plt.hist(df['total_runs'], bins=30, color='darkblue', edgecolor='black')
plt.xlabel("Total Runs")
plt.ylabel("Number of Players")
plt.title("Distribution of Total Runs")
plt.show()

plt.figure()
sns.scatterplot(x='strike_rate', y='total_runs', hue='role', data=df, palette="coolwarm")
plt.xlabel("Strike Rate")
plt.ylabel("Total Runs")
plt.title("Strike Rate vs. Total Runs")
plt.show()


top_scorers = df.nlargest(10, 'total_runs')
plt.figure()
sns.barplot(x='total_runs', y='player_name', data=top_scorers, palette="Greens_r")
plt.xlabel("Total Runs")
plt.ylabel("Player Name")
plt.title("Top 10 Run Scorers")
plt.show()


plt.figure()
sns.boxplot(x='matches_played_as_batter', y='total_runs', data=df)
plt.xlabel("Matches Played as Batter")
plt.ylabel("Total Runs")
plt.title("Matches as Batter vs. Total Runs")
plt.show()


plt.figure()
plt.hist(df['total_wickets_taken'], bins=20, color='darkred', edgecolor='black')
plt.xlabel("Total Wickets Taken")
plt.ylabel("Number of Players")
plt.title("Distribution of Total Wickets Taken")
plt.show()


plt.figure()
sns.scatterplot(x='total_runs_conceded', y='total_wickets_taken', hue='role', data=df, palette="coolwarm")
plt.xlabel("Total Runs Conceded")
plt.ylabel("Total Wickets Taken")
plt.title("Wickets Taken vs. Runs Conceded")
plt.show()


top_wicket_takers = df.nlargest(10, 'total_wickets_taken')
plt.figure()
sns.barplot(x='total_wickets_taken', y='player_name', data=top_wicket_takers, palette="Blues_r")
plt.xlabel("Total Wickets Taken")
plt.ylabel("Player Name")
plt.title("Top 10 Wicket-Takers")
plt.show()


plt.figure()
df.groupby('team')[['matches_won', 'matches_lost']].sum().plot(kind='bar', stacked=True, color=['darkblue', 'darkred'])
plt.xlabel("Team")
plt.ylabel("Matches Won/Lost")
plt.title("Team Matches Won vs. Lost")
plt.legend(["Won", "Lost"])
plt.show()


top_award_players = df.nlargest(10, 'player_of_match_awards')


plt.figure(figsize=(10, 6))


sns.barplot(x='player_of_match_awards', y='player_name', data=top_award_players, palette="flare")


plt.xlabel("Player of the Match Awards")
plt.ylabel("Player Name")
plt.title("Top 10 Players with Most Player of the Match Awards")


plt.show()


plt.figure()
sns.boxplot(x='team', y='percentage', data=df)
plt.xlabel("Team")
plt.ylabel("Win Percentage")
plt.title("Team Performance Comparison")
plt.xticks(rotation=90)
plt.show()


plt.figure()
sns.violinplot(x='role', y='total_runs', data=df, inner='quartile', palette="Set2")
plt.xlabel("Role")
plt.ylabel("Total Runs")
plt.title("Batting Performance by Role")
plt.show()


plt.figure()
sns.scatterplot(x='total_matches_played', y='average', hue='role', data=df, palette="coolwarm")
plt.xlabel("Total Matches Played")
plt.ylabel("Batting Average")
plt.title("Average Runs vs. Matches Played")
plt.show()
```
# OUTPUT:

![Graph 1](https://github.com/user-attachments/assets/72543747-d7f5-4c24-834d-5db0ddd88b47)
![Graph 2](https://github.com/user-attachments/assets/1d7adcce-33e9-4365-90ee-709bee775168)
![Graph 3](https://github.com/user-attachments/assets/128802fa-5960-41b9-a318-bcb8c08db9e3)

# RESULT:
Thus we have created the python code for plotting the time series of given data.
