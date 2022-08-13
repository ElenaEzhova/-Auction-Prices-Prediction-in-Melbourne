# Auction-Prices-Prediction-in-Melbourne

## **1.	Introduction**

Melbourne has consistently led Australia in terms of population growth (Melbourne Demographics. Wikipedia, 2021). Approximately 80% of transactions for the purchase and sale of residential properties in Melbourne are completed through public property auctions.

The auction method so commonly used in Australia for property sales differs from the private sale/treaty method used in many other jurisdictions. The chief differences between the two methods of sale are that in the private sale method the seller states an expected sale price. In an auction, while the seller may establish a reserve price known only to the seller and the auctioneer, no expectation of a selling price is tabled for potential buyers. While the auction method is more transparent for buyers it can result in higher prices than the private sale/treaty alternative. (Frino et al., 2010). Certainly the “real time” dynamic of the auction experience increases the competitive and emotional context of the sale.

## **2.	Analytical objectives**

In Melbourne there is a need for buyers and sellers to be knowledgeable about auction market pricing that includes emotional component. Sellers by auction need to strike the right reserve price to encourage bidders. Buyers need to take care not to overbid in the heat of the moment. The need for pricing information in the Australian based context is increased as most Australian buyers do not use agents, while sellers typically do. (Just Landed, 2021).

***This project attempts to predict the property auction sale prices, or in other words, people's willingness to pay a certain price for a particular property,*** based on data from auction property sales in 2016-2017. It makes use of several libraries in Python: pandas for data cleaning, analysis, and feature engineering, matplotlib and seaborn for data visualization, and scikit-learn and xgboost for machine learning. ***The goal is to train several different models (including linear, tree-based, and ensemble methods) to come up with the best model that can predict auction selling price within one standard deviation of the mean.***

## **3.	Overview of the Data**

The source dataset (21 columns and 13580 rows) is publicly available at: https://www.kaggle.com/dansbecker/melbourne-housing-snapshot?select=melb_data.csv.

The final dataset used for training the models contains **23** columns and 10147 rows:

**Rooms**: Number of rooms

**Price**: Price in dollars

Method: **S** - property sold; **SP** - property sold prior; **SA** - sold after auction

Type: **h** - house, cottage, villa, semi, terrace; **u** - unit, duplex; **t** - townhouse

**Distance**: Distance from city business centre (km)

Regionname: General Region of the city (**8 regions**)

**Propertycount**: Number of properties that exist in the suburb

**Bathroom**: Number of Bathrooms

**Car**: Number of car spots

**Landsize**: Land Size

**BuildingArea**: Building Size

**BuildAge**: Property age in 2022.

## **4.	Assumptions**

1.	The price has a linear dependence on the number of rooms and bathrooms.
2.	The region and distance to the business center influence the price.
3.	The Type of the property influences the Price.
4.	The season influences the price.

## **5.	Methodology**

1. Explored summary statistics and checked for missing and null values.
2. Explored linear correlation between each of the continuous variables and the price and checked for collinearity.
3. Explored the relationships between price and categorical variables.
4. Prepared the final dataset:
 -	dropped unused columns,
 -	replaced missing/null values depending on the type of property, localization, or local features of the property,
 -	created a new variable 'BuildAge' that indicates the property age in 2022,
 -	removed duplicates, price outliers and methods that are not a complete selling,
 -	converted categorical variables into dummy/indicator variables.
5. Trained 11 models (linear, regression and ensemble methods) to find which ML model worked best for this dataset, and tuned parameters for this model. Performance measure: 1) R2 (pronounced "R squared") evaluates the fit of the model, with 1.0 being a perfect fit; 2) Root Mean Squared Error (RMSE) well below that $423,000 - standard deviation of the mean auction sales price. 

## **6. Results**

The XGBoost Regressor performed the best on the dataset.

![image](https://user-images.githubusercontent.com/95148782/184517039-1610e668-ec97-4054-85b8-997bf49079a3.png)


R2=0.82
RMSE=184750

![image](https://user-images.githubusercontent.com/95148782/184517045-e54d8b59-ed84-43a9-9b45-16689ba1ac1f.png)

## **7. Conclusion**

Future work could tune this model further by adding new features. For example, we could add swimming pools, school district scores, crime count, floodplain, and average property tax by location as these can affect how willing people are to bid on a particular property. 

Given the auction price is a result of "voting", it is sensitive to unpredictable circumstances. Therefore, the model should be updated every quarter to keep it as accurate as possible while giving it time to accumulate new data, especially in our times of economic uncertainty.


