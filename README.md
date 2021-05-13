# Purpose
This Lambda function will clean a DynamoDB table used by the [Device Grant flow logic for Cognito](https://github.com/aws-samples/cognito-device-grant-flow) by:
 - Expiring non expired Codes that reach their maximum lifetime
 - Deleting non expired and expired Codes that reach their maximum visibility lifetime

# How to deploy it?
 - Create a new Lambda function (NodeJS based, tested with nodejs10.x)
 - Associate a IAM Execurtion role that allows:
   - Basic Lambda Execution permissions
   - Access to the DynamoDB table for Read, Update, and Delete operations
 - Create two environment variable:
   - DYNAMODB_TABLE that references the DynamoDB table that store the Codes and their status
   - DYNAMODB_MAX_VISIBILITY that defines the maximum visibility lifetime in seconds after expiration
 - Create a CloudWatch scheduled event following instructions at: https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/RunLambdaSchedule.html

# Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

# License

This library is licensed under the MIT-0 License. See the LICENSE file.

