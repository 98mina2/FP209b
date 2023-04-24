# FP209b

Final Project for AC209B

## Data Acquisition

Download the JSON data from this website:

https://www.yelp.com/dataset

After that, to make subsequent reading and writing faster, we will convert all `json` files to `feather` format. Run notebook `convert_data_format.ipynb` to achieve this.

## Perliminary Data Cleaning

Here is the order the run our data cleaning notebooks as they do form dependencies. Note that some of the cleaned results are too large, so we did not upload them to our git repo.

- `business_data_inspect.ipynb`
  - Filtered out non-restaurant businesses
  - Cleaned data is saved as `data/yelp_business_cleaned.feather`
- `review_data_inspect.ipynb`
  - Filtered reviews to match what we have for our previously filtered business data
  - Cleaned data is saved as `data/yelp_review_cleaned.feather`
- `user_data_inspect.ipynb`
  - Filtered users to keep those wrote reviews for the previous step
  - Cleaned data is saved as `data/yelp_user_cleaned.feather`

## EDA

- `EDA_business.ipynb`
- `EDA_review.ipynb`

## Modeling

- `base_model.ipynb`
- `advanced_model.ipynb`

## Final Report

- `recommender_system_report.ipynb`
