# Spotify
Spotify End-To-End Data Pipeline Project

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

- Language: Python, SQL
- Cloud - [Amazon Web Services](https://aws.amazon.com)
- Extraction & Transformation - [Jupyter Notebook](https://jupyter.org)
- Application and Infrastructure Monitoring - [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/)
- Serverless computing - [AWS Lambda](https://aws.amazon.com/lambda/)
- Storage - [Amazon S3](https://aws.amazon.com/s3/)
- Serverless Data Integration - [AWS Glue](https://aws.amazon.com/glue/)
- Serverless Query Service - [Amazon Athena](https://aws.amazon.com/athena/)
- Data visualization - [Amazon QuickSight](https://aws.amazon.com/quicksight/)

### Data Pipeline Architecture


### Final Result
![Dashboard]([image.jpg](https://github.com/umidmirzaev/spotify/blob/main/images/Dashboard.png))


https://github.com/umidmirzaev/spotify/blob/main/images/Dashboard.png
