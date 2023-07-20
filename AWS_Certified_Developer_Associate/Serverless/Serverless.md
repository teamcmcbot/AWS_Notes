## Serverless Summary (Part 1)

### Serverless 101
- Serverless enables building scalable applications without managing servers.
- Serverless applications are events-driven and charged only when code executes.
- AWS handles infrastructure, allowing focus on writing code and building applications.

### Lambda
- Lambda is cost-effective, scales automatically, and is event-driven.
- Triggered by various services like DynamoDB, Kinesis, API Gateway, S3, etc.
- Each event triggers a single Lambda function, which is independent.

### API Gateway
- API Gateway provides an endpoint for applications running in AWS.
- It is serverless, low cost, scales automatically, and provides throttling.
- Logs API calls, latencies, and errors to CloudWatch.

### Version Control with Lambda
- `$latest` refers to the latest version of the uploaded Lambda code.
- Lambda versioning and aliases can be used to point to specific code versions.
- If using aliases, updates to code won't automatically reflect; aliases need manual updates.

### Lambda Concurrent Executions Limit
- Default limit: 1000 concurrent executions per second.
- Hitting the limit leads to invocations being rejected (429 HTTP status code).
- Request a limit increase from AWS support or use reserved concurrency for critical functions.

## Key Points - Serverless Summary (Part 2)

### Lambda and VPCs
- Lambda can access resources in a private VPC by providing VPC config info.
- Lambda creates an elastic network interface using a private subnet IP address.
- Security group permits Lambda function to access VPC resources.

### Step Functions
- Step Functions visualize and orchestrate serverless applications.
- Automatic triggering and tracking of each step in the state machine.
- Different types of workflows: standard (long-running) and express (short-lived).

### X-Ray
- X-Ray helps analyze and debug distributed applications.
- Provides service map and traces to troubleshoot connectivity and performance.
- Integrated with AWS services and can be used for custom applications.

### API Gateway Caching
- API Gateway caching improves performance by caching API call responses.
- Cached responses are returned for the Time To Live (TTL) period.
- Reduces API calls to the backend application, improving performance and latency.

### API Gateway Throttling and Advanced Features
- API Gateway has default limits for requests per second and concurrent requests.
- Throttling prevents API overload and returns a 429 error for exceeding limits.
- Advanced features: Import APIs using OpenAPI, configure as web service passthrough, or convert XML to JSON for legacy applications.

## Key Points - Serverless Summary (Part 3)

### Example Serverless Architectures
- Serverless architectures are event-driven and asynchronous.
- AWS services act as building blocks to create serverless applications.
- Loosely couple systems using SQS and EventBridge for flexibility and scalability.

### Example 1: Banking Application
- Customer withdrawal from ATM triggers Lambda via API Gateway.
- Lambda updates DynamoDB and triggers event for overdraft.
- EventBridge routes event to notify customer and start workflow in SQS.

### Example 2: Image Processing Application
- Customer uploads image to S3, triggering Lambda to process it.
- Lambda resizes image and stores processed data in S3 and DynamoDB.
- CloudFront serves processed images.

### Example 3: Social Media Data Processing Application
- Social media data loaded into Kinesis, consumed by Lambda.
- Lambda processes data, stores results in DynamoDB.
- Lambda integrated with X-Ray for monitoring.

### Lambda Data Storage
- /tmp: Used for temporary data (10GB limit).
- Lambda Layers: Store libraries/SDKs for function sharing (50MB zipped limit).
- External Storage Options: S3 (no size limit) and EFS (elastic and dynamic).

### Lambda Configuration
- Environment Variables: Adjust function behavior without code change.
- Configurable Parameters: Adjust various settings in the console.
- Deployment Package: Contains function code and dependencies (zipped if >50MB).

### Performance Tuning for Lambda
- Increase memory allocation to increase CPU capacity and reduce duration.
- Import only necessary libraries/SDKs to avoid initialization delay.
- Retry Mechanism: Lambda automatically retries failed invocations (2 retries).

### Dead Letter Queues and Lambda Destinations
- Configure DLQs to save failed invocations for further processing.
- Lambda Destinations: Configure destinations for successful/unsuccessful invocations.

### API Gateway Stages and Mock Endpoints
- API Gateway Stages reference lifecycle state of the API (e.g., dev, prod).
- Stage variables used to reference specific backend endpoints.
- Mock Endpoints: Simulate API responses for testing and debugging.

### API Gateway Response and Request Transformations
- Transform HTTP requests and responses using parameter mapping.
- Request Transformations: Change header, query string, or request path.
- Response Transformations: Change header or status code of API response.

