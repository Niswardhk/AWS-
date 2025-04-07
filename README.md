Serverless Inventory Management System with AWS Lambda and DynamoDB
This is a Serverless Inventory Management System built using AWS serverless services. The project demonstrates how to manage inventory items efficiently with a web interface, leveraging AWS Lambda for backend logic, DynamoDB for data storage, and API Gateway for API management. Features include adding, editing, deleting, viewing, and managing inventory items with a simple and intuitive user interface.
Project Overview
Frontend: Built with HTML, CSS, and JavaScript (index.html), providing a responsive web interface for inventory management.

Includes a form to add new items, a table to display inventory, and buttons for reading and deleting items.
Uses Axios for making HTTP requests to the backend API.
Backend: Implemented with Python in lambda_function.py using AWS Lambda.

Handles API endpoints for CRUD operations (/add-item, /get-item, /get-all-items, /update-item, /delete-item), serving the frontend (/), populating data (/populate), and managing the favicon (/favicon.ico).
Includes error handling, logging, and a helper function to handle DynamoDB Decimal serialization.
Database: Stores inventory data in a DynamoDB table (InventoryTable).

Configured with itemID as the partition key.
Supports scalable storage for inventory items with attributes like itemID, itemName, quantity, and price.
Deployment: Hosted via AWS API Gateway.

Exposes the Lambda function as RESTful endpoints with CORS enabled for cross-origin requests.
Deployed to a dev stage with the Invoke URL: https://mo1eyckg8c.execute-api.us-east-1.amazonaws.com/dev.
How to Use
Deploy the Lambda Function:
Package lambda_function.py, index.html, and favicon.ico into a zip file (inventory_lambda.zip).
Upload the zip file to the InventoryFunction in the AWS Lambda console and deploy it.
Set Up the API Gateway:
Create an API Gateway (InventoryAPI) with resources for /, /populate, /favicon.ico, /add-item, /get-item, /get-all-items, /update-item, and /delete-item.
Configure each resource with a GET or POST method linked to the InventoryFunction.
Enable CORS for all resources and deploy the API to the dev stage.
Populate the DynamoDB Table with Sample Data:
Use the /populate endpoint (e.g., https://mo1eyckg8c.execute-api.us-east-1.amazonaws.com/dev/populate) to add 100 random inventory items to the InventoryTable.
Verify the data in the DynamoDB console under InventoryTable → “Items” tab.
Access the Inventory Interface:
Open the API URL in a browser: https://mo1eyckg8c.execute-api.us-east-1.amazonaws.com/dev/.
The index.html page will load, displaying the inventory table and allowing CRUD operations.
Demo Video
Check out the video tutorial for this project: [Insert Video Link Here]

Description: This video (to be created) will walk through the deployment process, demonstrate CRUD operations, and show how to troubleshoot common issues using CloudWatch logs. [Note: Since I cannot create a video, you can record a demo using screen recording software like OBS Studio or Camtasia, following the steps in the “How to Use” section.]
Future Enhancements
Add User Authentication with AWS Cognito:
Implement user login and authentication to restrict access to authorized users only.
Integrate Cognito for user management and secure API access.
Implement Advanced Search Using DynamoDB Indexes:
Add global secondary indexes (GSI) to InventoryTable for searching by itemName or price range.
Enhance the frontend with a search bar to filter inventory items.
Integrate AWS S3 for File Storage:
Store images or detailed item descriptions in an S3 bucket.
Update the frontend to upload and display these files.
Add Export to CSV Functionality:
Extend the backend to generate a CSV file of the inventory data.
Add a download button to the frontend to export the data.
