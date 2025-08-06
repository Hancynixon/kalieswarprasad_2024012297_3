Project Overview :
This project implements an automated data processing pipeline using a no-code/low-code tool (e.g., n8n). The pipeline validates, processes, and unifies data from five different Kaggle datasets. The key focus is on ensuring schema consistency, generating test data, and applying custom logic to transform records in a scalable and repeatable way.

atasets Used

The following public datasets from Kaggle are integrated in this workflow:

1. [Netflix Shows Dataset](https://www.kaggle.com/datasets/shivamb/netflix-shows)
2. [E-commerce Data](https://www.kaggle.com/datasets/carrie1/ecommerce-data)
3. [Human Resources Data](https://www.kaggle.com/datasets/rhuebner/human-resources-data-set)
4. [Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
5. [Heart Disease Dataset](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset)
Each dataset is ingested independently, processed, and then merged into a unified stream for further operations.


Workflow Structure

The flow consists of the following major components:

Webhook Trigger
- Accepts a POST request to start the workflow.

Extract & Parse Schema
- Extracts incoming schema and converts it into a usable format.

Rules Engine
- Applies basic schema rules or business logic for validation.

Generate Test Data
- Simulates or augments incoming records if needed.

Validation Agent
- Checks for missing fields, malformed entries, or invalid types.

Merge Nodes
- Combines all datasets (using append mode).
- Since merge nodes only accept 2 inputs at a time, multiple merges are chained logically.

Loop Over Items
- Iterates over each unified record for transformation or enrichment.

Code Nodes
- Custom logic is applied using JavaScript (or n8n expressions).

Replace Node & Final Code Block
- Placeholder for any final formatting or replacement logic.
- Outputs final formatted result.

 Webhook Response
- Sends the transformed response back to the client/API caller.

---



 How to Run This Workflow

1. Clone or download this workflow into your local or cloud n8n instance.
2. Make sure your n8n environment is authorized to access external files if needed.
3. Prepare and configure the webhook endpoint.
4. Use Postman, cURL, or another service to trigger the workflow.
5. Modify the rules/validation logic to suit your dataset needs.
6. Observe real-time data flow and debug as necessary.



Workflow Flowchart (Text Version)
Webhook
⮕ Trigger input received (via POST)

Extract Schema
⮕ Retrieves schema from input data

Parse Schema
⮕ Parses the extracted schema

Rules Node
⮕ Applies rule-based conditions or logic

Generate Test Data
⮕ Generates mock/test data for processing

Validation Agent
⮕ Validates test data using defined rules

Merge All Results
⮕ Consolidates validation output

Dataset Sampling Nodes

Netflix Sample Data

E-commerce Sample Data

Heart Disease Sample Data

HR Sample Data

Credit Card Fraud Data

Merge Nodes

Merge 1 = Netflix + E-commerce

Merge 2 = Heart Disease + HR

Merge 3 = Merge 1 + Merge 2

Merge 4 = Merge 3 + Credit Card Fraud Data

Loop Over Items
⮕ Iterates over merged data

Code Node
⮕ Performs custom processing on each item

Replace Me
⮕ Placeholder for transformation or replacement logic

Code1
⮕ Final post-processing logic

Respond to Webhook
⮕ Sends back response with processed data




