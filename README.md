# Customer Complaints Classifier Using n8n and Google Gemini AI

## 1. Project Overview

The Customer Complaints Classifier is an AI-powered automation workflow built using **n8n** and **Google Gemini AI**.

The project is designed to automate the classification of customer complaints submitted through an online form. It uses a Large Language Model (LLM) to analyse submitted complaints and categorise them into predefined categories.

A key feature of the workflow is its ability to identify multiple complaint categories within a single customer submission rather than restricting each submission to just one category.

<img width="1164" height="490" alt="image" src="https://github.com/user-attachments/assets/8a3637ec-d666-408f-afc2-730e36d975d3" />

## 2. Project Objectives

The primary objectives of this project are to:

- Automate the classification of customer complaints.
- Use AI to understand and categorise customer-submitted feedback.
- Identify multiple complaint categories when a customer raises different issues in one submission.
- Reduce the need for manual complaint categorisation.

## 3. Tools and Technologies

| Tool | Purpose |
|---|---|
| n8n | Workflow automation and orchestration |
| Google Gemini AI | AI-powered complaint classification |
| n8n Form Trigger | Capturing customer complaint submissions |
| Basic LLM Chain | Processing complaints using an LLM |
| Google Gemini Chat Model | Providing the language model for classification |

## 4. Complaint Classification Categories

The workflow currently classifies customer complaints into four predefined categories:

1. **Billing:** Complaints relating to payments, incorrect charges, subscriptions, and billing discrepancies.
2. **Sales:** Complaints and enquiries relating to product purchases, pricing, product availability, and sales services.
3. **Technical:** Complaints relating to technical faults, system errors, product malfunctions, and difficulties using products or services.
4. **Others:** Complaints that do not fall under the Billing, Sales, or Technical categories.

The AI model is instructed to identify all applicable categories when a customer mentions multiple issues in a single submission.

## 5. Workflow Architecture

The current workflow consists of three main nodes, with Google Gemini Chat Model connected to the Basic LLM Chain.

**Workflow sequence:**

On Form Submission → Edit Fields → Basic LLM Chain

Google Gemini Chat Model is connected to the Basic LLM Chain through its Model input.

### 5.1 On Form Submission

The On Form Submission node serves as the workflow trigger.

It captures customer information and complaint details submitted through the n8n form.

The form collects the following information:

- Customer Name
- Customer Email
- Customer Complaint

### 5.2 Edit Fields

The Edit Fields node is used to organise the information received from the form submission.

The fields available after this stage include:

- Name
- Email
- Complaints
- submittedAt
- formMode

This makes the submitted complaint information available for subsequent processing.

### 5.3 Basic LLM Chain

The Basic LLM Chain is responsible for analysing and classifying the submitted customer complaints.

It receives the complaint text from the Edit Fields node and passes it to the connected Google Gemini Chat Model for processing.

The user prompt instructs the model to:

- Analyse the entire customer complaint.
- Identify all distinct issues mentioned.
- Classify the issues into the appropriate predefined categories.
- Return multiple categories when applicable.
- Avoid assigning categories that are not supported by the complaint.
- Return only the applicable category names, separated by commas.

### 5.4 Google Gemini Chat Model

The Google Gemini Chat Model provides the language model used by the Basic LLM Chain.

It processes the customer complaint based on the instructions supplied in the user prompt and generates the classification result.

## 6. Implementation and Testing

After configuring the workflow, test submissions were made through the customer complaint form to evaluate the classification functionality.

### Test Case 1: Single Complaint Category

**Customer submission:**

"I was debited twice yesterday."

**Expected output:**

Billing

**Actual output:**

Billing

**Result:** Successful.

### Test Case 2: Multiple Complaint Categories

**Customer submission:**

"I was debited twice yesterday for a transaction, and I also want to know how much it costs to purchase your premium package."

**Expected output:**

Billing, Sales

**Actual output:**

Billing, Sales

**Result:** Successful.

The second test confirmed that the AI model could identify multiple complaint categories from a single customer submission.

## 7. Current Project Status

The following components have been implemented and tested:

- Customer complaint form created using the n8n Form Trigger.
- Form fields configured to capture customer information and complaints.
- Edit Fields node configured to organise submitted information.
- Basic LLM Chain configured with a complaint classification prompt.
- Google Gemini Chat Model connected to the Basic LLM Chain.
- Single-category complaint classification tested successfully.
- Multiple-category complaint classification tested successfully.

## 8. Conclusion

The initial implementation of the Customer Complaints Classifier demonstrates how AI and workflow automation can be combined to simplify customer complaint categorisation.

By integrating n8n with Google Gemini AI, the workflow can receive customer complaints through a form, process the submitted text, and identify the appropriate complaint categories.

The successful test cases demonstrate that the classifier can handle both individual complaints and submissions containing multiple issues.

This implementation establishes the foundation of an AI-powered customer complaints classification workflow.

## 9. Author
Ibrahim Abdulrasaq
