# DynamoDB Key Takeaways

## Overview
- DynamoDB is a NoSQL serverless database, different from traditional RDBMS databases like MySQL or PostgreSQL.
- It provides horizontal scalability, unlike RDBMS databases which mostly scale vertically.

## Features
- DynamoDB is fully distributed, meaning it can scale to millions of requests per second, trillions of rows, and hundreds of terabytes of storage.
- It offers fast and consistent performance with low latency on retrieval.
- It's fully integrated with IAM for security, authorization, and administration.
- It supports event-driven programming with DynamoDB Streams.
- It's low cost and has auto-scaling capability.
- It provides different storage tiers with the standard and Infrequent Access (IA) table class.

## Data Structure
- DynamoDB is made out of tables, each having a primary key that must be defined before creating the table.
- Each table can have an infinite number of rows (also called items), and each item has attributes (similar to columns in a table).
- Attributes can be nested, added over time, and can be null.
- Each item can have up to 400 kilobytes of data.

## Primary Key
- Two options for primary keys: partition key (hash strategy) and partition key + sort key (hash + range).
- The partition key must be unique for each item.
- The combination of partition key and sort key must be unique for each item.
- The choice of partition key is crucial for data distribution. It should have high cardinality (can take on the most amount of values).

## Exam Tips
- For the exam, you may be asked to choose the best partition key for some tables. Always choose the one with the highest cardinality.
- DynamoDB does not support query joins or perform aggregation computations such as SUM or AVG.


Here are some of the key parameters you should be familiar with for the AWS Developer Associate exam:

| Parameter | Description |
| --- | --- |
| `TableName` | Specifies the name of the DynamoDB table. |
| `KeyConditionExpression` | A string that specifies the conditions for the query. |
| `ExpressionAttributeValues` | A dictionary that maps the substitution variables in your `KeyConditionExpression` to their actual values. |
| `ExpressionAttributeNames` | A dictionary that maps the placeholder names in your `KeyConditionExpression` to the actual attribute names in your table. |
| `ProjectionExpression` | A string that identifies one or more attributes to retrieve from the table. |
| `FilterExpression` | A string that contains conditions that DynamoDB applies after the `KeyConditionExpression`, but before the data is returned to you. |
| `ScanIndexForward` | Specifies the order for index traversal: If `True` (default), the traversal is performed in ascending order; if `False`, the traversal is performed in descending order. |
| `Limit` | The maximum number of items to evaluate (not necessarily the number of matching items). |
| `ConsistentRead` | If `True`, a strongly consistent read is used; if `False` (default), an eventually consistent read is used. |
| `IndexName` | The name of a secondary index to scan. This index can be any local secondary index or global secondary index. |

For the AWS Developer Associate exam, you should be familiar with these parameters and understand how they are used in different scenarios. You should also understand the difference between a `Query` and a `Scan` operation, how to use secondary indexes, and how to design and interact with DynamoDB tables in a way that optimizes for performance and cost.