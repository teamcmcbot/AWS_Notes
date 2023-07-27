# CodePipeline
- Fully managed CI/CD service
- Ochestrates Build, Test & Deployment
    - Pipeline is triggered every time there is a change to your code.
- Automated
    - Fast, consistent, fewer mistakes. Enable quick release of new features and bug fixes.
- Integrates with AWS & 3rd party tools
    - CodeCommit, CodeBuild, CodeDeploy, Github, Jenkins, Elastic Beanstalk, CloudFormation, Lambda, Elastic Container Service

# AWS CodePipeline

* Visual Workflow to orchestrate your CICD
* Source – CodeCommit, ECR, S3, Bitbucket, GitHub
* Build – CodeBuild, Jenkins, CloudBees,TeamCity
* Test–CodeBuild,AWSDeviceFarm,3rd party tools,...
* Deploy – CodeDeploy, Elastic Beanstalk, CloudFormation, ECS, S3, ...
* Invoke – Lambda, Step Functions
* Consists of stages:
    * Each stage can have sequential actions and/or parallel actions
    * Example: Build ➔ Test ➔ Deploy ➔ Load Testing ➔ ...
    * Manual approval can be defined at any stage

# CodePipeline – Troubleshooting

* For CodePipeline Pipeline/Action/Stage Execution State Changes
    * Use CloudWatch Events (Amazon EventBridge). Example: 
        * You can create events for failed pipelines
        * You can create events for cancelled stages
    * If CodePipeline fails a stage, your pipeline stops, and you can get information in the console
    * If pipeline can’t perform an action, make sure the “IAM Service Role” attached does have enough IAM permissions (IAM Policy)
* AWS CloudTrail can be used to audit AWS API calls


# CodeStar
- <https://docs.aws.amazon.com/codestar/latest/userguide/welcome.html>
- AWS CodeStar is a cloud-based service for creating, managing, and working with software development projects on AWS. You can quickly develop, build, and deploy applications on AWS with an AWS CodeStar project. An AWS CodeStar project creates and integrates AWS services for your project development toolchain. Depending on your choice of AWS CodeStar project template, that toolchain might include source control, build, deployment, virtual servers or serverless resources, and more. AWS CodeStar also manages the permissions required for project users (called team members). By adding users as team members to an AWS CodeStar project, project owners can quickly and simply grant each team member role-appropriate access to a project and its resources.

# CodeArtifact
An artifact repository that makes it easy for developers to find the software packages they need.
## Artifact Repository
## Software Packages
## Including Open-Source
