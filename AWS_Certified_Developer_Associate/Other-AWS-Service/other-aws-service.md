# Other AWS Service

## SQS
- SQS is a distributed message queueing system.
- Allow us to decouple the components of an application so that they are independent.
- Pull-based, not push-based.
  ## SQS Features
  - Decouple the components of an application so they run independently, easing management between components.
  - Any component can store messages in the queue. Messages can contain up to 256 KB of text in any format
  - Any component can later retrieve messages using SQS API.

  ## SQS Key Facts
  - Pull-Based
  - Messages are `256 KB` in size
  - Text Data: XML, JSON, unformatted text.
  - Guarantee: Messages will be processed at least once.
  - Messages can be kept in queue from one minute to 14 days.

  ### SQS Queue Types
    #### Standard Queues (default)
    - Nearly unlimited number of transactions per second.
    - Guarantee message is delivered at least once.
    - Provides best-effort ordering which ensures messages are generally delivered in the same order as they are sent.
    - Might contain duplicate.
    #### FIFO (First-in-first-out) Queues
    - Order in which messages are sent and received is strictly preserved.
    - A message is delivered once and remains available until a consumer processes and deletes it. 
    - Duplicates are not introduced.
    - 300 TPS limit

    | Standard                          | FIFO                                                                  |
    |:----------------------------------|:----------------------------------------------------------------------|
    | Best-effort ordering              | First-in-first-out message order is strictly presereved               |
    | Message delivered at least once   | Messages are delivered once.                                          |
    | Occational duplicates             | No duplicates                                                         |
    | Default queue type                | Good for banking transactions which need to happen in a strict order. |

  ### SQS Settings
    #### Visibility Timeout
    - Default 30 seconds.
    - Increase if the task takes more than 30 seconds to complete.
    - Max is 12 hours.

    | Short Polling                          | Long Polling                                                                  |
    |:----------------------------------|:----------------------------------------------------------------------|
    | Returns a response immediately even if the message queue being polled is empty| Periodically polls the queue. |
    | Can result in alot of empty responses if nothing is in the queue.| Doesn't return a response until a message arrives in the message queue or the long poll times out|
    | You will still pay for theses responses| Can save money!|
    | | Long polling is generally preferable to short polling.|

  ### SQS Delay Queues & Large Messages
    #### SQS Delay Queues
    - Postpone delivery of new messages to a queue for a number of seconds
    - Messages sent to the Delay Queue remain invisible to consumers for the duration of the delay period.
    - Default delay is 0 seconds, maximum is 900 seconds.
    - For standard queues, changing the setting doesn't affect the delay of messages already in the queue, only new messages.
    - For FIFO queues, this affects the delay of messages already in the queue.
    #### SQS Delay Queue use-case
    - add delay of a few seconds to allow updates to your sales and stock control databases before sending notification to a customer confirming an online transaction.

    #### Managing Large SQS Messages
    - Store large messages - 256 KB - 2 GB in S3
    - AWS SDK for Java, provides API for S3 bucket and object operations.
    - Amazon SQS Extended Client Library for Java to manage them in S3
    - Cannot use: AWS CLI, AWS Manangement Console / SQS Console, SQS API



## SNS Simple Notification Service
  ### SES vs SNS

## Kinesis 
  ### Kinesis Data Stream
  ### Kinesis Shards and Consumers

## Elastic Beanstalk

## RDS & Elastic Beanstalk

## Other AWS Servics Summary