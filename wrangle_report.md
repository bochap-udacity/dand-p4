# Wrangle and Analyze Data Report

> Author: Darren Seet

This project performs the Data Wrangling required to clean the data for performing the analysis. It is done in the following steps:

- [Gather](#Gather)
- [Access](#Access)
- [Clean](#Clean)

## Gather

In this step, the operations to obtain the data for analyzing is carried out. There are 3 data sources and the following are the methods used to obtained them.

1. twitter archive enhanced: This was provided in the Udacity site as a download that is manually downloaded via the browser

2. tweet image predictions: This is hosted on a location that is accessible publicly on the web. The python requests package is used to access the file and saved on a location accessible to the notebook

3. twitter archive details: This data is obtained from the Twitter API. The ids are obtained from the twitter archive enhanced datasource and used to query the API to obtain the result as a JSON object for each tweet. The JSON object is stored as a line in a flat text file.

## Access

In this step, the datasources obtained in the Gather step is analyzed to observe to find any Dirty or Messy data for cleaning.

- Dirty data, also known as low quality data. Low quality data has content issues.
- Messy data, also known as untidy data. Untidy data has structural issues. - Data that belong

To find these data, we made visually or access via code. The visual method is performed by opening the flat file in Excel using the data filtering features to look into the data. The second method uses Python and Pandas code and the following is some of the commands that provides insight to the data.

1. DataFrame.info - Provides visibility to the data that checks for null values across columns and also counts by columns. Shows the schema of the dataframe that allows possible identification of Untidy data.

2. DataFrame.describe - Provides visibility to outliers in the data source

3. DataFrame.duplicate - Allows the identification of duplicates in the data source

4. DataFrame.query - Allows the querying of values in the DataFrame to observe the data for issues

5. Series.str.len - Allows the querying of data by the length of the value to find short values that might be wrong

6. Series.value_counts - Allows a count of data in a series to find possible duplicates

7. Series.isnull - Allows the querying of null data 

## Clean

In this step, the issues identified in the Access step is clean via code. Firstly the source dataframes are duplicated using the copy command to make sure the original source data is available while cleaning if required.

### twitter archive enhanced

1. `expanded_urls` - cleaned by removing None and split into a new DataFrame of expanded_url by tweet_id

2. `timestamp` - converted to a date time type using `to_datetime`

3. `rating_denominator` - set to 10 for all records to match the rating rules

4. `in_reply_to_status_id` - all records with non null value is removed from the dataframe. Twitter API documentation indicates that a non null value represents a reply `Nullable. If the represented Tweet is a reply, this field will contain the integer representation of the original Tweet’s ID.`

5. `retweeted_status_id` - all records with non null value is removed from the dataframe. Twitter API documentation indicates that a non null value represents a retweet. `Users can amplify the broadcast of Tweets authored by other users by retweeting . Retweets can be distinguished from typical Tweets by the existence of a retweeted_status attribute. This attribute contains a representation of the original Tweet that was retweeted. Note that retweets of retweets do not show representations of the intermediary retweet, but only the original Tweet. (Users can also unretweet a retweet they created by deleting their retweet.)`

6. expanded_urls (expanded_url) - Removed all entires that do not start with `https://twitter.com/dog_rates/` since that represents tweets not related to dog_rates.

7. source - clean the column to remove the HTML markup

8. All columns not used like name, doggo, floofer, pupper, puppo is dropped from the source

### twitter archive details

1. `id` - Used `rename` to change the name to `tweet_id` to match other datasources

### twitter analysis

This is the new dataframe that is created by joining `twitter archive enhanced`, `tweet image predictions` and `twitter archive details`. The final result is persisted as a flat file (csv) named `twitter_analysis_source.csv`.

The schema of the data source is

```pandas
 #   Column              Non-Null Count  Dtype
---  ------              --------------  -----
 0   tweet_id            1971 non-null   int64
 1   timestamp           1971 non-null   datetime64[ns, UTC]
 2   source_enhanced     1971 non-null   object
 3   text                1971 non-null   object
 4   rating_numerator    1971 non-null   int64
 5   rating_denominator  1971 non-null   int64
 6   img_num             1971 non-null   int64
 7   p1                  1971 non-null   object
 8   p1_conf             1971 non-null   float64
 9   p1_dog              1971 non-null   bool
 10  p2                  1971 non-null   object
 11  p2_conf             1971 non-null   float64
 12  p2_dog              1971 non-null   bool
 13  p3                  1971 non-null   object
 14  p3_conf             1971 non-null   float64
 15  p3_dog              1971 non-null   bool
 16  created_at          1964 non-null   datetime64[ns, UTC]
 17  full_text           1964 non-null   object
 18  retweet_count       1964 non-null   Int64
 19  favorite_count      1964 non-null   Int64
```
