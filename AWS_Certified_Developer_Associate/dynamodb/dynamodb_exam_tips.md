# Exam Tips
## What is DynamoDB
- DynamoDB is a low latency NoSQL database.
## Data Models
- Supports both document and key-value data models (JSON, HTML, XML).

## Consistency Models:
- Eventually consistent
- Strongly consistent
- DynamoDB Transactions (ACID transactions)

## DynamoDB Features
- Consists of tables, items, and attributes.
## 2 Types of Primary Key
- Partition key
- Composite key  (partition key + sort key)

## Access Control
- Fine-Grained Access Control with IAM
- IAM condition paramter `dynamodb:LeadingKeys` allows users to access only items where the partition key value mathes their User_ID

## DynamoDB Secondary Indexes
- Enable fast queries on specific data columns.
- Give you a different view of your data based on alternative partition / sort keys.
### Local Secondary Index
- Same partition key and different sort key to your table.
- Must be created when you create table.
- Cannot be modified or deleted.
### Global Secondary Index
- Different partition key and different sort key to your table.
- Can be created any time.

## DynamoDB Query
### Query 
- Finds Items in a Table
- Using only the primary key attribute, you provide the primary key name and a distinct value to search for.
### Results
- Sorted
- Query results are always sorted in ascending order by the sort key if there is one.
## Reverse
- Set `ScanIndexForward` Paramter to False
- This reverses the order of query result.

## Scan
- Scan operation examines every item in the table and by default returns all data attributes.
- Use the `ProjectionExpression` parameter to refine the results.

### Make Scans More Efficient
- Reduce the impact of query or scan by setting a smaller page size which uses fewer read operations.
- Isolate scan operations to specific tables and segregate them from your mission-critical traffic.
- Try parallel scans rather than default sequential scan. 
- A query operation is generally more efficient than a scan.
- Design tables in a way that you can use `Query`, `Get`, or `BatchGetItem` APIs.

## Provisoned Throughput
- Provisioned throughput is measured in capacity units.

> ### You have a motion sensor which writes 600 items of data every minute. Each item consists of 5KB. What should you set the write throughput to? 
>
> - One write request unit represents one write for an item up to 1 KB in size. 
> - If you write 600 items every minute, it means 10 items are written per second ( 600 / 60 ). 
> - The total number of write capacity units required depends on the item size. 
> - If your item size is 5 KB, just multiply 10 items by 5 KB, 
> - so you require 50 write capacity units to sustain one write request.

### Write Capacity Units
- Each capacity unit gives 1 * 1KB write per second
### Strongly Consistent Reads
- 1 * 4KB read per second
### Eventually Consistent Reads (Default)
- 2 * 4KB reads per second

## On-Demand Capactiy
- Unpredictable application traffic.
- Pay-per-use model.

## Provisioned Capacity
- Read and write capacity requirements can be forecasted.
- Application traffic is consistent or increases gradually.

## DynamoDB accelerator (DAX)
- Provides in-memory caching for DyanmoDB tables.
- Improves response times for eventually consistent reads only.
- Data is written to the cache and the backend store at the same time.
- Point your API calls at the DAX cluster instead of table.
- If item you are querying is in the cache, DAX will return it.
- Not suitable for write-intensive applications or applications that require strongly consistent reads.

## DynamoDB TTL
- Defines an expiry time for your data. Once expired, an item is marked for deletion.
- Great for removing irrelevant or old data (session data, event logs, temporary data).
- Reduce cost of table by automatically removing data which is no longer relevant.

## DynamoDB Streams
- time-ordered sequence of item level modifications in your DynamoDB tables.
- Data is encrypted and stored for 24 hours only.
- Can be used as an event source for Lambda, so you can create applications that take actions based on events in your DynamoDB table.

## Exponential Backoff
- `ProvisionedThroughputExceededException` error means the number of requests is too high.
- Exponential backoff improves flow by retrying requests using progressively longer waits.
- Exponential backoff is a feature of every AWS SDK and applies to many services within AWS (S3, CloudFormation, SES).

## AWS CLI Commands
| AWS CLI Command   | Usage                                                                                     |
|:------------------|:------------------------------------------------------------------------------------------|
| create-table      | `Creates` a new table                                                                     |
| put-item          | Adds a `new` item into a table or `replaces` an old item with a new one                   |
| get-item          | Returns a set of `attributes for an item` with given primary key                          |
| update-item       | Allows you to `edit` the attribute of an existing item (e.g. `add or delete` attributes)  |
| update-table      | `Modifies` a table (e.g. modify the provisioned throughtput settings of table)            |
| list-tables       | Returns a `list of tables` in your account                                                |
| describe-table    | Returns `information about` the table (e.g current status, creation date, pk, indexes)    |
| scan              | Reads every item in a table and returns `all items` and attributes. Use filter to return fewer items|
| query             | Queries the table based on a `partition key` value that you provide                       |
| delete-item       | Allows you to delte item based on its `primary key`.                                      |
| delete-table      | `Deletes` a table, including all of its items.                                            |







