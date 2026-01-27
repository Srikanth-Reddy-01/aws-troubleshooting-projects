# Project 3: S3 AccessDenied Error – IAM Troubleshooting

## Environment
- Cloud Platform: AWS
- Service: Amazon S3
- Security: AWS IAM
- IAM User with limited permissions

## Problem
An IAM user was unable to upload files to an S3 bucket and received an **AccessDenied** error, even though the bucket existed and was accessible in the console.

## Symptoms
- S3 bucket was visible in the AWS Console
- File upload operation failed with **AccessDenied**
- No infrastructure or service outage observed

## Investigation
- Verified that the S3 bucket existed and was correctly named
- Confirmed the IAM user could log in and access the S3 service
- Reviewed the IAM policy attached to the user
- Identified that required permissions for object upload were missing

## Root Cause
The IAM policy attached to the user did not include the `s3:PutObject` permission on the bucket objects ARN, which is required to upload files to an S3 bucket.

## Resolution
- Updated the IAM policy to include `s3:PutObject` permission
- Ensured the correct resource ARN was used (`bucket-name/*`)
- Retested the upload operation after policy update

## Outcome
The IAM user was able to successfully upload files to the S3 bucket after correcting the IAM policy.

## Key Learning
- S3 access is strictly controlled by IAM permissions
- Console visibility and object-level actions require separate permissions
- `s3:PutObject` must be granted on the bucket objects ARN
- Proper IAM policy analysis is essential for resolving AccessDenied errors

## Skills Demonstrated
- AWS IAM policy analysis
- S3 permission troubleshooting
- Least-privilege access design
- Root cause analysis
