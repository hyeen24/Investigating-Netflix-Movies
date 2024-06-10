# Introduction
This Project can be found in DataCamp

Aim : 
Apply the foundational Python skills you learned in Introduction to Python and Intermediate Python by manipulating and visualizing movie data.

# Investigating Netflix Movies

Netflix! What started in 1997 as a DVD rental service has since exploded into one of the largest entertainment and media companies.

Given the large number of movies and series available on the platform, it is a perfect opportunity to flex your exploratory data analysis skills and dive into the entertainment industry. Our friend has also been brushing up on their Python skills and has taken a first crack at a CSV file containing Netflix data. They believe that the average duration of movies has been declining. Using your friends initial research, you'll delve into the Netflix data to see if you can determine whether movie lengths are actually getting shorter and explain some of the contributing factors, if any.

You have been supplied with the dataset netflix_data.csv , along with the following table detailing the column names and descriptions. This data does contain null values and some outliers, but handling these is out of scope for the project.

# The data
netflix_data.csv
| Column |	Description
| --- | --- |
| show_id | The ID of the show
| type | Type of show
| title | 	Title of the show
| director | 	Director of the show
| cast | Cast of the show
| country | Country of origin
| date_added | Date added to Netflix
| release_year | Year of Netflix release
| duration | Duration of the show in minutes
| description | Description of the show
| genre |	Show genre

# Instruction
Perform exploratory data analysis on the netflix_data.csv data to understand more about movies from the 1990s decade.
1. Filter the data for movies released in the 1990s
2. Find the most frequent movie duration
3. Count the number of short action movies from the 1990s ( less than 90 mins )

# The code
```python
# Importing pandas and matplotlib
import pandas as pd
import matplotlib.pyplot as plt

# Read in the Netflix CSV as a DataFrame
netflix_df = pd.read_csv("netflix_data.csv")

# Subset the DataFrame for type "Movie"
netflix_subset = netflix_df[netflix_df["type"] == "Movie"]

# Filter the to keep only movies released in the 1990s
# Start by filtering out movies that were released before 1990
subset = netflix_subset[(netflix_subset["release_year"] >= 1990)]

# And then do the same to filter out movies released on or after 2000
movies_1990s = subset[(subset["release_year"] < 2000)]

# Visualize the duration column of your filtered data to see the distribution of movie durations
# See which bar is the highest and save the duration value, this doesn't need to be exact!
plt.hist(movies_1990s["duration"])
plt.title('Distribution of Movie Durations in the 1990s')
plt.xlabel('Duration (minutes)')
plt.ylabel('Number of Movies')
plt.show()

duration = 100

# Filter the data again to keep only the Action movies
action_movies_1990s = movies_1990s[movies_1990s["genre"] == "Action"]

# Use a for loop and a counter to count how many short action movies there were in the 1990s

# Start the counter
short_movie_count = 0

# Iterate over the labels and rows of the DataFrame and check if the duration is less than 90, if it is, add 1 to the counter, if it isn't, the counter should remain the same
for label, row in action_movies_1990s.iterrows() :
    if row["duration"] < 90 :
        short_movie_count = short_movie_count + 1
    else:
        short_movie_count = short_movie_count

print(short_movie_count)

# A quicker way of counting values in a column is to use .sum() on the desired column
# (action_movies_1990s["duration"] < 90).sum()
```


![download](https://github.com/hyeen24/Investigating-Netflix-Movies/assets/81229303/fd56dc42-bb7f-473d-af14-cfa5284d14e3)

