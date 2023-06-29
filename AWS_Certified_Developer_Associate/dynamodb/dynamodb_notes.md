# DynamoDB

## DynamoDB Access Control
- DynamoDB provides access control mechanisms to secure and control access to your tables and data.
- Access control in DynamoDB is primarily managed through AWS Identity and Access Management (IAM).
- IAM allows you to define fine-grained permissions for users, groups, and roles, granting or denying access - to specific DynamoDB resources.
- Permissions can be set at the table level, enabling you to control read, write, and management actions.
- IAM policies define the permissions and are attached to IAM entities.
- You can also use Attribute-Based Access Control (ABAC) to set fine-grained access controls based on item - attributes.
- ABAC allows you to define conditional expressions in IAM policies, granting or denying access based on - attribute values.
- Additionally, you can use Identity-Based Access Control (IBAC) to control access based on user identities, - roles, or group memberships.
- DynamoDB also integrates with other AWS services like AWS Identity Federation and Amazon Cognito for more - advanced access control scenarios.
- Monitoring and auditing tools like AWS CloudTrail can be used to track access and changes to DynamoDB resources.

By properly configuring and managing access control, you can ensure the security and privacy of your DynamoDB tables and data.

## Global Secondary Index vs Local Secondary Index

Global Secondary Index (GSI) and Local Secondary Index (LSI) are two types of indexes in Amazon DynamoDB that provide efficient querying capabilities.

### Global Secondary Index (GSI):
- Contains a different partition key and/or sort key from the base table.
- Allows querying the table using different attributes as keys.
- Can be defined at table creation or added later.
- Supports multiple GSIs.
- Offers eventual consistency by default.
- Incurs additional costs for storage and provisioned throughput.

### Local Secondary Index (LSI):
- Shares the same partition key as the base table but has a different sort key.
- Provides an additional way to query data within a single partition of the table.
- Created when defining the table's schema and cannot be modified later.
- Supports up to five LSIs.
- Offers strong consistency.
- Does not incur additional storage costs but may impact provisioned throughput.

GSIs and LSIs enhance data access patterns and allow flexible querying in DynamoDB. Consider the access patterns and query requirements when designing your table schema to decide the appropriate use of GSIs, LSIs, or a combination of both.

Remember, GSIs provide broader querying capabilities with different keys, while LSIs offer specific querying within a partition.

## Scan vs Query API call

## DynamoDB API Calls

## DynamoDB TTL
- Defines an expiry time for your data. Once expired, an item is marked for deletion (deleted within 48 hours)
- Use Case: remove irrelevant or old data (session data, event logs, temporary data)
- Reduce cost of your table by removing data which is no longer relavant.

## DynamoDB Streams
- Time ordered sequence of item level modification (insert, update, delete)
- Data encrypted and stored for 24 hours
- Can be event source for Lambda

## Provisioned Throughput Exceeded & Exponential Backoff
- `ProvisionedThroughputExceededException` error means the number of request is too high.
- Exponential backoff improves flow by retrying requests using progressively longer waits.
- Exponential backoff is a feature in every AWS SDK (S3, CloudFormation, SES).

