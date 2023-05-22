# Spotify

![logo](https://github.com/umidmirzaev/spotify/blob/main/images/Spotify-Logo.png)

## Description

### Objective

The goal of the project is to build a data pipeline that extracts data about the most popular songs in Norway. We want to understand the current music trends in Norway, which albums are popular, and who are the artists behind these songs. We get this data from the "Top Songs - Norway" playlist on Spotify.

The data pipeline allows us to continuously collect updated data from Spotify's API since this playlist changes weekly, so we can always stay in the loop about what's new and popular in the Norwegian music scene. 

As a culmination of the project, we create a dashboard that gives us a clear view of music trends, popular albums, and leading artists in Norway.

### Dataset

The dataset comes from the weekly music chart called "Top Songs Norway", which we access through Spotify's Web API. The raw data is transformed into the datasets that include fields capturing the name and ID of the album, the name and ID of the song, the popularity index provided by Spotify, the duration of the song, and more.

More info can be found here: 
- Website: https://developer.spotify.com/documentation/web-api
- Playlist: https://open.spotify.com/playlist/37i9dQZEVXbJvfa0Yxg7E7

### Tools & Technologies

- Language - [Python](https://www.python.org/)
- Cloud - [Amazon Web Services](https://aws.amazon.com)
- Extraction & Transformation - [Jupyter Notebook](https://jupyter.org)
- Application and Infrastructure Monitoring - [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/)
- Serverless computing - [AWS Lambda](https://aws.amazon.com/lambda/)
- Storage - [Amazon S3](https://aws.amazon.com/s3/)
- Serverless Data Integration - [AWS Glue](https://aws.amazon.com/glue/)
- Serverless Query Service - [Amazon Athena](https://aws.amazon.com/athena/)
- Data visualization - [Amazon QuickSight](https://aws.amazon.com/quicksight/)

### Data Pipeline Architecture
![Architecture](https://github.com/umidmirzaev/spotify/blob/main/images/Spotify_Architecture.jpg)

### Final Result
![SpotifyDashboard](https://github.com/umidmirzaev/spotify/blob/main/images/Dashboard.png)

## Setup

### Prerequisites

- AWS Cloud account where you can start building with a free tier.
- Web API to retrieve metadata from Spotify content.

### Steps
1. **CloudWatch Alarm Setup (Optional)**: You can set up a CloudWatch alarm with a fixed threshold if you need to.

2. **Creating S3 Bucket and Folders**: Make a new bucket and folders on AWS S3.

3. **Lambda Functions**: We need two AWS Lambda functions:
  - `spotify_api_data_extract` is the first function. It pulls raw data from Spotify Web API and saves it into a folder for raw data. For this to work, the function needs the "AmazonS3FullAccess" permission. Besides, we need to add an additional layer to use an external module called `spotipy` to work with the Spotify API. 
  - `spotify_transformation_load_function` is the second function. It takes raw data from the raw data folder, processes it, and stores the processed data into a new folder in the same bucket. This function needs access to the entire Lambda environment. In this function, we need to add an additional layer of `pandas`.

4. **Setting Up Triggers**: Both Lambda functions need triggers:
  - The first function `spotify_api_data_extract` runs on a schedule, set up in CloudWatch Events. You can set it to run every day.
  - The second trigger is linked to our S3 bucket. It runs the second function `spotify_transformation_load_function` every time new data is added to the bucket.

5. **Creating a Glue Crawler**: Set up a Glue Crawler to read files in S3. It finds information like column names and data types. After running, the Crawler makes a table in AWS Glue. This table is used in AWS Athena for queries.

6. **Linking Athena and QuickSight**: Connect Athena with QuickSight for visualizing and analyzing the data we've stored in Athena.

## Potential next steps

- Build dimensional models
- Add more visualizations

