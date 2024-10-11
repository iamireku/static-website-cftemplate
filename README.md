# S3 Static Website Hosting Template

This AWS CloudFormation template provisions an S3 bucket for hosting a static website. It includes options to enable or disable versioning and cross-region replication.

## Features

- **Static Website Hosting**: Easily host a static website on Amazon S3.
- **Versioning**: Optionally enable versioning to keep track of object changes.
- **Cross-Region Replication**: Optionally set up cross-region replication to replicate your objects to another S3 bucket in a different AWS region.

## Parameters

- **BucketName**: 
  - Description: Name of the S3 bucket to host the static website.
  - Type: String
  - Default: `my-static-website`
  - Allowed Pattern: `^[a-z0-9.-]+$` (lowercase letters, numbers, dots, and hyphens)

- **EnableVersioning**: 
  - Description: Enable S3 bucket versioning (true/false).
  - Type: String
  - Allowed Values: `true`, `false`
  - Default: `false`

- **EnableReplication**: 
  - Description: Enable cross-region replication (true/false).
  - Type: String
  - Allowed Values: `true`, `false`
  - Default: `false`

- **ReplicationDestinationBucket**: 
  - Description: Destination bucket for cross-region replication (required if replication is enabled).
  - Type: String
  - Default: `""`
  - Allowed Pattern: `^[a-z0-9.-]*$`

- **ReplicationDestinationRegion**: 
  - Description: AWS region of the destination bucket for cross-region replication.
  - Type: String
  - Default: `""`
  - Allowed Pattern: `^[a-z0-9-]*$`

## Conditions

- **EnableVersioningCondition**: Checks if versioning is enabled.
- **EnableReplicationCondition**: Checks if replication is enabled.

## Resources

- **StaticWebsiteBucket**: The S3 bucket configured for static website hosting.
- **WebsiteBucketPolicy**: A policy that allows public access to the bucket's objects.
- **ReplicationRole**: An IAM role that grants permissions for cross-region replication.
- **BucketReplicationConfig**: Configuration for cross-region replication.

## Outputs

- **WebsiteURL**: The URL of the static website hosted on S3.

## Usage

To use this template:

1. Open the AWS CloudFormation console.
2. Create a new stack and upload this template.
3. Fill in the required parameters, including the bucket name and options for versioning and replication.
4. Review and create the stack.

Once the stack is created, you can access your static website using the URL provided in the outputs section.

## Notes

- Make sure that the bucket name you provide is unique across all existing bucket names in S3.
- If you enable cross-region replication, ensure that the destination bucket exists in the specified region and that you have the necessary permissions to access it.
- The bucket name must adhere to S3 naming conventions, which include being globally unique and using only lowercase letters, numbers, dots, and hyphens.
