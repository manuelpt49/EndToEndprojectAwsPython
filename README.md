# EndToEndprojectAwsPython

This end-to-end project uses AWS resources such as Redshift, Athena, S3, IAM, and Glue, and it was developed using Python. 

This project was implemented taking into consideration Darshil's videos - https://www.youtube.com/playlist?list=PLBJe2dFI4sgvavQzL2Hm5CsnoIWHY5fI3

Below I'd like to let you know which steps were executed to extract, transform, and load data into Redshift data warehouse.
1. Loading manually files into S3. Files are proportionated in the first video of the link shared above.
2. Getting data using Crawlers in AWS Glue. This resource allows us to create metadata in our data catalog to be queried after.
![image](https://github.com/manuelpt49/EndToEndprojectAwsPython/assets/79064546/7d8e33f5-af1f-4f1e-b5dc-2ca759e0b2ed)
3. Using AWS Athena, query our data catalog through SQL.
![image](https://github.com/manuelpt49/EndToEndprojectAwsPython/assets/79064546/62494d2f-31bf-4a09-9ae3-261958369a17)
4. Using Python (boto3 library) and our local machine, connecting all resources of AWS in our local machine within a notebook. Inside the notebook, we make queries to each table in our data catalog and we save the response in files locally, to be transformed then. Transformation applied inside was making some preprocessing in some columns of some tables and creating Dim and Fact tables to create our data model. At the root of this project is available the notebook (ConnectingWithAwsResources.ipynb). At the end of the notebook, we make the process to connect to Redshift and create the schema of the data warehouse. Also, we make a copy statement of data from S3 to redshift only for one table (dimDate). 
5. At this step we make the copy process of the other tables but now using AWS Glue. Here we implement the ETL pipeline using a notebook. We instantiated a redshift_connector library to allow a connection between our AWS Glue with Redshift. Due to this library is not available inside Glue, we must declare it as a parameter as I show in the image below.
![image](https://github.com/manuelpt49/EndToEndprojectAwsPython/assets/79064546/9818016d-8bc9-4067-9591-a35ff620d43b)
Besides, this step required an IAM role with permission between Glue, S3, and Redshift. Regarding the Redshift Cluster which executed the copy statement, We had to enable his inbound rules (Virtual Private Cloud - VPC) to permit traffic from AWS Glue and S3.
6. At the end, Dim and Fact tables were available in our data warehouse to feed reports, train models, or whatever was needed.

I want to thank Darshil for his amazing videos explaining end-to-end projects to get more experience in cloud providers such as AWS, Azure, and GCP.
