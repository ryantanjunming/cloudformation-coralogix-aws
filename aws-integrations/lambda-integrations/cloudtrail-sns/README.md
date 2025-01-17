# AWS CloudTrail-SNS integration for Coralogix

This template were created automatically from coralogix/coralogix-aws-serverless.
To make a change in the template go to the link below.

https://github.com/coralogix/coralogix-aws-serverless/tree/master/src/cloudtrail-sns

Coralogix provides a predefined Lambda function to easily forward your CloudTrail logs through SNS to the Coralogix platform.

## Prerequisites
* Active CloudTrail 
* Permissions to create lambda functions.
* SNS topic with permission `SNS:Publish` on the S3 bucket.
* An AWS account.
* A coralogix account.

## Fields 

| Parameter | Description | Default Value | Required |
|---|---|---|---|
| Application name | The stack name of this application created via AWS CloudFormation. |   | :heavy_check_mark: |
| CoralogixRegion | The Coralogix location region, possible options are [Europe, Europe2, India, Singapore, US, US2].In case that you want to use Custom domain, leave this as default and write the Custom doamin in the ``CustomDomain`` filed. |  Europe | :heavy_check_mark: | 
| CustomDomain | The Coralogix custom domain,leave empty if you don't use Custom domain. |  |  | 
| ApiKey | Your Coralogix secret key. |   | :heavy_check_mark: | 
| ApplicationName | Application Name as it will be seen in Coralogix UI. |   | :heavy_check_mark: | 
| SubsystemName | Sybsystem Name as it will be seen in Coralogix UI. |   | :heavy_check_mark: | 
| SNSTopicARN | The arn of the SNS topic (must be in the same region as the S3 bucket) |   | :heavy_check_mark: | 
| S3BucketName | The name of the S3 bucket with CloudTrail logs to watch (must be in the same region as stack that you will create). |   | :heavy_check_mark: | 
| S3KeyPrefix | The prefix of the path within the log, this way you can choose if only part of your bucket is shipped. |   |  | 
| S3KeySuffix | A filter for the suffix of the file path in your bucket, the default is  |  .json.gz. |  | 
| NotificationEmail | If the lambda fails a notification email will be sent to this address via SNS (requires you have a working SNS, with a validated domain).| | |
| FunctionArchitecture | Lambda function architecture, possible options are [x86_64, arm64]| x86_64 ||
| FunctionMemorySize | The maximum allocated memory this lambda may consume. Don't change| 1024 | |
| FunctionTimeout | The maximum time in seconds the function may be allowed to run. Don't change| 300 | |

## License

This project is licensed under the Apache-2.0 License.

