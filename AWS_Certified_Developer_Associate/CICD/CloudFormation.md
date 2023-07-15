# CloudFormation

## Infrastructure As Code
- CloudFormation allows you to manage, configure, and provision AWS infrastructure as YAML or JSON code.

## Parameters
- Input custom values

## Conditions
- provision resources based on environment

## Resources
- Mandatory
- Describes the AWS resources that CloudFormation will create.

## Mappings
- Create custom mappings like Region: AMI

## Transform
- Reference code located in s3, e.g. Lambda code or reusable snippets of CloudFormation code.

## CloudFormation Summary 
- YAML or JSON templates are used to describe the end state of the infrastructure you are provisioning or changing.
- After creating the template, you upload it to CloudFormation where it is stored in S3. 
- CloudFormation reads the template and makes API calls on your behalf.
- The resulting set of resourcs that CloudFormation builds from your template is called a "stack".

