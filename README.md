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

Once outliers were removed, the data was checked to determine the ratio of null values within each column. To reduce the number of null values, the data as whole itself was reduced to reflect only prominent video game platforms as there were far too many platforms prior that could be considered noise.

The data was then checked again to determine the ratio of null values within each column. The ratio of null values within several key variables was assessed once more by replacing null values with either median or mode values. 

Once null values were taken care of, it was time to drop unecessary columns. These columns included: Name, Publisher, Developer, NA_Sales, EU_Sales, JP_Sales, Other_Sales, and Year_of_Release.

With an almost clean dataset, the next step was to define what would be considered a "hit" video game. This was done using a function that defined a video game as a "hit" if the game's global sales were equal to or above 10 million sales. The function then returned either a "1" or a "0" if the game was a "hit" ot not, respectively.

---

## Building the Models

With a clean dataset and a video game "hit" defined, it was time to start building our models.

This proces began by defining X and Y values and splitting these into training and testng data. The shape of both the train and test data was checked to be sure they aligned. Once the data was split, we began training our first model.

### Logisitic Regression Model

The first step in our logisitic regression model was to import the LogisticRegression model from sklearn and train the data. This was originally performed on the unscaled data, which returned a training score of 0.9918 and a testing score of 0.9918. These scores were erroneously high, leading us to believe the model was overfitting. 

Our next step to account for overfitiing involved scaling the data. This was done by importing StandardScaler from sklearn and scaling the data to give us both X_train_scaled and X_test_scaled values. The model was then ran once more resulting in very slightly lower training and testing scores of 0.9926 and 0.9942, respectively. 

### Random Forest Classifier Model

Because our logisitic regression model seemed to be overfitting, we decided to use a random forest classifier model next. The first step in our random forest classifier model was to imort the RandomForestClassifier from sklearn and train the data. This was also, originally performed on the unscaled data, which returned a training score of 1.0 and a testing score 0.9942. These scores were also erroneously high, leading us to believe once again the model was overfitting. 

Our next step, to once again, account for overfitting involved sclaing the data. This was done by importing StandardScaler from sklearn and scaling the data to give us both X_train_scaled and X_test_scaled values. The model was then ran once more resulting in training and testing scores of 1.0 and 0.9942 respectively. 

## Refining

After reviewing both models, and observing each significantly overfitting, we decided to refine our approach in hopes of improving each model's training and testing scores.

Our first step in refining involved removing additional unecessary features. These additional features included Crtitic_Count and User_Count. These were removed as their mean values were much larger than the rest of the features in the dataset. The models were both ran again resulting in lower but similar overfitting training and testing values.

Our second step in refining included normalizing the data. This was done by importing Normalizer from sklearn and transforming the X values. Once normalized, both models were ran again resulting in, again lower but similar overfitting training and testing values...

## Considerations

While we could not achieve meaningful predicitive power with either model, we did step away with significant considerations. 

The first being that perhaps a feature other than global sales may have produced better predictive power. Features such as Critic Score or User Score, that can have a fairly large effect on whether a game is bought or played, and thus considered a "hit."

The second consideration was that perhaps a third different model would have performed better. A neural net machine learning model may have been the approach to instead take. We were under the assumption a simpler model would outperform, however a multilayer network may have better classified and predicted a game as a "hit."

Overall, the process of finding and preparing a dataset to build each machine learning model was quite the endeavor!