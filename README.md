# AWS Security Hub Alert with Lambda

This project automates security alerts from AWS Security Hub using AWS Lambda, EventBridge, and SNS.

## Overview

The goal of this project is to trigger AWS Lambda to send an email alert whenever a new security finding is created in AWS Security Hub.

## Architecture

- **AWS Security Hub**: Monitors and detects security findings in your AWS environment.
- **AWS Lambda**: Receives security findings and sends alerts via SNS.
- **EventBridge**: Triggers Lambda when a new finding occurs.
- **SNS**: Sends email alerts with the findings.

## Steps Taken

### 1. **Set Up AWS Security Hub**
   - Enabled Security Hub in the AWS Console and configured it to detect security findings.
   
### 2. **Create Lambda Function**
   - Lambda function code to process findings:

   ```python
   import boto3

   def lambda_handler(event, context):
       sns = boto3.client('sns')
       sns.publish(
           TopicArn='arn:aws:sns:ap-south-1:221082192093:security-alert-topic',
           Message='Security Hub Finding: ' + str(event),
           Subject='AWS Security Alert'
       )
3. Create EventBridge Rule
Created an EventBridge rule to trigger Lambda when a new Security Hub finding is created.

4. Subscribe to SNS Topic
Subscribed an email address to the SNS topic for receiving notifications.

### **Step 5: Add, Commit, and Push to GitHub**

Now that you have your `README.md` file documenting the project:

1. **Stage the changes**:

   ```bash
   git add .

