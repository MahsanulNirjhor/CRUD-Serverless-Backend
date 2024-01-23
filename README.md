## CRUD Serverless Backend with Python, AWS Lambda, DynamoDB, and API Gateway

This project contains source code and supporting files for a serverless application with CRUD (Create, Read, Update, Delete) functionality that you can deploy with the Github Actions. Built with the power of serverless technologies, it delivers flexibility, scalability, and cost-effectiveness.

It includes the following files and folders.

### Key Features

* **Serverless architecture:** Leverages AWS Lambda to run code without managing servers, ensuring seamless scaling and cost optimization.
* **CRUD operations:** Create, read, update, and delete data in your chosen DynamoDB table through intuitive API endpoints.
* **RESTful API:** Exposes well-defined API endpoints for easy integration with your front-end applications.
* **Automated deployments:** CI/CD pipeline powered by GitHub Actions automates deployments for seamless updates and maintenance.

### Prerequisites

* AWS account with appropriate permissions
* AWS CLI installed and configured
* Python 3.9 installed

### Deployment with GitHub Actions

1. **Fork the repository:** Create a copy of this repository in your GitHub account.
2. **Create secrets:** Add the following secrets in your repository settings:
    * BETA_KEY_ID: Your AWS access key ID
    * BETA_ACCESS_KEY: Your AWS secret access key
    * AWS_REGION: The AWS region for deployment (e.g., `us-east-1`)
3. **Clone the repository:** Navigate to your terminal and run: `git clone https://github.com/<your-username>/CRUD-Serverless-Backend.git`
4. **Prepare for deployment:**
    * Ensure you have necessary permissions for CloudFormation stacks and DynamoDB tables.
    * Open your terminal and navigate to the `CRUD-Serverless-Backend` directory.
5. **Create the DynamoDB Table:** Execute: `aws cloudformation create-stack --stack-name MyDynamoDBStack --template-body file://dynamodb-template.yaml --capabilities CAPABILITY_AUTO_EXPAND`
    * Wait for a minute for table creation.
6. **Verify Table Creation:**
    * Check the AWS Management Console or use: `aws dynamodb list-tables`
7. **Update the Table (Optional):** Modify `dynamodb-template.yaml` and rerun the previous command with `--update-stack`.
8. **Trigger the workflow:** Push changes to your forked repository's `main` branch. The workflow will automatically run.
9. **View deployment details:** Navigate to the workflow in your repository to see deployment logs and API endpoint URLs.

### API References

**Verifying Deployment Success:**

The `health` endpoint confirms successful deployment:

* **Endpoint:** `https://[YOUR_DEPLOYMENT_URL]/Prod/health`
* **Operation:** GET
* **Expected Response:**
    * **Status Code:** 200 OK
    * **Response Body:** `{"message": "Deployment successful"}`

**Creating a Product:**

* **Endpoint:** `https://[YOUR_DEPLOYMENT_URL]/Prod/product`
* **Operation:** POST
* **Request Body:** JSON object with product details (e.g., `productId`, `color`, `price`)
* **Example Response:**
    * **Status Code:** 200 OK
    * **Response Body:** `{"Operation": "SAVE", "Message": "SUCCESS", "Item": {...product details...}}`

**Retrieving a Product:**

* **Endpoint:** `https://[YOUR_DEPLOYMENT_URL]/Prod/product`
* **Operation:** GET
* **Query Parameter:** `productId` (required)
* **Example Response:**
    * **Status Code:** 200 OK
    * **Response Body:** JSON object with product details for the specified `productId`

**Updating a Product:**

* **Endpoint:** `https://[YOUR_DEPLOYMENT_URL]/Prod/product`
* **Operation:** PATCH
* **Request Body:** JSON object with `productId`, `updateKey` (attribute to update), and `updateValue`
* **Example Response:**
    * **Status Code:** 200 OK
    * **Response Body:** Details about the updated attribute and its new value

**Deleting a Product:**

* **Endpoint:** `https://[YOUR_DEPLOYMENT_URL]/Prod/product`
* **Operation:** DELETE
* **Request Body:** JSON object with `productId` (required)
* **Example Response:**
    * **Status Code:** 200 OK
    * **Response Body:** Details about the deleted product

**Retrieving All Products:**

* **Endpoint:** `https://[YOUR_DEPLOYMENT_URL]/Prod/products`
* **Operation:** GET
* **Expected Response:**
    * **Status Code:** 200 OK
    * **Response Body:** JSON array containing objects with details of all products in the table (e.g., `productId`, `color`, `price`)

**Error Handling:**

* Each API endpoint returns appropriate status codes and error messages for various scenarios (e.g., invalid requests, missing data, internal errors). Refer to the AWS documentation for specific code meanings.

**Additional Resources:**

* AWS Lambda Documentation: [https://docs.aws.amazon.com/lambda/](https://docs.aws.amazon.com/lambda/)
* DynamoDB Documentation: [https://docs.aws.amazon.com/dynamodb/](https://docs.aws.amazon.com/dynamodb/)
* API Gateway Documentation: [https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html)

**Contributing:**

We welcome contributions to improve this project! Feel free to fork the repository, raise issues, and submit pull requests with enhancements or bug fixes.
