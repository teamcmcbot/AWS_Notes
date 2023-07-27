# CodeCommit
- Centralized Code Repository based on git.
- Enables Collaboration
- Version Control

## Code Commit Repository
  ## Master Branch
  - source code
  - binaries
  - libraries

  ## Dev Branch 
  - source code
  - binaries
  - libraries

# CodeDeploy
- Automated deployment service
- Works on EC2, on-premises & Lambda
- Quickly release new feautures.
- Avoid downtime during deployments.
- Avoid risks associated with manual processes.

## CodeDeploy Deployment Approaches
  ## In-Place
  - Application is stopped on each instance and new release is installed.
  - Known as rolling update.
  
  ## Blue / Green
  - New instances are provisioned and the new release is installed on the new instances.
  - Blue represents the active deployment, green is the new release.

  ## Differences
  
    ### In-Place
    - Capacity is reduced during the deployment.
    - Lambda is not supported.
    - Rolling back involves a re-deploy. 
    - Great when deploying the first time.

    ### Blue / Green
    - No capacity reduction.
    - Green instances can be created ahead of time.
    - Easy to switch between old and new.
    - You pay for 2 environments until you terminate the old servers. 

## Appspec file
- Defines parameters to be used during a CodeDeploy deployment.
- For EC2 and on-prem system, YAML only.
- Lambda: YAML and JSON supported. File structure depends on whether you are deploying to Lambda or EC2.

  ## EC2 AppSpec File Structure
  - version
  - os
  - files
  - hooks 

  ## Scripts you might run during deployment
  - unzip files
  - run tests
  - deal with load balancing

  ### Configuration File
  - Defines the parameters to be used by CodeDeploy e.g. OS, files, hooks.
  
  ### appspec.yml
  - Saved to the root of your revision.
  - appspec.yml
  - /Scripts
  - /Config
  - /Source

  ### Hooks
  - Lifecycle event hooks have a specific run order
  - BeforeInstall
  - AfterInstall
  - ApplicationStart
  - ValidateService

## CodeDeploy Lifecycle event hooks
- `BeforeBlockTraffic`: Task to run before they are de-registered from load balancer
- `BlockTraffic`: De-register instance from a load balancer
- `AfterBlockTraffic`: Task to run on instance after they are de-registered from load balancer
- `ApplicationStop`: Gracefully stop the application
- `DownloadBundle`: CodeDeploy agent copies application revision files to a temp location.
- `BeforeInstall`: Pre-installation scripts, e.g. backup current version, decrypt files
- `Install`: Copy application files to final location
- `AfterInstall`: Post install scripts e.g. configuration, file permission
- `ApplicationStart`: Start any service what were stopped during ApplicationStop
- `ValidateService`: run test to validate the service.
- `BeforeAllowTraffic`: Task to run on instance before they are registered to LB.
- `AllowTraffic`: Register instance with a LB
- `AfterAllowTraffic`: Task to run on instance after they are registered to LB.

## CodeCommit vs GitHub, GitLab, Bitbucket...
- Git repositories can be expensive
- AWS CodeCommit:
  - Private Git reporsitories
  - No size limit on repositories (scale seamlessly)
  - Fully managed, highly available
  - Code only in AWS account -> increased security and compliance
  - Security (encrypted, access control...)
  - Integrated with Jenkins, AWS CodeBuild, and other CI tools


## CodeCommit – Security 

* Interactions are done using Git (standard)
* Authentication
    * SSH Keys – AWS Users can configure SSH keys in their IAM Console
    * HTTPS – with AWS CLI Credential helper or Git Credentials for IAM user
* Authorization
    * IAM policies to manage users/roles permissions to repositories
* Encryption
    * Repositories are automatically encrypted at rest using AWS KMS
    * Encrypted in transit (can only use HTTPS or SSH – both secure)
* Cross-account Access
    * **Do NOT share your SSH keys or your AWS credentials**
    * Use an IAM Role in your AWS account and use AWS STS (AssumeRole API)





