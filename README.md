# Project: Data Wrangling and Analyzing

# Data Wrangling
The data wrangling involved the following processes:
> + Data Gathering
> + Data Assessing
> + Data Cleaning
> + Data Storing

## Data Gathering
+ load the necessary libraries
+ load the twitter-archive-enhanced.csv into a dataframe called twitter_archive
+ Use Requests library to download the tweet image_prediction.tsv file and load into a dataframe called image_prediction
+ Read the tweet_Json.txt file line by line into a dataframe named tweet_count

## Assessing Data
+ Visual assessment
+ Programmatic assessment

## Cleaning Data
The following data issues were noticed during the data assessing stage and were cleaned in this stage:

### Quality Issues
1. Information on retweeted  data is not needed, so drop these rows: retweeted_status_id, retweeted_status_user_id, retweeted_status_timestamp, and expanded_urls.

2. Information on reply  data is not needed, so drop these rows in_reply_to_status_id, in_reply_to_user_id

3. Columns on retweeted  data and reply data are not needed, so drop these columns: retweeted_status_id, retweeted_status_user_id, retweeted_status_timestamp, and expanded_urls, in_reply_to_status_id, in_reply_to_user_id

4. From **twitter_archive table**, tweet_id has dtype int64 and should be object and timestamp should be a datetime64 dtype.
   From **image_pred table,** The tweet_id column in image_pred table should be object datatype not int64.
   From **tweet_count_df**, change id_str dtype to "string".

5. **From twitter_archive table,** Many invalid names such as: 'a', 'such' and 'an' might be parts of strings that got taken out of context.

6. **twitter_archive table**, Some rating_numerator were not properly extracted because rating_numerator cannot be less than 10 

7. Rating_denominator should be equal to 10 in **twitter_archive table.**

8. Many columns from the **twitter_archive table** have 'None' instead of NaN to represent null values.

9. Duplicated rows in **image_prediction.**

### Tidiness Issues
1. Dog type are in different columns, it should be merged together in a single column.

2. All three tables should be be merged into one for easy accessibility of the datasets.

## Data Storing

# Analyzing and Visualizing Data
## Insights
+ The maximum rating_numerator is an outlier and 90% of the rating_numerator are <= 13.
+ Also, @WeRateDogs almost always rate dogs more than 10 and only about 20% of the dataset do not fall into this category. And there is just one instance of a rating_numerator of 0.
+ The highest rating_denomiantor is 170 and lowest is 2.0. @WeRateDogs almost always rates dog with a rating_denominator of 10 as 99% of the values are 10.
+ The favourite_count of the dataset ranges from 81 to 132810.
+ The favourite_count column of the dataset ranges from 16 to 79515.
+ The commonest dog name is Walter and it is twice the frequency of the 2nd commonest name (Penny).
+ 1194 times (60.6%) the neural image prediction recognized the images uploaded as dogs and 305 times (15.5%) the algorithm didnt predict the images as dogs.
+ The commonest predicted dog breed is the **golden_retriever followed by the Labrado_retriever**
+ The maximum number of image uplaoded was 4, although majority of the rated pictures were the first pictures 

## Data Visualization
+ There is a linear relationship between Rating_numerator and number of Favourite_count gotten by a dog.
+ A barchart showing the frequency of the 20 most frequently posted dogs on the twitter pagefication uncovered that the top 3 dogs recognized by the neural image prediction were Golden retriever, Labrador_retriever and Pembroke respectively.


# Credits
This project was done as a partial fulfilment of the requirements for the Udacity Data Analytics Nanodegree certification.
