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
- KMS encryption keys are single-Region by default
- KMS multi-Region encryption keys can be created using advanced options and can be replicated into other Regions.
- You cannot export (copy out of the AWS KMS service in plaintext) your customer master key.

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
### aws kms encrypt
- Encrypts plaintext into ciphertext by using a customer master key.
```plaintext
aws kms encrypt --key-id YOURKEYIDHERE --plaintext fileb://secret.txt --output text --query CiphertextBlob | base64 --decode > encryptedsecret.txt
```

### aws kms decypt 
- Decrypts ciphertext that was encypted by an AWS KMS customer master key (CMK).
```plaintext
aws kms decrypt --ciphertext-blob fileb://encryptedsecret.txt --output text --query Plaintext | base64 --decode > decryptedsecret.txt

```

### aws kms re-encrypt
- Decrypts ciphertext and then re-encypts it entirely within AWS KMS (e.g. when you change the CMK or manually rotate the CMK)
```plaintext
aws kms re-encrypt --destination-key-id YOURKEYIDHERE --ciphertext-blob fileb://encryptedsecret.txt | base64 > newencryption.txt
```

## aws kms enable-key-rotation
- Enables automatic key rotation every 365 days.
```plaintext
aws kms enable-key-rotation --key-id YOURKEYIDHERE
aws kms get-key-rotation-status --key-id YOURKEYIDHERE
```

## aws kms generate-data-key
- Uses the CMK to generate a data key to encrypt data > 4KB. 
```plaintext
aws kms generate-data-key --key-id YOURKEYIDHERE --key-spec AES_256
```

## Envelope Encryption
- Encrypting the key that encrypts our data
- The CMK is used to encrypt the data key (or envelope key).
- The data key encrypts our data.
- Used for encrypting anything over 4 KB.
- Avoids sending all your data into KMS over the network.
- Remember the `GenerateDataKey` API call

> ### What is the name of the practice of encrypting plaintext data with a data key, and then encrypting the data key under another key?
>
> Envelope ecryption
> - When you encrypt your data, your data is protected, but you have to protect your encryption key. One strategy is to encrypt it. Envelope encryption is the practice of encrypting plaintext data with a data key, and then encrypting the data key under another key.



## KMS Key Rotation
- Automatic encryption is available for CMKs.
- KMS will rotate cryptographic material on `yearly` basis
- It saves `previous versions` of the cryptographic material so that you can still decrypt files that were previously encrypted.

## Certificate Management
### AWS Certificate Manager
- Create and manage SSL/TLS certificates for `securing` your website

### Secure Connections
- Enables secure connections to your website using `HTTPS`.

### CloudFront
- When using ACM with CloudFront, the certificate must be created in `us-east-1` region.

