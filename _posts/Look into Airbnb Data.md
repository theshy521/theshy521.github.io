---
layout: post
title: Look into Airbnb data with Seattle and Boston.
---

# Introduction
Airbnb is an online marketplace that connects people looking to rent out their homes or accommodations to travelers looking for lodging. It allows individuals to list their properties and for travelers to book those properties for short-term stays.
![Airbnb](/images/airbnb.jpeg)
Therefore, I used data from Kaggle's Airbnb Seattle and Boston data.
1. Seattle
Since 2008, guests and hosts have used Airbnb to travel in a more unique, personalized way. As part of the Airbnb Inside initiative, this dataset describes the listing activity of homestays in Seattle, WA.
2. Boston
Since 2008, guests and hosts have used Airbnb to travel in a more unique, personalized way. As part of the Airbnb Inside initiative, this dataset describes the listing activity of homestays in Boston, MA.

Based on above Airbnb data, I will look into below 3 questions including:
1. Analyze property_type for seattle and boston
2. Analyze probalibity distribution of Price
3. Analyze correlation between numerical columuns and price. And customed AI model to predict price.


# Part 1: Analyze property_type for seattle and boston
what kind of property are most popular for travel people?

![Property Type](/images/Analyze property type.PNG)

The data here are aggregated that appartment and house are most popular for travel people.


# Part 2: Analyze probalibity distribution of Price
What kind of distribution of Price both Seattle and Boston.

![Price distribution](/images/Probability distribution of price.PNG)

Here you can see that price distribution is focus on less than $500.



# Part 3: Analyze correlation between numerical columuns and price. And train customed AI model to predict price.
Is there any correlation between numerical columns and price?
![Correlation](/images/Correlation.PNG)


What is most important feature for price?
![Feature importance](/images/Feature importance.PNG)

After training a customized AI model with sample data, refer above screenshot that "Bedroom" is most important feature of price.
