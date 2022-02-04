# Machine Learning with Video Games

<img src="Images/project_header.jpg" width="100%" align="cemter"/>

---

This project consisted of building a machine learning model to predict whether or not a video game would be considered a "hit."

The idea of a "hit" is defined by a game's global sales and several other factors such as critic and user score.

The dataset chosen to tackle this project inluded the following features: 

Name, Platform, Year of Release, Genre, Publisher, NA Sales, EU Sales, JP Sales, Other Sales, Global Sales, Critic Score, Critic Count, User Score, User Count, Developer, and Rating

---

## Data Exploration

Exploration began by loading the data into a Tableau workbook. Once loaded, various graphs were made to determine relationships between each of the features available in the dataset.

--- 

## Preprocessing

Following exploration, the dataset was read into a Jupyter notebook to begin preprocessing.

The first step in preprocessing included removing any outliers within the data using the following:

vg_data = vg_data.drop(vg_data[(vg_data['Critic_Score']>60) & (vg_data['Global_Sales']>60)].index)

Once outliers were removed, the data was checked to determine the ratio of null values within each column. To reduce the number of null values, the data was reduced to reflect only prominent video game platforms as there were too many prior that could be considered noise.

The data was then checked again to determine the ratio of null values within each column. The ratio of null values within several key variables was assessed once more by replacing null values with either median or mode values. 

Once null values were taken care of, it was time to drop unecessary columns. These columns included: Platform, Genre, and Rating.

With an almost clean dataset, the next step was to define what would be considered a "hit" video game. This was done using a function that defined a video game as a "hit" if the game's global sales were equal to or above 10 million sales. The function then returned either a "1" or a "0" if the game was a "hit" ot not, respectively.

---

## Building the Models

With a clean dataset and a video game "hit" defined, it was time to start building our models.