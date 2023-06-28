# DynamoDB

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