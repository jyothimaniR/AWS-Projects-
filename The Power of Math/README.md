#AWS Projects 

The Power of Math

Overview –

"The Power of Math" is a comprehensive project that combines web hosting, mathematical operations, and database storage using AWS services. The project is structured into distinct phases, each contributing to the overall functionality and user experience.

Application architecture

The diagram below provides a visual representation of the services used in this tutorial and how they are connected. This application uses AWS Amplify, Amazon API Gateway, AWS Lambda, Amazon DynamoDB, and AWS Identity and Access Management (IAM).

![](https://d1.awsstatic.com/webteam/getting_started/GSRC%202020%20updates/full-stack%20amplify%20console%20arch%20diagram%20module%205.8d82fc2a7b47b307dfcefb6fa5f364e8c24426bc.png)

AWS services Used –

1.AWS Amplify: Used for hosting the website.

2.AWS Lambda: Executes the core mathematical operations.

3.Amazon API Gateway: Facilitates the invocation of the Lambda function and enables CORS.

4.Amazon Dynamo DB: Serves as the storage solution for the application.

5. AWS Identity and Access Management (IAM):Manages access control and permissions.

1. Website Creation

1.1 Create a Web Page (INDEX.html)

Create an HTML webpage that represents the content you want to host on the internet. Save it as INDEX.html.

1.2 Host the Website Using AWS Amplify

Utilize the Amplify AWS service to host your website.

Enter the App name and Environment name in Amplify.

Choose the HTML page (INDEX.html) you want to host.

2. Perform Calculation

2.1 Create a Lambda Function

Develop a Lambda function using Python scripting (Boto 3).

Test and verify that the code runs error-free.

2.2 Invoke Lambda Function

Create a new REST API.

Enable CORS (Cross-Origin Resource Sharing) to facilitate content fetching from other domains.

API Gateway provides tools for creating and documenting web APIs that route HTTP requests to Lambda functions. Also it's a very common serverless integration on AWS.

3. Storage with Dynamo DB

3.1 Create a Dynamo DB Database

Establish a Dynamo DB Database to serve as storage.

Dynamo DB supports key-value and document data models, making it suitable for this application over other Databases.

3.2 Assign IAM Permissions

Grant IAM permissions to the Lambda function for accessing Dynamo DB.

Assign an inline policy to the Lambda function with the following permissions:

{

"Version": "2012-10-17",

"Statement": [

{

"Sid": "VisualEditor0",

"Effect": "Allow",

"Action": [

"dynamodb:PutItem",

"dynamodb:DeleteItem",

"dynamodb:GetItem",

"dynamodb:Scan",

"dynamodb:Query",

"dynamodb:UpdateItem"

],

"Resource": "arn:aws:dynamodb:ap-south-1:233676577733:table/ThePowerOfMath"

}

]

}

With the help of this IAM inline policy Lambda function will be able to write down the results of the application every time when it's invoked.

4. Testing the Application

4.1 Integration with API Gateway

Include the API Gateway link in your code.

4.2 Testing the App

Open the Amplify website link.

Verify that the application runs successfully.

![](https://user-images.githubusercontent.com/150769721/283196743-6df5960a-d49c-4103-80fa-03062d73c2d8.png)

2 to the power 8 equals 256, which is displayed on the above image as a result of the application.

Conclusion –

"The Power of Math" showcases a robust and integrated solution for mathematical operations, hosting a website, and managing data storage. The project's clear documentation and structured approach provide a comprehensive overview, making it accessible for users to understand, deploy, and extend its capabilities.
