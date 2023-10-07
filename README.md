# End-to-End Data Engineering Project with AWS and Python

This end-to-end project utilizes AWS resources such as Redshift, Athena, S3, IAM, and Glue, and was developed using Python.
![image](https://github.com/manuelpt49/EndToEndprojectAwsPython/assets/79064546/5bd63bf7-bf08-40b5-9f35-2c029fd0210e)
*Copy from Darshil's videos.

## References
This project was implemented taking into consideration Darshil's videos - [Darshil's YouTube Playlist](https://www.youtube.com/playlist?list=PLBJe2dFI4sgvavQzL2Hm5CsnoIWHY5fI3)

## Project Workflow

### 1. Loading Files into S3
Manually load files into S3. The files are proportioned in the first video of the link shared above.

### 2. Getting Data Using AWS Glue Crawlers
Use AWS Glue Crawlers to create metadata in the data catalog for subsequent querying.

![Image: Crawlers in AWS Glue](https://github.com/manuelpt49/EndToEndprojectAwsPython/assets/79064546/7d8e33f5-af1f-4f1e-b5dc-2ca759e0b2ed)

### 3. Querying Data Catalog with AWS Athena
Use AWS Athena to query the data catalog through SQL.

![Image: AWS Athena Query](https://github.com/manuelpt49/EndToEndprojectAwsPython/assets/79064546/62494d2f-31bf-4a09-9ae3-261958369a17)

### 4. Data Transformation with Python (boto3 library)
- Connect all AWS resources in the local machine within a notebook.
- Make queries to each table in the data catalog and save responses locally for transformation.
- Perform preprocessing on some columns and create Dim and Fact tables to establish the data model.
[Notebook: ConnectingWithAwsResources.ipynb](https://github.com/manuelpt49/EndToEndprojectAwsPython/blob/main/ConnectingWithAwsResources.ipynb)

### 5. ETL Pipeline Implementation with AWS Glue
- Use AWS Glue for ETL pipeline implementation through a notebook.
  [Notebook: ConnectingWithAwsResources.ipynb](https://github.com/manuelpt49/EndToEndprojectAwsPython/blob/main/CopyDataGlue.ipynb)
- Instantiate the `redshift_connector` library to connect AWS Glue with Redshift.
- Declare the library as a parameter due to its unavailability inside Glue.

![Image: AWS Glue ETL Pipeline](https://github.com/manuelpt49/EndToEndprojectAwsPython/assets/79064546/9818016d-8bc9-4067-9591-a35ff620d43b)

**Additional Steps:**
- Configure IAM role permissions between Glue, S3, and Redshift.
- Enable inbound rules in the Redshift Cluster's VPC to allow traffic from AWS Glue and S3.

### 6. Data Warehouse Availability
Dim and Fact tables are now available in the data warehouse for reporting, model training, or other necessary purposes.
![image](https://github.com/manuelpt49/EndToEndprojectAwsPython/assets/79064546/8f855439-fb72-479b-802e-757045e36402)


## Acknowledgments
Special thanks to Darshil for his informative videos explaining end-to-end projects on various cloud providers such as AWS, Azure, and GCP.
