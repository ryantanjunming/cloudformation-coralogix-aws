# AWS CloudWatch-logs integarion for Coralogix

This template were created automatically from coralogix/coralogix-aws-serverless.
To make a change in the template go to the link below.

https://github.com/coralogix/coralogix-aws-serverless/tree/master/src/cloudwatch-logs

Coralogix provides a predefined Lambda function to easily forward your CloudWatch logs straight to the Coralogix platform.

IF you want to use **AWS Secrets** to store the private_key, first you need to deploy Coralogix SecretLayer form AWS Serverless Repository.
Take in consideration that both layers and lambda need to be in the same AWS Region.

## Prerequisites

* AWS user with permissions to create lambdas and IAM roles.
* AWS Cloudwatch log group & log stream
* A Coralogix account.
* in case you use SSM you should first deploy the [SSM lambda layer](https://us-east-1.console.aws.amazon.com/lambda/home?region=us-east-1#/create/app?applicationId=arn:aws:serverlessrepo:eu-central-1:597078901540:applications/Coralogix-Lambda-SSMLayer)

## Fields 

| Parameter | Description | Default Value | Required |
|---|---|---|---|
| Application name | The stack name of this application created via AWS CloudFormation. |   | :heavy_check_mark: |
| CoralogixRegion | The Coralogix location region, possible options are [Europe, Europe2, India, Singapore, US, US2].In case that you want to use Custom domain, leave this as default and write the Custom doamin in the ``CustomDomain`` filed. |  Europe | :heavy_check_mark: | 
| CustomDomain | The Coralogix custom domain,leave empty if you don't use Custom domain.| |  |
| CreateSecret | Set to False In case you want to use SSM with your secret that contains coralogix ApiKey. | True |  | 
| ApiKey | Your Coralogix secret key or incase you use your own created secret put here the name of your secret that contains the coralogix Api Key |  | :heavy_check_mark: | 
| ApplicationName | Application Name as it will be seen in Coralogix UI.|   | :heavy_check_mark: | 
| SubsystemName | Sybsystem Name as it will be seen in Coralogix UI.|   | :heavy_check_mark: | 
| CloudWatchLogGroupName | Has to contain a list of *log group* names separated by a comma(log-group1,log-group2,log-group3).|   | :heavy_check_mark: | 
| LayerARN | In case you are using SSM This is the ARN of the Coralogix Security Layer. Copy from the ``SSM`` serverless application the ARN that was installed on the AWS account. | | |
| NotificationEmail | If the lambda fails a notification email will be sent to this address via SNS (requires you have a working SNS, with a validated domain).| | |
| NewlinePattern | Do not change! This is the pattern for lines splitting.| ``(?:\r\n\|\r\|\n)`` | |
| FunctionArchitecture | Lambda function architecture, possible options are [x86_64, arm64]| x86_64 | |
| FunctionMemorySize | The maximum allocated memory this lambda may consume. Don't change| 1024 | |
| FunctionTimeout | The maximum time in seconds the function may be allowed to run. Don't change| 300 | |
| SamplingRate | Send messages with specific rate.| 1 | |
| BufferCharset | The charset to use for buffer decoding, possible options are [utf8, ascii]| utf8 | |

The application should be installed in the same AWS region as the CloudWatch log group.
 
**Note:** You can use log field as `Application/Subsystem` names. Use the following syntax: `$.my_log.field`.

## License

This project is licensed under the Apache-2.0 License.



