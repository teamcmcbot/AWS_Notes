# KMS and Encryption

## KMS Key Management Service
- Managed service that makes it really easy for you to create
and control the encryption keys used to encrypt your data in
AWS.
- Seamlessly integrated with many AWS services to make encrypting data in those services as easy as checking a box.
    
    - S3
    - RDS
    - DyanmoDB
    - Lambda
    - EBS
    - EFS
    - CloudTrail
    - Developer Tools
- With KMS, it is simple to encrypt your data with encryption keys that you manage.

## CMK Customer Master Key
- Encrypt / Decrypt data up to 4KB
- Generate / encrypt /decrypt the Data Key
- Data Key: Use to encrypt/decrypt data.

## CMK Summary
- Alias: Your application can refer to the alias when using the CMK
- Creation Date: The date and time when the CMK was created
- Description: You can add your own description to describe the CMK
- Key State: Enabled, disabled, pending deletion, unavailable
- Key Material: Customer-provided or AWS-provided
- Stays Inside KMS: Can never be exported

    ### Set Up CMK
    - Create alias and description.
    - Choose key material
    - > Alias -> Description -> Key Material

    ### Key Adminstrative Permissions
    - IAM users and roles that can administer (but not use) the key through the KMS API.
    - > Users -> Roles -> Admin Permissions

    ### Key Usage Permissions
    - IAM users and roles that can use the key to encrypt and decrypt data.
    - > Users -> Roles -> Usage Permissions

## AWS-Managed CMK
- AWS-provided and AWS-managed CMK.
- Used on your behalf with the AWS services integrated with KMS.

## Customer-Managed CMK
- You create, own and manage yourself.

## Data Key
- Encryption keys that you can use to encrypt data, including large amounts of data.
- You can use a CMK to generate, encrypt, and decrypt data keys.

## KMS API Calls
> aws kms encrypt --key-id YOURKEYIDHERE --plaintext fileb://secret.txt --output text --query CiphertextBlob | base64 --decode > encryptedsecret.txt
> aws kms decrypt --ciphertext-blob fileb://encryptedsecret.txt --output text --query Plaintext | base64 --decode > decryptedsecret.txt
> aws kms re-encrypt --destination-key-id YOURKEYIDHERE --ciphertext-blob fileb://encryptedsecret.txt | base64 > newencryption.txt 
> aws kms enable-key-rotation --key-id YOURKEYIDHERE
> aws kms get-key-rotation-status --key-id YOURKEYIDHERE
> aws kms generate-data-key --key-id YOURKEYIDHERE --key-spec AES_256