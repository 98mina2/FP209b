# Restaurant Recommender System

## Introduction

For the past few decades, with the fast growing market of digital platforms, 
firms have tried to customize the advertising of their products based on individual customers' preferences or interests. 
This practice has been utilized across various industries and companies, from the e-commerce site Amazon suggesting relevant products to the streaming platform Netflix recommending similar shows to their users' view history and profile. The recommendation systems help increase sales as the users are able to easily see and purchase recommended products that match their needs and preferences.

In this project, we focus on devising a restaurant recommendation system (hereby referred to as “recommender”).
We use data of restaurants, customer profiles, and their reviews from [Yelp](https://www.yelp.com/dataset/documentation/main), a platform for crowd-sourced reviews about businesses.
As an individual has unique restaurant preferences, such as cuisines, ambience, pets, diet types, and/or parking availability, we build a recommender to recommend restaurants to users based on the insights gleaned from their reviews on the previous restaurants they have been to.

## Data Preprocessing

The data is downloaded from [Yelp official website](https://www.yelp.com/dataset/documentation/main). There are three datasets relevant to our analysis and models: `business`, `review`, and `user` data. The `business` dataset contains information about the businesses including name, location, hours, average rating stars, hours, number of reviews, and other features such as cuisine types and parking availability. The `user` data include the user's friend mapping and all the metadata associated with the user such as number of upvotes. The `review` dataset records full review text data as well as the `user_id` who wrote the review and the `business_id` for which the review was written. There are 150,346 businesses and 6,990,280 reviews in the Yelp original datasets.

We converted the original datasets which are in JSON format to `.feather` filetype to reduce storage space and optimize faster reading. The documentation of data cleaning process can be found in `recommender_system_report.ipynb`

Note that there are dependencies among the data cleaning Jupyter notebooks. The order of the run should be as follows:

- **Business data**: `data cleaning/business_data_inspect.ipynb`
  - Filtered out non-restaurant businesses and extracted attribute features of each restaurant. 
  - Output in `data/yelp_business_cleaned.feather`.
- **Review data**:`data cleaning/review_data_inspect.ipynb`
  - Filtered the review data in accordance with the business dataset by filtering out reviews for irrelevant businesses (using `business_id`), reducing the dataset size from 6,990,280 to 5,257,329 entries.
  - Additionally, standard scaling is applied to the numeric features.
  - Output in `data/yelp_review_cleaned.feather`.
- **User/customer data**: `data cleaning/user_data_inspect.ipynb`
  - Filtered users to keep those wrote reviews for the previous step.
  - Engineer certain features such as `elite`, `friends`, and `yelping_since`.
  - Output in `data/yelp_user_cleaned.feather`

## Model

- **Baseline model**: `models/base_model.ipynb`
- **NCF model**: `models/advanced_model.ipynb`
- **NCF model with extended features**: `models/final_model.ipynb`
