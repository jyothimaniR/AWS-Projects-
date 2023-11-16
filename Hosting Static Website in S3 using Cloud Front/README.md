# AWS-Projects-

**Project Documentation: Hosting a Static Website in S3 Bucket using CloudFront Distribution**

Objective:

The objective of this project is to host a static website on Amazon S3, enhance security with SSL/TLS certificates, and optimize performance using CloudFront distribution. The primary AWS resources used in this project include S3, Route 53, ACM (AWS Certificate Manager), and CloudFront.

Steps:

1\. Create a new S3 Bucket:

Resource Used: S3

Action:

Create a new S3 bucket with the same name as the website.

Note:

The bucket name must be unique globally.

2\. Enable Static Website Hosting:

Resource Used: S3

Action:

Navigate to the bucket's Properties tab.

Select "Static website hosting" and enable static hosting.

Specify the home page (HTML file).

Note:

This step makes the S3 bucket ready to host a static website.


3\. Make S3 Bucket Public:

Resource Used: S3

Action:

Create an S3 bucket policy to make all objects publicly accessible.




Bucket Policy:

json

Copy code

{

`    `"Version": "2012-10-17",

`    `"Statement": [

`        `{

`            `"Sid": "PublicReadGetObject",

`            `"Effect": "Allow",

`            `"Principal": "\*",

`            `"Action": [

`                `"s3:GetObject"

`            `],

`            `"Resource": [

`                `"arn:aws:s3:::your-website-bucket-name/\*"

`            `]

`        `}

`    `]

}

Note:

This policy allows public read access to all objects in the bucket.

4\. Obtain SSL/TLS Certificate:

Resources Used: ACM, Route 53

Action:

Purchase a domain name from Route 53 or another domain registrar.

Create an A Record for the website with Simple Routing.

Go to ACM, request a public certificate, and enter the domain name.

Complete the validation process to obtain the SSL/TLS certificate.

![](C:\Users\Admin\OneDrive\Documents\GitHub\AWS-Projects-\Hosting Static Website in S3 using Cloud Front\Pictures\Aspose.Words.ab546bbe-9bd5-40c7-a292-162326f252a2.001.png)










5\. Create CloudFront Distribution:

Resource Used: CloudFront

Action:

Create a CloudFront distribution.

Select the S3 bucket as the origin and choose the SSL/TLS certificate.

(Ensure the certificate is created in the US East (N.Virginia) Region if CloudFront is to be enabled.)

Note:

This step optimizes the website by distributing content globally.

6\. Update DNS Record:

Resource Used: Route 53

Action:

Edit the A Record to route all traffic to the CloudFront distribution.

Note:

This step directs the domain to the CloudFront distribution.

![](C:\Users\Admin\OneDrive\Documents\GitHub\AWS-Projects-\Hosting Static Website in S3 using Cloud Front\Pictures\Aspose.Words.ab546bbe-9bd5-40c7-a292-162326f252a2.002.png)










7\. Completion:

Outcome:

The static website is now hosted securely on the S3 bucket with HTTPS via CloudFront.

The website is optimized for performance through the CloudFront content delivery network.


Conclusion:

Following these steps ensures a secure, performant, and globally accessible static website hosted on AWS using S3, ACM, Route 53, and CloudFront.

