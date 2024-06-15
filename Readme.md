<h1>Datacamp: Investigating Netflix movies</h1>


![image](redpopcorn.jpg)


## Solution Python

```python

# Importing pandas and matplotlib
import pandas as pd
import matplotlib.pyplot as plt

# Read in the Netflix CSV as a DataFrame
df = pd.read_csv("netflix_data.csv")
# Start coding here! Use as many cells as you like
# print(df.head())
df_90 = df[(df['type'] == 'Movie') & (df['release_year'] >= 1990) & (df['release_year'] <= 1999)]
df_90 = df_90[["title","release_year","duration","genre"]]
# print(df_1.head())
df_90['duration'] = df_90['duration'].astype(str)
df_90['duration'] = df_90['duration'].str.extract('(\d+)').astype(int)

# print(df_90['duration'])
# Find the most frequent duration
duration = df_90['duration'].mode()[0]

# Print the most frequent duration
print(duration)
short_movies = df_90[(df_90['duration'] < 90) & (df_90['genre'] == 'Action') ]
short_movie_count = len(short_movies)
print(short_movie_count)
```