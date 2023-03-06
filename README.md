# Stellar_Classification
Dataset Source: https://www.kaggle.com/fedesoriano/stellar-classification-dataset-sdss17

## Final Project Overview

We chose to select a stellar classification dataset that was compiled from the Sloan Digital Sky Survey which analyzed over 100,000 interstellar phenomena as either a star, galaxy, or quasar. The survey provided us with a wide array of observation data that included the object's alpha (right ascension angle), delta (declination angle), ultraviolet filter, green filter, red filter, infared filter, near infared filter, redshift, plate, the date the object was identified, and a variety of identification numbers relating to how the data was collected. In our analysis, we removed the object's identifiers (i.e. Object ID, Run ID, etc.) from the machine learning model because they had no impact on classifying what would the object would be.

### Column identifiers and meanings
![image](https://user-images.githubusercontent.com/92773195/156466962-665f5b20-747f-4f2d-9bc1-bc2f01782e4f.png)

Figure 1. Column identifications and their definitions.

The group was highly interested in the topic of astronomy, and learning which features of an astronomical object were most important in classifying it as a star, galaxy, or quasar was highly interesting to all group members which is why we picked this comprehensive and detailed dataset. 

In this project we hope to learn how accurate our models are at predicting future objects with the same kind of data provided as stars, galaxies, or quasars. Additionally, our goal is to understand which variables are most important in determining/classifying objects in those three groups. 

## Analysis
We created multiple types of machine learning models in pandas that included random forest classification, neural networks, and K-means clustering to determine the most accurate model at classifying which stellar objects. Multiple iterations of each model were created to verify the consistancy of the machine learning model type.

Random forest classification proved to be the most accurate modeling type with an average accuracy of 97.8% and a standard deviation of 0.03%. 

![Random Forest Accuracy Values](https://user-images.githubusercontent.com/91921522/160036675-61aa4ad1-fdbb-4144-950e-441b7e378211.png)

Figure 2. Accuracy values for 10 random forest models.

K-Means was found to be a less accurate machine learning model type for this classification with an average accuracy of 70.4% and a standard deviation of 17.45%.

![K-Means Accuracy Values](https://user-images.githubusercontent.com/91921522/160036772-d9bf58dd-e9e6-496b-8e1d-544833b4ff8d.png)

Figure 3. Accuracy values for 10 K-means models.

Neural Networks were found to be more accurate than the K-Means, but less accurate than the random forest models, with an average accuracy of 80.0% and a standard deviation of 1.3%. 8 input features were used for all cases, the first layer had 25 nodes for the first two models, 50 for the following two, then 75 for the following two, 100 for the following two, and 150 for the last two. The second layer used 5 nodes and 9 nodes alternating.

![Neural Network Accuracy Values](https://user-images.githubusercontent.com/91921522/160721547-4e802c37-3835-4ad1-bb61-33681e80e50d.png)

Figure 4. Accuracy values for 10 neural network models.

We also wanted to determine which features were the most important in determining the object's classification. Redshift was the most important feature in determining whether the object would be a star, quasar, or galaxy with a weight of 0.61. Since redshift was so heavily weighted in determining the object's classification, we also attempted an additional random forest models with the redshift removed to better determine the impact of the redshift on the average model accuracy. The random forest models had an average accuracy of 87.6% and a standard deviation of 0.04%.

![Random Forest without Redshift Accuracy Values](https://user-images.githubusercontent.com/91921522/160040222-bfbfd04c-7676-43d0-8b22-0ce04c91f719.png)

Figure 5. Accuracy values for 10 random forest models with redshift data omitted.

DECISION: Based on all the models, we felt the random forest classification model was the best option for us to use in our dataset due to its highly accurate nature of 98.0%. This is a great model for datasets using numerical and categorical data (like our own), and although random forests can be a little hard to interpret, we felt that we could not ignore such a highly accurate model for future use. 

TRAINING: We split the data in our machine learning models using the train_test_split method in the sklearn library in Jupyter Notebooks. The data was taken from the aforementioned Sloan Digital Sky Survey data and additional training of the data could be used from other stellar cartography datasets containing the same or similar information, only from different stellar objects in our universe. 

A SQL database was also created with multiple tables to store our stellar classification data and linked to our Jupyter Notebook file. Jupyter Notebook was also used to show the locations the stellar objects in a 3D plot.

## Dashboard
For our dashboard, we used Tableau to create our visualizations. To start, we wanted to display the counts of galaxies, stars, and quasars contained in the dataset using a barchart. There are roughly 60k galaxies, 20k stars, and 20k quasars in the Sloan Digital Sky Survey dataset. 

Following that, and due to the nature of redshift being the most important feature in stellar classifcation, we decided to visualize the average redshift by stars, quasars, and galaxies. Quasars produced by the far the highest amount of redshift (approx. 1.7), galaxies (approx. 0.42), and stars had essentially 0 redshift. 

Finally, we wanted to visualize the filters used to observe the objects based on the type of light they emit and if we could spot any tendencies from there. We also used a floating filter that created an interactive element of the visualization for users to toggle between the galaxies, stars, and quasars. 

https://public.tableau.com/app/profile/john.molenda/viz/StellarClassification/StellarDashboard


In the second dashboard, we again used Tableau to graph the redshift (Y-axis) and alpha angles (x-axis) of the stellar bodies. The following visual is displayed in a scatter plot with the points being color coded based on the absolute magnatude in the infrared (z) wavelength spectrum.

This analysis shows the distribution of the redshift amoung stellar bodies in relation to earths location and showed unusual gaps in space. Furthermore the absolute magnitude in the infrared (z) spectrum showed an interesting correlation between the redshift and absolute magitude.

https://public.tableau.com/app/profile/edward.goldhill/viz/RedshiftvsAlpha/Dashboard1?publish=yes

Google Slides: https://docs.google.com/presentation/d/1oDV5cDXPCrpJuMypeMD07zXWSuc-ywPKzj5fVKoqTpM/edit?usp=sharing

Presentation Notes: https://docs.google.com/document/d/1D5F6Dd88zmH1SOzo6yHuQClS8AL4-0Prpe79HR2Vvfs/edit
