### Bird-Population-Regression-Analysis ###
Linear regression analysis of bird population data.
Uses _"Occurance and Climate Data of Birds in Asia"_ Dataset by Prathamesh Patil 2025.
Dataset available at: https://www.kaggle.com/datasets/prathameshpatil2025/occurance-and-climate-data-of-birds-in-asia

--------------------------------------------------------------------------------------------

## Running the Code ##

_Step 1: Import Libraries_
* Ensure the folowing libraries have been imported without issue. 
  * import pandas as pd
  * import numpy as np
  * import matplotlib.pyplot as plt
  * from sklearn.model_selection import train_test_split
  * from sklearn.linear_model import LinearRegression
  * from sklearn.metrics import mean_squared_error, r2_score

_Step 2: Load the Dataset_
* The "Occurance_and_climatedata_of_birds.csv" dataset is available at https://www.kaggle.com/datasets/prathameshpatil2025/occurance-and-climate-data-of-birds-in-asia
* The dataset is by Prathamesh Patil and last updated in 2024.
* It contains the follwing information (avaiable on Kaggle):
  * Bird_Species: The scientific or common name of the bird species observed.
  * Year: The year of the observation (ranging from 1980 to 2010).
  * Country: The Asian country where the observation was recorded.
  * Latitude: The geographic latitude of the observation point.
  * Longitude: The geographic longitude of the observation point.
  * Temperature: The average temperature (in Celsius) for the region during the observation period.
  * Precipitation: The total precipitation (in mm) for the region during the observation period.
  * Shift_km: A calculated value representing the potential geographic shift in the species' core habitat range in kilometers, possibly due to climate change.
  * Population: The observed population count for that species at that location and time.
  * Traffic: An index or count representing local traffic, likely serving as a proxy for human activity and urbanisation levels.

_Step 3: Clean the Data_
* Drop the 'Shift_km' column: It is uncertain if this variable has been calculated based on the other variables in the dataset. Therefore it is dropped to avoid multicollinearity.
* Drop rows with missing values: Optional step to clean up data.

_Step 4: Run Linear regression_
* Standard linear regression using 80/20 train/test split.
* After evaluating the model performance notice the R² and RMSE values indicate a poorly fitting model. The next step tries using a log transformation on the population to better meet the assumptions of the model.

_Step 5: Log transform the population and re-run the regresion_
* Log transform the population and re-run the regression using the same 80/20 train/test split.
* After evaluating the model performance notice the R² and RMSE values have improved but the model is still weak. The bird species column includes a range of species which could be affecting the result.
* Proceed with the log transformed population but attempt single species analysis next.

_Step 6: Run analysis of single species with log transformed population_
* In the code the Bar-headed Goose has been used as the specific species to test the regression. However, any of the species with high member counts may be suitable.
* The R² and RMSE values still indicate that the population size is not well explained by the predictors- nay linear relationships are extremely weak or absent.
* Inspecting the coefficients shows small or negligible effects.
* The plot of observed vs predicted counts illustrates that the model is not a good fit.

-----------------------------------------------------------------------------------------------

## Conclusions ##

* The linear regression remains an unsuitable model even after log transfomation of the population AND after focusing on population at a individual species level.
* A GLM OR GAM maybe a better fit- these are more commonly used with ecological data as they are better suited to population count data, and avoid issues with log transformations.
* Additionally, the poor model fit is likely driven by confounding factors within the dataset, including species rarity, differing ecological niches, and geographic variation in conservation context.
