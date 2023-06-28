# AWS Certified Developer Associate Notes
![Developer Associate Badge](https://images.credly.com/size/220x220/images/b9feab85-1a43-4f6c-99a5-631b88d5461b/image.png)

The purpose of this is to consolidate and document my preparation for AWS Certified Developer Associate (DVA-C02) exam.

## Courses
Video Course:
- [acloudguru](https://learn.acloud.guru/course/aws-certified-developer-associate/overview)
- [Udemy course by Stephane Maarek](https://www.udemy.com/course/aws-certified-developer-associate-dva-c01) 

## Practice Exams
Practice exam:
- [Udemy | Stephane Maarek](https://www.udemy.com/course/aws-certified-developer-associate-practice-tests-dva-c01)
- [TutorialsDojo | Jon Bonso](https://portal.tutorialsdojo.com/courses/aws-certified-developer-associate-practice-exams/)

## Other resource
- [AWS Skillbuilder Exam Prep](https://explore.skillbuilder.aws/learn/course/external/view/elearning/14723/exam-prep-aws-certified-developer-associate-dva-c02-with-practice-material)
- [Whitepaper](https://aws.amazon.com/whitepapers/?whitepapers-main.sort-by=item.additionalFields.sortDate&whitepapers-main.sort-order=desc&awsf.whitepapers-content-type=*all&awsf.whitepapers-tech-category=*all&awsf.whitepapers-industries=*all&awsf.whitepapers-business-category=*all&awsf.whitepapers-global-methodology=*all)
- [Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-dev-associate/AWS-Certified-Developer-Associate_Exam-Guide.pdf)

## Exam Guide

| Domain                                    | % of Exam |
|:------------------------------------------|:----------|
| Domain 1: Development with AWS Services   | 32%       |
| Domain 2: Security                        | 26%       |
| Domain 3: Deployment                      | 24%       |
| Domain 4: Troubleshooting and Optimization| 18%       |
| **Total**                                 | **100%**  |

## Cost
| Item                            | Cost                |
|:--------------------------------|:--------------------|
| acloudguru                      | *PAID*              |
| Udemy course by Stephane Maarek | S$17.98 ~ $13.88 USD|
| Udemy practice exam             | S$12.98 ~ $10.03 USD|
| TutorialsDojo practice exam     | $10.99 USD          |
| Exam                            | *PAID*              |
| **Total**                       | **$34.90 USD**      |

## Notes
=-------------------------------------------=
= AWS Certified Developer Associate Notes   =
=-------------------------------------------=

- [ ] DynamoDB maximum item size of 400 KB
    DynamoDB read requests can be either strongly consistent, eventually consistent, or transactional.
    * A strongly consistent read request of an item up to 4 KB requires one read request unit.
    * An eventually consistent read request of an item up to 4 KB requires one-half read request unit.
    * A transactional read request of an item up to 4 KB requires two read request units.
    If you need to read an item that is larger than 4 KB, DynamoDB needs additional read request units. The total number of read request units required depends on the item size, and whether you want an eventually consistent or strongly consistent read. For example, if your item size is 8 KB, you require 2 read request units to sustain one strongly consistent read, 1 read request unit if you choose eventually consistent reads, or 4 read request units for a transactional read request.

	One write request unit represents one write for an item up to 1 KB in size. If you need to write an item that is larger than 1 KB, DynamoDB needs to consume additional write request units. Transactional write requests require 2 write request units to perform one write for items up to 1 KB. The total number of write request units required depends on the item size. For example, if your item size is 2 KB, you require 2 write request units to sustain one write request or 4 write request units for a transactional write request.

    For example, suppose that you create a provisioned table with 6 read capacity units and 6 write capacity units. With these settings, your application could do the following:
    * Perform strongly consistent reads of up to 24 KB per second (4 KB × 6 read capacity units).
    * Perform eventually consistent reads of up to 48 KB per second (twice as much read throughput).
    * Perform transactional read requests of up to 12 KB per second.
    * Write up to 6 KB per second (1 KB × 6 write capacity units).
    * Perform transactional write requests of up to 3 KB per second.

- [ ] ECS:
	- If you terminate a container instance in the RUNNING state, that container instance is automatically removed or deregistered from the cluster. However, if you terminate a container instance in the STOPPED state, that container instance isn’t automatically removed from the cluster.
	- To deregister your container instance from the cluster, you should deregister it after terminating it in the STOPPED state by using the Amazon ECS Console or AWS Command Line Interface. The deregistered container instance will no longer appear as a resource in your Amazon ECS cluster.

- [ ] The purpose of resharding in Amazon Kinesis Data Streams is to enable your stream to adapt to changes in the rate of data flow. You split shards to increase the capacity (and cost) of your stream. You merge shards to reduce the cost (and capacity) of your stream.
	One approach to resharding could be to split every shard in the stream—which would double the stream’s capacity. However, this might provide more additional capacity than you actually need and therefore create unnecessary cost.
	You can also use metrics to determine which are your “hot” or “cold” shards, that is, shards that are receiving much more data, or much less data, than expected. You could then selectively split the hot shards to increase capacity for the hash keys that target those shards. Similarly, you could merge cold shards to make better use of their unused capacity.
	You can obtain some performance data for your stream from the Amazon CloudWatch metrics that Kinesis Data Streams publishes. However, you can also collect some of your own metrics for your streams. One approach would be to log the hash key values generated by the partition keys for your data records. Recall that you specify the partition key at the time that you add the record to the stream.

- [ ] Amazon ECS supports the following task placement strategies:
	binpack – Place tasks based on the least available amount of CPU or memory. This minimises the number of instances in use.
	random – Place tasks randomly.
	Random places tasks on instances at random yet still honours the other constraints that you specified, implicitly or explicitly. Specifically, it still makes sure that tasks are scheduled on instances with enough resources to run them.
	spread – Place tasks evenly based on the specified value. Accepted values are attribute key-value pairs, instanceId, or host.
	The Random task placement strategy is fairly straightforward as it doesn’t require further parameters. The two other strategies, such as binpack and spread, take opposite actions. Binpack places tasks on as few instances as possible, helping to optimise resource utilisation, while spread places tasks evenly across your cluster to help maximise availability. By default, ECS uses spread with the ecs.availability-zone attribute to place tasks.

- [ ] Lambda Best Practices
	 – Separate the Lambda handler (entry point) from your core logic.
	 – Take advantage of Execution Context reuse to improve the performance of your function
	 – Use AWS Lambda Environment Variables to pass operational parameters to your function.
	 – Control the dependencies in your function’s deployment package.
	 – Minimise your deployment package size to its runtime necessities.
	 – Reduce the time it takes Lambda to unpack deployment packages
	 – Minimise the complexity of your dependencies
	 – Avoid using recursive code

- [ ] Step Functions: States can perform a variety of functions in your state machine:
	- Task State – Do some work in your state machine
	- Choice State – Make a choice between branches of execution
	- Fail or Succeed State – Stop execution with failure or success
	- Pass State – Simply pass its input to its output or inject some fixed data, without performing work.
	- Wait State – Provide a delay for a certain amount of time or until a specified time/date.
	- Parallel State – Begin parallel branches of execution.
	- Map State – Dynamically iterate steps.

- [ ] KMS
	– Create symmetric and asymmetric keys where the key material is only ever used within the service
	– Create symmetric keys where the key material is generated and used within a custom key store under your control.
	– Import your own symmetric key for use within the service.
	– Create both symmetric and asymmetric data key pairs for local use within your applications.
	– Define which IAM users and roles can manage keys.
	– Define which IAM users and roles can use keys to encrypt and decrypt data.
	– Choose to have keys that were generated by the service to be automatically rotated on an annual basis.
	– Temporarily disable keys so they cannot be used by anyone.
	– Re-enable disabled keys.
	– Schedule the deletion of keys that you no longer use.
	– Audit the use of keys by inspecting logs in AWS CloudTrail.

- [ ] AWS Step Functions is a serverless function orchestrator that makes it easy to sequence AWS Lambda functions and multiple AWS services into business-critical applications. Through its visual interface, you can create and run a series of check pointed and event-driven workflows that maintain the application state. The output of one step acts as an input to the next. Each step in your application executes in order, as defined by your business logic.
	Task and Parallel states can have a field named Retry, whose value must be an array of objects known as retriers. An individual retrier represents a certain number of retries, usually at increasing time intervals.
	A retrier contains the following fields:
	ErrorEquals
		A non-empty array of strings that match error names. When a state reports an error, Step Functions scans through the retriers. When the error name appears in this array, it implements the retry policy described in this retrier.
	IntervalSeconds
		An integer that represents the number of seconds before the first retry attempt (1 by default).
	MaxAttempts
		A positive integer that represents the maximum number of retry attempts (3 by default). If the error recurs more times than specified, retries cease and normal error handling resumes. A value of 0 specifies that the error or errors are never retried.
	BackoffRate
		The multiplier by which the retry interval increases during each attempt (2.0 by default)
		Task and Parallel states can have a field named Catch. This field’s value must be an array of objects, known as catchers.
		A catcher contains the following fields.
	Next
		A string that must exactly match one of the state machine’s state names.
	ResultPath
		A path that determines what input is sent to the state specified in the Next field.
	
	When a state reports an error and either there is no Retry field, or if retries fail to resolve the error, Step Functions scans through the catchers in the order listed in the array. When the error name appears in the value of a catcher’s ErrorEquals field, the state machine transitions to the state named in the Next field.

- [ ] To perform a multipart upload with encryption using an AWS Key Management Service (AWS KMS) customer master key (CMK), the requester must have permission to the kms:Decrypt and kms:GenerateDataKey* actions on the key. These permissions are required because Amazon S3 must decrypt and read data from the encrypted file parts before it completes the multipart upload.

- [ ] AWS AppSync is quite similar with Amazon Cognito Sync which is also a service for synchronising application data across devices. It enables user data like app preferences or game state to be synchronised as well however, the key difference is that, it also extends these capabilities by allowing multiple users to synchronise and collaborate in real time on shared data.

- [ ] CodeDeployDefault.HalfAtATime is  is only applicable for EC2/On-premises compute platform and not for Lambda.

- [ ] Canary deployment method is not readily available in Elastic Beanstalk, but primarily to Lambda.

- [ ] Immutable deployment is only applicable in Elastic Beanstalk and not for Lambda.

- [ ] AWS Lambda compute platform deployments cannot use an in-place deployment type.

- [ ] In CodeDeploy, blue/green deployments only work with Amazon EC2 instances only.

- [ ] In Rolling deployments, only blue/green deployment is allowed if you used the AWS CodeDeploy service to deploy the new version of your application to ECS. Take note that in CodeDeploy, only the EC2/On-Premises compute platform can use both in-place deployments and blue/green deployment. For Lambda and ECS, you can only do a blue/green deployment in CodeDeploy. This type of deployment is actually done in Elastic Beanstalk for Multi-container docker environment which implicitly uses ECS.

- [ ] Code Deploy: Only deployments that use the EC2/On-Premises compute platform can use in-place deployments. AWS Lambda compute platform deployments cannot use an in-place deployment type.

- [ ] Blue/green deployment: The behaviour of your deployment depends on which compute platform you use:
	– Blue/green on an EC2/On-Premises compute platform: The instances in a deployment group (the original environment) are replaced by a different set of instances (the replacement environment). If you use an EC2/On-Premises compute platform, be aware that blue/green deployments work with Amazon EC2 instances only.
	– Blue/green on an AWS Lambda compute platform: Traffic is shifted from your current serverless environment to one with your updated Lambda function versions. You can specify Lambda functions that perform validation tests and choose the way in which the traffic shift occurs. All AWS Lambda compute platform deployments are blue/green deployments. For this reason, you do not need to specify a deployment type.
	– Blue/green on an Amazon ECS compute platform: Traffic is shifted from the task set with the original version of a containerized application in an Amazon ECS service to a replacement task set in the same service. The protocol and port of a specified load balancer listener are used to reroute production traffic. During deployment, a test listener can be used to serve traffic to the replacement task set while validation tests are run.

- [ ] Stage variables are not applied to the security definitions section of the API specification. For example, you cannot use different Amazon Cognito user pools for different stages.

- [ ] The CodeDeploy agent is a software package that, when installed and configured on an instance, makes it possible for that instance to be used in CodeDeploy deployments. The CodeDeploy agent communicates outbound using HTTPS over port 443.

- [ ] It is also important to note that the CodeDeploy agent is required only if you deploy to an EC2/On-Premises compute platform. The agent is not required for deployments that use the Amazon ECS or AWS Lambda compute platform.

- [ ] CloudFormation: For Node.js and Python functions, you can specify the function code inline in the template. Changes to a deployment package in Amazon S3 are not detected automatically during stack updates. To update the function code, change the object key or version in the template.

- [ ] There is no Canary deployment configuration in Elastic Beanstalk. This type of deployment strategy is usually used in Lambda.

- [ ] A CF template can include up to 8 sections: Description, Metadata, Parameters, Mappings, Conditions (test/prod), Transform (include snippet), Resources, Outputs

- [ ] AWS services that integrate with AWS KMS differ in their support for KMS keys. Some AWS services encrypt your data by default with an AWS owned key (owned by a AWS service) or an AWS managed key (you cannot rotate them). Some AWS services support customer managed keys (you can rotate them). Other AWS services support all types of KMS keys to allow you the ease of an AWS owned key, the visibility of an AWS managed key, or the control of a customer managed key.
      AWS KMS is replacing the term customer master key (CMK) with AWS KMS key and KMS key. The concept has not changed. To prevent breaking changes,        AWS KMS is keeping some variations of this term.

- [ ] AWS CodePipeline is a fully managed continuous delivery service that helps you automate your release pipelines for fast and reliable application and infrastructure updates. CodePipeline automates the build, test, and deploy phases of your release process every time there is a code change, based on the release model you define.

- [ ] AWS Cognito:
	- User pools are for authentication (identify verification). With a user pool, your app users can sign in through the user pool or federate through a third-party identity provider (IdP).
	- Identity pools are for authorisation (access control). You can use identity pools to create unique identities for users and give them access to other AWS services.

- [ ] Changes to a deployment package in Amazon S3 are not detected automatically during stack updates. To update the function code, change the object key or version in the template. docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-lambda-function-code.html
       The ZipFile property is only for node.js and python code, to include the code directly in CFn

- [ ] AWS X-Ray: Annotations are key-value pairs with string, number, or Boolean values. Annotations are indexed for use with filter expressions. Use annotations to record data that you want to use to group traces in the console, or when calling the GetTraceSummaries API.
       docs.aws.amazon.com/xray/latest/devguide/xray-sdk-python-segment.html

- [ ] AWS Secrets: In Java applications, you can use the Secrets Manager SQL Connection drivers to connect to MySQL, PostgreSQL, Oracle, and MSSQLServer databases using credentials stored in Secrets Manager. Each driver wraps the base JDBC driver, so you can use JDBC calls to access your database. However, instead of passing a username and password for the connection, you provide the ID of a secret. The driver calls Secrets Manager to retrieve the secret value, and then uses the credentials in the secret to connect to the database.
       docs.aws.amazon.com/secretsmanager/latest/userguide/retrieving-secrets_jdbc.html

- [ ] Elastic Beanstalk automatically handles the deployment, from capacity provisioning, load balancing, auto-scaling to application health monitoring. It allows smooth application upgrades (rolling, ...)

- [ ] Amazon Kinesis Data Firehose is an extract, transform (Lambda), and load service that reliably captures, transforms, and delivers streaming data to data lakes (S3), data stores (Redshift), and analytics services (OSS, Kinesis Data Analytics). 

- [ ] GenerateDataKey API: Using the KMS key ID, the client first sends a request to AWS KMS for a new symmetric encryption key that it can use to encrypt their object data. AWS KMS returns two versions of a randomly generated data key:
	- A plaintext version of the data key that the client uses to encrypt the object data.
	- A cipher blob of the same data key that the client uploads to Amazon S3 as object metadata.
        docs.aws.amazon.com/AmazonS3/latest/userguide/UsingClientSideEncryption.html

- [ ] Step Functions:
    The Map state can be used to run a set of steps for each element of an input array. While the Parallel state executes multiple branches of steps using the same input, a Map state will execute the same steps for multiple entries of an array in the state input.
    docs.aws.amazon.com/step-functions/latest/dg/amazon-states-language-map-state.html
    States are elements in your state machine that can perform a variety of functions:
        - Do some work in your state machine (a Task state)
        - Make a choice between branches of execution (a Choice state)
        - Stop an execution with a failure or success (a Fail or Succeed state)
        - Simply pass its input to its output or inject some fixed data (a Pass state)
        - Provide a delay for a certain amount of time or until a specified time/date (a Wait state)
        - Begin parallel branches of execution (a Parallel state)
        - Dynamically iterate steps (a Map state)

- [ ] CloudFormation:
    - The intrinsic function Ref returns the value of the specified parameter or resource.
    - The intrinsic function Fn::Join appends a set of values into a single value, separated by the specified delimiter. If a delimiter is the empty string, the set of values are concatenated with no delimiter.
    - The intrinsic function Fn::GetAZs returns an array that lists Availability Zones for a specified region in alphabetical order.
    - The cfn-init helper script reads template metadata from the AWS::CloudFormation::Init key and acts accordingly to fetch and parse metadata from CloudFormation, install packages, write files to disk, and enable/disable/start/stop services.
    - AWS::Region is a pseudo parameter returning a string representing the Region in which the encompassing resource is being created.
    - AWS::Include is a transform/macro hosted by CloudFormation

- [ ] DynamoDB: High-performance reads and writes are easy to manage with DynamoDB, and you can expect performance that is effectively constant across widely varying loads.

- [ ] SQS
    - VisibilityTimeout: the length of time during which a message will be unavailable after a message is delivered from the queue. Default is 30sec.
    - ReceiveMessageWaitTimeSeconds: when the wait time for the ReceiveMessage API action is greater than 0, long polling is in effect. The maximum long polling wait time is 20 seconds. Long polling helps reduce the cost of using Amazon SQS by eliminating the number of empty responses.
    - MessageRetentionPeriod: the number of seconds that Amazon SQS retains a message. Default is 4 days. Minimum is 1 min and Maximum is 14 days.
    - DelaySeconds: The time in seconds for which the delivery of all messages in the queue is delayed. Default is 0.
    - [ ] aws sts assume-role returns a set of temporary security credentials that you can use to access AWS resources that you might not normally have access to. These temporary credentials consist of an access key ID, a secret access key, and a security token. In this case, the developer will run the following commands as if he was the application to validate accesses.
    - [ ] A bucket policy is a resource-based policy that you can use to grant access permissions to your bucket and the objects in it. Only the bucket owner can associate a policy with a bucket. The permissions attached to the bucket apply to all of the objects in the bucket that are owned by the bucket owner. These permissions do not apply to objects owned by other AWS accounts.
       
	Use the Principal element in a resource-based JSON policy to specify the principal that is allowed or denied access to a resource. You can specify IAM users in the Principal element of a resource-based policy or in condition keys that support principals. "Principal": { "AWS": "arn:aws:iam::AWS-account-ID:user/user-name" }

- [ ] DynamoDB:
    ProvisionedThroughputExceededException can be caused by these issues:
    - A request rate greater than the provisioned throughput or on-demand account limits. 
    - Uneven distribution of data due to the wrong choice of partition key
    - Frequent access of the same key in a partition. This is the most frequent, also known as a hot key.
    Note that the AWS SDKs for DynamoDB automatically retry requests that receive this exception. Your request is eventually successful, unless your retry queue is too large to finish.

- [ ] You can share objects with others by creating a presigned URL, using the website IAM role security credentials, to grant time-limited permission to download the objects. With the AWS SDKs, the maximum expiration time for a presigned URL is 7 days from the time of creation.
- [ ] AWS X-Ray: The X-Ray SDK for Go is a set of libraries for Go applications that provide classes and methods for generating and sending trace data to the X-Ray daemon. Trace data includes information about incoming HTTP requests served by the application, and calls that the application makes to downstream services using the AWS SDK, HTTP clients, or an SQL database connector. You can also create segments manually and add debug information in annotations and metadata.
- [ ] A gateway response is identified by a response type defined by API Gateway. The response consists of an HTTP status code, a set of additional headers that are specified by parameter mappings, and a payload that is generated by a non-VTL (Apache Velocity Template Language) mapping template.

    You can set up a gateway response for a supported response type at the API level. Whenever API Gateway returns a response of the type, the header mappings and payload mapping templates defined in the gateway response are applied to return the mapped results to the API caller.
    The following are the Gateway response types which are associated with the HTTP 504 error in API Gateway:
    INTEGRATION_FAILURE – The gateway response for an integration failed error. If the response type is unspecified, this response defaults to the DEFAULT_5XX type.
    INTEGRATION_TIMEOUT – The gateway response for an integration timed out error. If the response type is unspecified, this response defaults to the DEFAULT_5XX type.
    For the integration timeout, the range is from 50 milliseconds to 29 seconds for all integration types, including Lambda, Lambda proxy, HTTP, HTTP proxy, and AWS integrations.
 

- [ ] Amazon SQS long polling is a way to retrieve messages from your Amazon SQS queues. While the regular short polling returns immediately, even if the message queue being polled is empty, long polling doesn’t return a response until a message arrives in the message queue or the long poll times out.
Long polling helps reduce the cost of using Amazon SQS by eliminating the number of empty responses (when there are no messages available for a ReceiveMessage request) and false empty responses (when messages are available but aren’t included in a response). This type of polling is suitable if the new messages that are being added to the SQS queue arrive less frequently.

    You can configure long polling to your SQS queue by simply setting the “Receive Message Wait Time” field to a value greater than 0.

- [ ] AWS X-Ray

    - [ ] Even with sampling, a complex application generates a lot of data. The AWS X-Ray console provides an easy-to-navigate view of the service graph. It shows health and performance information that helps you identify issues and opportunities for optimization in your application. For advanced tracing, you can drill down to traces for individual requests, or use filter expressions to find traces related to specific paths or users.

    When you instrument your application, the X-Ray SDK records information about incoming and outgoing requests, the AWS resources used, and the application itself. You can add other information to the segment document as annotations and metadata.
        - [ ] Annotations are simple key-value pairs that are indexed for use with filter expressions. Use annotations to record data that you want to use to group traces in the console, or when calling the GetTraceSummaries API. X-Ray indexes up to 50 annotations per trace.
        - [ ] Metadata are key-value pairs with values of any type, including objects and lists, but that are not indexed. Use metadata to record data you want to store in the trace but don’t need to use for searching traces. You can view annotations and metadata in the segment or subsegment details in the X-Ray console.Hence, adding the custom attributes as annotations in your segment document is the correct answer.
        - [ ] Including the custom attributes as new segment fields in the segment document is incorrect because a segment field can’t be used as a filter expression. You have to add the custom attributes as annotations to the segment document that you’ll send to X-Ray, just as mentioned above.
        - [ ] Creating a new sampling rule based on the custom attributes is incorrect because sampling is primarily used to ensure efficient tracing and to provide a representative sample of the requests that your application serves.
        - [ ] Adding the custom attributes as metadata in your segment document is incorrect because metadata is primarily used to record custom data that you want to store in the trace but not for searching traces.

- [ ] Lambda Alias: You can point an alias to a maximum of two Lambda function versions. In addition:
    *  Both versions must have the same IAM execution role.
    *  Both versions must have the same AWS Lambda Function Dead Letter Queues configuration, or no DLQ configuration.
    *  When pointing an alias to more than one version, the alias cannot point to $LATEST.

- [ ] ECS
    Port mappings allow containers to access ports on the host container instance to send or receive traffic. Port mappings are specified as part of the container definition which can be configured in the task definition.
    - For task definitions that use the awsvpc network mode, you should only specify the containerPort. The hostPort can be left blank or it must be the same value as the containerPort.
    - Port mappings on Windows use the NetNAT gateway address rather than localhost. There is no loopback for port mappings on Windows, so you cannot access a container’s mapped port from the host itself.
