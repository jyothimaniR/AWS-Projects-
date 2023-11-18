# AWS-Projects-

**Building a Chatbot using Amazon Lex –**



**Architecture -** 

![image](https://github.com/jyothimaniR/AWS-Projects-/assets/150769721/d8a125c3-239c-432c-9811-ddb9fe137065)


Step 1: Create a Custom Bot in Amazon Lex

Log in to the AWS Management Console.

Navigate to the Amazon Lex service.

Click on "Create" to create a new bot.

Choose "Custom Bot" and provide a name for your bot.

Enable or Disable COPPA based on your bot's audience.

Customize the bot's behavior by adding intents and sample utterances.

Save the intent configurations.

![image](https://github.com/jyothimaniR/AWS-Projects-/assets/150769721/72726cbe-7827-404f-a3b1-bd77ecf12682)



Step 2: Test the Bot in Lex Dashboard

After saving the intent, navigate to the Lex dashboard.

Test the bot's behavior using the Lex dashboard.

Ensure that the bot responds appropriately to the sample utterances.

Connecting the Chatbot to a Weather API using Lambda Function


Procedure:

Step 1: Create a Lambda Function

Navigate to the AWS Lambda service in the AWS Management Console.

Click on "Create function."

Choose a function name, runtime (Node.js or any other supported language), and create a new role with the necessary permissions.

Click on "Create function" to create the Lambda function.

Step 2: Write Lambda Function Code





'use strict';

const axios = require("axios");

module.exports.getWeather = async (event) => {

`    `const city = event.currentIntent.slots["City"];

`    `const url = `http://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&APPID=08e3ad0437282f8abefa56ee74ab56af`;



`    `try {

`        `const response = await axios.get(url);

`        `const data = response.data;

`        `const answer = `The temperature is ${data.main.temp}°C and Humidity is ${data.main.humidity}.`;

`        `return {

`            `"sessionAttributes": {},

`            `"dialogAction": {

`                `"type": "Close",

`                `"fulfillmentState": "Fulfilled",

`                `"message": {

`                    `"contentType": "PlainText",

`                    `"content": answer

`                `}

`            `}

`        `};

`    `} catch (error) {

`        `console.error(error);

`        `return {

`            `"sessionAttributes": {},

`            `"dialogAction": {

`                `"type": "Close",

`                `"fulfillmentState": "Fulfilled",

`                `"message": {

`                    `"contentType": "PlainText",

`                    `"content": "Sorry, I couldn't fetch the weather information."

`                `}

`            `}

`        `};

`    `}

};



Step 3: Save and Deploy the Lambda Function

Save the Lambda function code.

Deploy the Lambda function.

Provide IAM Policies to Lambda to Access Amazon Lex Chatbot

Procedure:

Step 1: Create IAM Role for Lambda

Navigate to the IAM service in the AWS Management Console.

Click on "Roles" and then "Create role."

Choose "Lambda" as the use case and attach the necessary policies (e.g., AWSLambdaBasicExecutionRole).

Step 2: Add Additional Policy for Lex Access

Attach a policy that grants permission to invoke the Lex bot.

{

`  `"Version": "2012-10-17",

`  `"Statement": [

`    `{

`      `"Effect": "Allow",

`      `"Action": "lex:PostText",

`      `"Resource": "arn:aws:lex:REGION:ACCOUNT\_ID:bot/BOT\_NAME/ALIAS\_NAME"

`    `}

`  `]

}


Step 3: Attach IAM Role to Lambda

Go to the Lambda function configuration in the AWS Management Console.

Under the "Permissions" tab, click on "Role name" to navigate to the IAM role.

Attach the IAM role created earlier to the Lambda function.

Now, your Lambda function has the necessary permissions to access the Amazon Lex chatbot.

This project demonstrates the successful integration of natural language processing capabilities through Amazon Lex, serverless logic using Lambda functions, and a user-friendly Angular web application powered by Amazon Amplify. The chatbot can now effectively provide weather information based on user queries.
