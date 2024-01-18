 # CRUD Serverless Backend with Python, AWS Lambda, DynamoDB, and API Gateway**

 ## Overview

This repository contains a serverless backend application that provides CRUD (Create, Read, Update, Delete) functionality for a data model of your choice. It's built using the following technologies:

- **Python:** The programming language used for Lambda functions.
- **AWS Lambda:** Serverless compute service for running code without provisioning or managing servers.
- **DynamoDB:** NoSQL database service for storing data.
- **API Gateway:** Service for creating, managing, and securing APIs.
- **Github Actions:** CI/CD workflow for automating builds, tests, and deployments.


## Getting Started

1. 
2. **Deployment Using GitHub Actions:**

   **To deploy the application using GitHub Actions, follow these steps:**

   2.1. 
   
   2.2. **Create secrets:**
      - In your forked repository's settings, navigate to the "Secrets" section.
      - Create the following secrets:
      - **BETA_KEY_ID:** Your AWS access key ID.
      - **BETA_ACCESS_KEY:** Your AWS secret access key.
      - **AWS_REGION:** The AWS region where you want to deploy the application (e.g., `us-east-1`).

   
   2.4.  **Creating the DynamoDB Table**

      **2.4.0. Before proceeding, ensure you have:**

      - An AWS account with appropriate permissions to create CloudFormation stacks and DynamoDB tables.
      - The AWS CLI installed and configured on your system.

      **2.4.1. Create the DynamoDB Table:**

         

      

      **2.4.2. Monitor Stack Creation:**

         ```
         aws cloudformation describe-stacks --stack-name MyDynamoDBStack
         ```

      Use this command to track the progress of the stack creation process. The output will display the stack status, which should eventually change to `CREATE_COMPLETE`.

      **2.4.3. Verify Table Creation:**

      Once the stack creation is complete, you can verify the existence of the DynamoDB table in the AWS Management Console or by using the AWS CLI:

         ```
         aws dynamodb list-tables
         ```

      **2.4.4. Updating the Table (Optional):**

      If you need to modify the table structure in the future, update the `dynamodb-template.yaml` file and re-run the `aws cloudformation create-stack` command with the `--update-stack` flag. This will update the existing stack with the new configuration.`


      **2.4.5. Trigger the workflow:**
      - Push a change to the `main` branch of your forked repository. This will automatically trigger the GitHub Actions workflow.

      **2.4.6 Monitor the workflow:**
      - Access the "Actions" tab in your repository to view the progress of the workflow.
      - The workflow will perform the following actions:
      - Build the application.
      - Deploy the application to AWS using CloudFormation.

      **2.4.7 View deployment details:**
      - Upon successful completion, the workflow will provide output that includes the deployed application's URL and other relevant information.

**Additional notes:**

- Ensure that your AWS account has the necessary permissions to deploy resources using CloudFormation.
- If you encounter any errors, review the workflow logs for more details.
- Consider customizing the workflow to suit your specific needs, such as adding additional testing steps or deploying to different environments.

4. **Configure environment variables:**
   - Create a `.env` file in the project root and add the following variables:
     ```
     REGION=your-aws-region
     DYNAMODB_TABLE_NAME=your-dynamodb-table-name
     STAGE_NAME=your-api-gateway-stage-name
     ```

6. **Deploy the application:**
   - Use the AWS SAM CLI to deploy the application:
     ```bash
     sam build
     sam deploy --guided
     ```

## Usage

- Interact with the API endpoints using tools like Postman or curl.
- Refer to the API documentation (if available) for specific endpoint details and usage examples.

## CI/CD Workflow

- The Github Actions workflow automatically builds, tests, and deploys the application upon pushes to the `main` branch.

## Additional Information

- **Data model:** Specify the model being managed by the CRUD functions.
- **API endpoints:** List the available API endpoints and their functionalities.
- **Testing:** Describe the testing strategy and any existing test cases.
- **Contributing:** Provide guidelines for contributing to the project.

