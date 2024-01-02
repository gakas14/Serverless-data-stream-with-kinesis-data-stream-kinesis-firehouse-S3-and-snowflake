# Serverless-data-stream-with-kinesis-data-stream-kinesis-firehouse-S3-and-snowflake

Use Postman to make an API call, then Amazon API Gateway will trigger a Lambda function then the function will write into the s3 bucket, after what snowpipe will be trigger to write the data into snowflake. To not trigger snowpipe for every Api call and optimize the process, we will use Amazon Kinesis data Stream to collect the data first (dump the data only after some period of time or if there are few messages) then use Kinesis Firehouse to dump the data intro s3. 

 

Step 1: Create the Lambda Role 

 

Step 2: Create the lambda function to read the data from API Gateway and put in Kinesis Data Stream 

 

Step 3: Create API Gateway and make the integration with AWS Lambda create in Step 2 

Create a simple HTTP API and integrated with the lambda function 

Configure the route: POST method  

Get the api endpoint " https://fwpwl5qova.execute-api.us-east-1.amazonaws.com/dev/project3_lambda1_kinesis_apigateway" 

 

 

Step 4: Create Kinesis Data Stream to consume data from AWS Lambda create in step 2 

 

Step 5: Create a second Lambda function for processing the data before s3 dump 

This second lambda function will transform the data( decode the data, to put a delimiter in between each records), to make it easy to put on snowflake. 

We will convert the binary data intro a string data. Then add a \n to make a new line. 

 

Step 6: Create a S3 bucket that will be the kinesis Firehose destination 

S3  

Step 7: Create Kinesis Firehose 

Create kinesis firehouse 

 Activate Transform source records with AWS Lambda 

 

Step 8: Create Snowflake role. 

Storage Integration Creation: Copy the snowflake role arm into the snowflake console, Copy the s3 bucket arm role. 

Copy the 'STORAGE_AWS_IAM_USER_ARN' ARN and 'STORAGE_AWS_EXTERNAL_ID' from Snowflake and update the Trust Policy in the snowflake role in IAM  

Create an event notification for the s3 bucket 

 

Step 9: Test the pipeline 

 Open postman and pass a series of records 

Check the data into snwoflake 
