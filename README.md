# Spotify ETL End-To-End Pipeline Project

### Outline

Welcome to this project! It’s an ETL pipeline that pulls music data from Spotify, transforms it, and sends it to AWS — making it easy to explore and analyze your favorite tunes.
 
 ### Architecture
![Architecture Diagram](https://github.com/ameetsinghmanyal/spotify-etl-aws-data-pipeline-project/blob/main/Architecture.jpeg)
 
 ### About Spotify API
 The [Spotify API](https://developer.spotify.com/documentation/) opens the door to Spotify’s vast music universe. It lets developers build powerful apps that can search songs, explore artists, manage playlists, and dive into rich metadata about tracks, albums, and more — all while connecting directly with the world’s leading music streaming platform..
 
 In this project we have used the [**Top 100 - Aura Playlist**](https://open.spotify.com/playlist/6VOedaf3eNWDOVpa9Qdlvg) Playlist as our data    
 
 

### 🔧 Tools & Services Used in This Project
🎵 Amazon S3
A reliable, scalable cloud storage service used to store all our Spotify data — songs, playlists, metadata, you name it. Access it from anywhere, anytime.
Learn more → (https://docs.aws.amazon.com/s3/index.html)

👁️‍🗨️ Amazon CloudWatch
The eyes and ears of our pipeline. Tracks metrics, monitors logs, and keeps everything in check with smart alerts.
Learn more → (https://docs.aws.amazon.com/cloudwatch/)

🕷️ AWS Glue Crawler
Our smart data detective. It crawls the data in S3, figures out the structure, and updates the Data Catalog so we can query like pros.
Learn more → (https://docs.aws.amazon.com/glue/latest/webapi/API_Crawler.html)

⚡ AWS Lambda
Code that runs only when it needs to — no servers, no hassle. Perfect for triggering transformations and actions on-the-fly.
Learn more → (https://docs.aws.amazon.com/lambda/index.html)

🧠 Amazon Athena
Instant SQL power! Run queries directly on your S3 data without setting up a database. Fast, flexible, and serverless.
Learn more → (https://docs.aws.amazon.com/athena/)

🗂️ AWS Glue Data Catalog
The brain behind the data. It keeps track of schemas, tables, and metadata so services like Athena know what they're working with.
Learn more → (https://docs.aws.amazon.com/glue/latest/dg/catalog-and-crawler.html)
 

### Installed Packages
```
pip install pandas
pip install boto3
pip install spotipy
pip install numpy
```


###🚀 How It Works: End-to-End Flow
1. 🎧 Data Extraction Begins
We kick things off by pulling music data using the Spotify API — albums, artists, tracks, and more.

2. ⏰ Scheduled by CloudWatch
Once a week, Amazon CloudWatch triggers the process automatically — no manual work needed.

3. 📥 Raw Data Lands in S3
A Lambda function runs and drops the freshly extracted data into the raw/ folder of an S3 bucket.

4. 🔄 Data Gets Cleaned & Transformed
A second Lambda function processes the raw data, cleans it up, and stores the polished output in the transformed/ folder in S3.

5. 🕵️‍♀️ Glue Crawler Scans the Data
AWS Glue Crawlers detect schema details from the transformed data — organizing it neatly in the Data Catalog.

6. 🔍 Query Time with Athena
With everything cataloged, Amazon Athena steps in to query and analyze the music data using simple SQL.

