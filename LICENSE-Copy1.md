# Mod 2 Project

By Carl Cook

## Introduction

In this project, we'll be looking at data provided in the King County Housing Database. Using the data provided, we'll use multiple linear regression to create a model for the expected price of a home based upon the features of that home.

We'll be using the OSEMiN workflow to take us step-by-step through this process.

## Obtain

This one is pretty easy, as the data has already been provided for us. We just need to load the .csv file into a DataFrame.

## Scrub

This is a little more involved. We'll check out our data, deal with null values, remove outliers, normalize, and one-hot encode our categorical variables.

## Explore

Here we'll really get into the meat of problem. We'll use Seaborn joint plots to determine linearity for each variable compared to price. We'll then look at a heatmap to see how all these variable relate to one another.

## Model

Once we've gotten a good look at all the data, we'll use what we've observed to make a multiple linear regression model. This will give us coefficients for each variable, allowing us to combine all variables to come up with an estimated price for a home.

## iNterpret

Once we've made our model, we have to give some thought to what it means. Which features are the most important?