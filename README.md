# Automated-S3-Static-Website-Deployment-Pipeline
This project automates the deployment of static websites hosted on Amazon S3 whenever code is committed to a specific branch in an AWS CodeCommit repository. The approach provides a central deployment pipeline that can be easily extended to include features such as code reviews, builds, and tests.


```markdown
# S3 Static Website Automated Deployments

## Overview

This project automates the deployment of static websites hosted on Amazon S3 whenever code is committed to a specific branch in an AWS CodeCommit repository. The approach provides a central deployment pipeline that can be easily extended to include features such as code reviews, builds, and tests.

## Architecture

The deployment workflow is structured as follows:

```
CodeCommit -> CodePipeline -> Lambda -> S3 Static Website
```

### Technologies Used

- **AWS CodeCommit**: Source control service that hosts the code repository.
- **AWS CodePipeline**: Continuous integration and continuous delivery (CI/CD) service that automates the build, test, and deployment phases.
- **AWS Lambda**: Serverless compute service that runs code in response to events, utilized here as a custom action in CodePipeline.
- **Amazon S3**: Storage service for hosting the static website.
- **Node.js**: JavaScript runtime used for developing the Lambda function.

## Features

- **Automated Deployments**: Automatically deploy your static website to S3 whenever changes are pushed to the specified branch in CodeCommit.
- **Custom Lambda Function**: The deployment process is managed by a Lambda function, ensuring efficient and scalable operations.
- **Centralized Pipeline**: Easily extend the deployment pipeline to include additional stages such as testing and code reviews.

## Setup Instructions

### Prerequisites

- An AWS account with programmatic access.
- AWS CLI installed and configured.
- An S3 bucket in the `us-east-1` region (CodeCommit is currently only available here).

### Installation Steps

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/alexgibs/StaticS3Deploy.git
   ```

2. **Navigate to the Project Directory**:
   ```bash
   cd StaticS3Deploy.git
   ```

3. **Install Dependencies**:
   Install the necessary dependencies for the Lambda function:
   ```bash
   npm install
   ```

4. **Package the Lambda Function**:
   Create a zip archive of the required files for the Lambda function:
   ```bash
   zip -r StaticS3SiteDeploy.zip index.js node_modules/
   ```

5. **Upload the Lambda Function Zip to S3**:
   Upload the zip archive to an S3 bucket in the `us-east-1` region:
   ```bash
   aws s3 cp StaticS3SiteDeploy.zip s3://<your-bucket> --region us-east-1
   ```

6. **Deploy the CloudFormation Stack**:
   Deploy the CloudFormation stack in `us-east-1` using the provided `codepipeline.json` template to set up the pipeline and Lambda function.

### Caveats

- The Lambda function extracts the output artifact from CodeCommit to the `/tmp` directory, which has a 512 MB limit. If your codebase exceeds this size, consider modifying the function to handle individual files instead of extracting all at once.

## Skills and Learning Outcomes

Through this project, I gained valuable experience and skills, including:

- **AWS Cloud Services**: Deepened my understanding of key AWS services and how they interact in a CI/CD pipeline.
- **Automation**: Developed automation skills by creating a deployment pipeline that reduces manual intervention.
- **Serverless Computing**: Learned to leverage AWS Lambda for executing code in response to events without managing servers.
- **Infrastructure as Code**: Gained experience in using AWS CloudFormation to provision infrastructure efficiently.
- **Problem-Solving**: Addressed limitations of serverless architectures and optimized deployment processes.

## Conclusion

This project provides an efficient way to automate static website deployments on Amazon S3, showcasing my proficiency in AWS services and CI/CD practices. By implementing this automation, I can focus on development and enhancement rather than manual deployment processes.

For any questions or contributions, feel free to reach out!

```

This README provides a clear overview of the project, highlights the technologies used, explains how to set it up, and emphasizes the skills you learned throughout the process. Let me know if you’d like any adjustments!
