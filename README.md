# Machine Learning with Video Games

<img src="Images/project_header.jpg" width="100%" align="cemter"/>

---

This project consisted of building a machine learning model to predict whether or not a video game would be considered a "hit."

The idea of a "hit" is defined by game's global sales and several other factors such as critic and user score.

The dataset chosen to tackle this project inluded the following features: 

Name, Platform, Year of Release, Genre, Publisher, NA Sales, EU Sales, JP Sales, Other Sales, Global Sales, Critic Score, Critic Count, User Score, User Count, Developer, and Rating

---

## Data Exploration

Exploration began by loading the data into a Tableau workbook. Once loaded, various graphs were made to determine relationships between each of the features available in the dataset.

--- 

## Preprocessing

Following exploration, the dataset was read into a Jupyter notebook to begin preprocessing.

The first step in preprocessing included removing any outliers within the data.

vg_data = vg_data.drop(vg_data[(vg_data['Critic_Score']>60) & (vg_data['Global_Sales']>60)].index)