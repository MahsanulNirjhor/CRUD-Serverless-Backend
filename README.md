 # CRUD Serverless Backend with Python, AWS Lambda, DynamoDB, and API Gateway

 ## Overview

This repository contains a serverless backend application that provides CRUD (Create, Read, Update, Delete) functionality for a data model of your choice. It's built using the following technologies:

- **Python:** The programming language used for Lambda functions.
- **AWS Lambda:** Serverless compute service for running code without provisioning or managing servers.
- **DynamoDB:** NoSQL database service for storing data.
- **API Gateway:** Service for creating, managing, and securing APIs.
- **Github Actions:** CI/CD workflow for automating builds, tests, and deployments.

## Key Features

- Serverless architecture for scalability and cost-efficiency.
- CRUD functionality for interacting with data.
- API Gateway for exposing RESTful endpoints.
- CI/CD pipeline for automated deployments.

## Prerequisites:
   - An AWS account with appropriate permissions.
   - AWS CLI installed and configured.
   - Python 3.9 installed.


## Deployment Using GitHub Actions:
To deploy the application using GitHub Actions, follow these steps:
   
1. **Fork the repository:** Create a copy of this repository in your own GitHub account.

2. **Create secrets:**
   - In your forked repository's settings, navigate to the "Secrets" section.
   - Create the following secrets:
   - **BETA_KEY_ID:** Your AWS access key ID.
   - **BETA_ACCESS_KEY:** Your AWS secret access key.
   - **AWS_REGION:** The AWS region where you want to deploy the application (e.g., `us-east-1`).

3. **Clone the repository:**
   ```
   git clone https://github.com/<your-username>/CRUD-Serverless-Backend.git.git
   ```

   **Before proceeding, ensure you have:**

   - An AWS account with appropriate permissions to create CloudFormation stacks and DynamoDB tables.
   - The AWS CLI installed and configured on your system.
   - Open your terminal and run `cd CRUD-Serverless-Backend`

4. **Create the DynamoDB Table:**
   ```
      aws cloudformation create-stack \
      --stack-name MyDynamoDBStack \
      --template-body file://dynamodb-template.yaml \
      --capabilities CAPABILITY_AUTO_EXPAND
   ```
   
   Wait for 1 minute. This command will initiate the creation of the DynamoDB table based on the specifications defined in the `dynamodb-template.yaml` file.

5. **Verify Table Creation:**
   
   Once the stack creation is complete, you can verify the existence of the DynamoDB table in the AWS Management Console or by using the AWS CLI:

   ```
   aws dynamodb list-tables
   ```
6. **Updating the Table (Optional):**

   If you need to modify the table structure in the future, update the `dynamodb-template.yaml` file and re-run the `aws cloudformation create-stack` command with the `--update-stack` flag. This will update the existing stack with the new configuration.

7. **Trigger the workflow:**

   Push a change to the `main` branch of your forked repository. This will automatically trigger the GitHub Actions workflow.

8. **View deployment details:**
   
   Upon successful completion, the workflow will provide output that includes the deployed application's URL and other relevant information.



