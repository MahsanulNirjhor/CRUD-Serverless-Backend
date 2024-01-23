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
   
   Upon successful completion, the workflow will provide output that includes the deployed application's api endpoint URL and other relevant information.

9. **API Gateway endpoint:**
   
   Now Navigate to the repository in question and click on the "Actions" tab located near the top of the page.
   Locate the latest workflow you're and click on it. Click on the `deploy-dov` button and check the `Run sam deploy --no-confirm-changeset` stage, there you will find api endpoints for different paths. Here is the demo:

   **Endpoint** | **Description**
   ------- | --------
   **[https://xxxxxxxxxxx.execute-api.us-east-1.amazonaws.com/Prod/health](https://xxxxxxxxxxx.execute-api.us-east-1.amazonaws.com/Prod/health)** | To check if deployment was successful.
   **[https://xxxxxxxxxxx.execute-api.us-east-1.amazonaws.com/Prod/product](https://xxxxxxxxxxx.execute-api.us-east-1.amazonaws.com/Prod/product)** | To perform post, patch, get, delete actions.
   **[https://xxxxxxxxxxx.execute-api.us-east-1.amazonaws.com/Prod/products](https://xxxxxxxxxxx.execute-api.us-east-1.amazonaws.com/Prod/products)** | To perform get actions to view all data.
   
   ## Verifying Deployment Success

      Once you've deployed your serverless application using the provided instructions, you can verify its success by sending a GET request to the health check endpoint.

      **Endpoint:**

      [https://6wp4jo6t9h.execute-api.us-east-1.amazonaws.com/Prod/health](https://6wp4jo6t9h.execute-api.us-east-1.amazonaws.com/Prod/health)

      **Operation:**

      GET

      **Expected Response:**

      - **Status Code:** 200 OK
      - **Response Body:** A JSON object containing a success message:

      ```json
      {
      "message": "Deployment successful"
      }
      ```

      **Testing the Endpoint:**

      You can test the endpoint using tools like Postman or curl. Here's an example using curl:

      ```bash
      curl https://6wp4jo6t9h.execute-api.us-east-1.amazonaws.com/Prod/health
      ```

      **Response Interpretation:**

      - A 200 OK status code and the "Deployment successful" message confirm that your application is deployed and running successfully.



