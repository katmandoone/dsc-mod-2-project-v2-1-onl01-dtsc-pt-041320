# Mod 2 Project

By Carl Cook

## Introduction

In this project, we'll be looking at data provided in the King County Housing Database. Using the data provided, we'll use multiple linear regression to create a model for the expected price of a home based upon the features of that home.

We'll be using the OSEMiN workflow to take us step-by-step through this process.

## Obtain

This one is pretty easy, as the data has already been provided for us. We just need to load the .csv file into a DataFrame.
I also created a scatter matrix to see how each variable relates to price.

## Scrub

This is a little more involved. We'll check out our data, deal with null values, remove outliers, normalize, and one-hot encode our categorical variables.

## Explore

Here we'll really get into the meat of problem. We'll use Seaborn joint plots to determine linearity for each variable compared to price. The jointplots established linearity for the following variables: bedrooms, bathrooms, sqft_living, sqft_lot, floors, waterfront, grade, sqft_above, lat, and sqft_living15.

We'll then look at a heatmap to see how all these variable relate to one another.

## Model

Once we've gotten a good look at all the data, we'll use what we've observed to make a multiple linear regression model. This will give us coefficients for each variable, allowing us to combine all variables to come up with an estimated price for a home.

I ended up refining the model three times. The first just removes undesirable features with high p-values. The second uses the log transformation of the price, and the third uses the log transformation of all continuous numerical values.

## iNterpret

Once we've made our model, we have to give some thought to what it means. Which features are the most important?

Our final model ended up with an R-squared of 0.761, which is a little higher than our original model despite having fewer features. All multicollinearity issues have been addressed, and though the kurtosis is slightly higher than ideal at 4.448, it is much better than the original model's 8.055.

We did use the log function on our continuous numerical features and the target, so those coefficients will be in terms of percentages rather than true values. We did not apply the log function to 'floors' or 'grade,' so those coefficients will be in terms of absolute increase in feature to percent increase in price.

Unsurprisingly, homes built on the waterfront tend to be more valuable than those that are not. Since the target (price) has been log transformed, and waterfront variable has not, we must interpret the coefficient of 0.6681 as (np.exp(0.6681) - 1) * 100. This tells us that a house on the waterfront can be expected to have a price about 95% higher than a similar house that is not on the waterfront.

We apply that same logic to 'floors' and 'grade' to find that for each incremental increase in 'floors' the expected value of the home decreases by about 2.4%. An incremental increase in grade leads to an expected value increase of 11.8%

As for the continuous numerical variables, the square footage of the home shows the most effect, with a 1% increase in square footage adding an expected 0.4% increase in price. The variable 'sqft_living15' is the square footage of a homes 15 nearest neighbors, and a 1% increase shows an expected 0.25% increase in a home's price. Lastly, the square footage of a home's lot has a coefficient of 0.1117, meaning that a 1% increase in lot size amounts to an expected 0.11% increase in price. 

As for location, the Seattle and East Urban regions tend to have the highest positive influence on price. South Urban and South Rural homes tend to be the most negatively influenced.