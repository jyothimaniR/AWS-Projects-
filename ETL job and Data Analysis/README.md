# AWS-Projects-

**ETL job and Data Analysis** 

Architecture - 

![image](https://github.com/jyothimaniR/AWS-Projects-/assets/150769721/cc7dc5aa-8ae3-41a3-a0e1-98e840b5c3db)
















Resources used – S3 source and destination buckets, Glue Crawler, Glue ETL Job, Lambda Function, Athena and API Gateway.

1\. S3 Bucket:

Purpose:

The S3 bucket serves as the primary data store for raw data.

Configuration:

Create an S3 bucket in the AWS Management Console, choose a unique name, and select an appropriate region to store the data to be analyzed.

Configure versioning for data version control.

Implement server-side encryption for data at rest.

Establish access control through bucket policies and IAM roles, ensuring proper permissions.

Create a destination S3 bucket to store the processed data. 

Note: The source and destination buckets should not be the same to avoid an infinite loop.

2\. AWS Glue Crawler:

Purpose:

The Glue Crawler automates the process of discovering and cataloging metadata from raw data.

Configuration:

Create a Crawler in the AWS Glue Console.

Specify the S3 bucket as the data store for the crawler.

Set up a schedule for periodic crawling or trigger it manually when needed.

Define output settings, including the Glue Data Catalog database.

3\. AWS Glue ETL Job:

Purpose:

The ETL job transforms raw data into a structured format.

Configuration:

Create an ETL job in the AWS Glue Console, specifying the source and target connections (S3 buckets).

Define the transformations using PySpark or AWS Glue Studio.

Configure job parameters, such as allocated memory and timeout settings.

Implement error handling and logging within the ETL script.

Test and run the ETL job using sample data.

4\. AWS Lambda Function:

Purpose:

The Lambda function triggers the Glue ETL job based on events or schedules.

Configuration:

python

Copy code

import boto3

def lambda\_handler(event, context):

`    `glue\_client = boto3.client('glue')

`    `glue\_client.start\_job\_run(JobName="glueproject")

`    `return "Job Started"

Create a Lambda function in the AWS Lambda Console.

Configure an IAM role for the Lambda function with the necessary permissions to invoke the Glue ETL job.

Define triggers, such as an S3 event (object creation) or a CloudWatch event for scheduled execution.

Now the lambda will process the data from the source S3 bucket and dump the processed data into the destination S3 bucket.

![image](https://github.com/jyothimaniR/AWS-Projects-/assets/150769721/2ef96e36-8d19-4300-ba0c-560578d3b77b)

The transformed data is stored in a separate S3 bucket to maintain a clear separation from the raw data.

5\. AWS Glue Trigger:

Purpose:

The Glue Trigger is associated with the Glue ETL job and initiates the job based on a schedule or an event.

Configuration:

Set up a Glue Trigger in the AWS Glue Console.

Associate the trigger with the Glue ETL job.

Configure the trigger to start the job based on a schedule or an event, such as the completion of the Glue Crawler.

6\. Amazon Athena:

Purpose:

Athena allows for SQL queries on the transformed data stored in S3 through the Glue Data Catalog.

Configuration:

Set up Athena in the AWS Management Console.

Define tables in Athena using the Glue Data Catalog.

Use the Athena Query Editor or connect to Athena through other SQL clients.

Optimize queries by partitioning data and managing column statistics.

7\. API Gateway:

Purpose:

API Gateway exposes Athena queries through a RESTful API.

Configuration:

Create an API in API Gateway with resources and methods.

Set up integration with Athena as the backend, allowing API Gateway to execute SQL queries.

Implement security measures, such as API key authentication or IAM roles.

Deploy the API to make it publicly accessible.

8\. AWS Identity and Access Management (IAM):

Purpose:

IAM manages permissions and access control for each service.

Configuration:

Create IAM roles for each service (Lambda, Glue, Athena).

Define policies to grant specific permissions, following the principle of least privilege.

Attach roles to corresponding services to ensure secure interactions between components.

Conclusion - 

This architecture facilitates a scalable, serverless ETL process, providing efficient data processing and analysis capabilities. Ensure proper security measures, error handling, and logging for robustness and performance.
