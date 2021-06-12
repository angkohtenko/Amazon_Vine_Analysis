# Amazon_Vine_Analysis
## Overview of the analysis
The goal of the analysis was to determine if there is any bias towards reviews that were written as part of the Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products.

To complete the analysis I’ve used PySpark and PgAdmin hosted on AWS.

First of all, I’ve extracted the dataset from [S3](https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt) related to products under [baby category]( https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Baby_v1_00.tsv.gz).

![](https://github.com/angkohtenko/Amazon_Vine_Analysis/blob/main/images/amazon_reviews_dataset.png)

I’ve split dataset to 4 tables: customers, products, reviews and vine. Then, I’ve connected to an AWS RDS instance and loaded the transformed data into pgAdmin.

![](https://github.com/angkohtenko/Amazon_Vine_Analysis/blob/main/images/connect_to_RDS.png)

To perform further analysis, I’ve used Pandas. I analysed vine table with review id, start rating, votes for the review and its helpfulness, vine/non-vine participant. Analysis is based on reviews that have 20 votes of more and at least half of them are marked as helpful.

## Results
I’ve filtered data to meet analysis requirements and created summary dataframe:

![](https://github.com/angkohtenko/Amazon_Vine_Analysis/blob/main/images/summary.png)

There are only 463 reviews within Vine program and 25,094 reviews from non-Vine customers.

202 Vine program reviews have five stars rating. It is equal to 43.63% of all reviews written by Vine program participants.

On the other hand, there are 12,033 five stars rating. That’s 47.95% of all non-Vine reviews.

## Summary
Based on the numbers in the summary table, I can admit that there is no any positivity bias for reviews in the Vine program. The non-vine customers tend to leave even more reviews with high rating.
To expand the analysis, I’ve created similar summary table but for every rating option.

![](https://github.com/angkohtenko/Amazon_Vine_Analysis/blob/main/images/total_summary.png)

According to the results, non-vine customers more often rate a product with only 1 star. So, I assume that non-vine customers tend to think in only two categories: like / dislike or 5 stars / 1 star, while vine customers try to evaluate a product fairly. They often leave 3 or 4 stars reviews.


