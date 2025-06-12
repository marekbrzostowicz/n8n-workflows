# SQL Query Workflow

**n8n workflow for automated SQL query processing with Google Sheets integration**

![Workflow Overview](https://github.com/user-attachments/assets/3e12bb1d-92ed-4495-8bbe-8ca07f0add94)

## Description

This workflow automates data extraction from Google Sheets, processes it through SQL queries, and delivers results. Designed for scheduled data operations and reporting workflows.

## Features

- **Google Sheets data extraction** - Seamless integration with Google Sheets API
- **SQL query execution** - Automated processing of complex database queries
- **Automated reporting** - Scheduled data operations and result delivery

## Installation

### 1. Import Workflow

1. Download the `workflow.json` file
2. In n8n, navigate to **File** → **Import** → **Select JSON** → **Import**

### 2. Configure Google OAuth

1. **Enable Google Sheets API** in Google Cloud Console
2. **Create OAuth 2.0 credentials**
3. **Add redirect URI**: 
   ```
   https://your-n8n-domain.com/callback
   ```
4. In n8n, **create connection** with Google OAuth2 API under **n8n Credentials**

### 3. Configure Workflow

**Update the required parameters in the workflow nodes to match your setup**

### 4. Configure HTML Interface

1. **Download** the `index.html` file
2. **Update the following in the file**:
   - **Webhook URL**: Replace with your n8n webhook URL
   - Update the form action:
     ```html
     <form
       action="https://your-webhook-url-here"
       method="GET"
       id="form"
     >
     ```
3. **Host the HTML file** on your web server or **open it locally**

## Form Configuration

![Form Interface](https://github.com/user-attachments/assets/e3e9416f-26af-41a5-9845-2dbc4f07c6e6)

### First Google Sheet ID

**Database Schema Sheet**

The first sheet must contain your database visualization in this **exact format**:

- **Table name** (as header)
- **Column names** (row headers)  
- **Data types** (for each column)

> **Note**: You can add multiple tables in the same sheet, but all tables must be from the same database.

![Database Schema Example](https://github.com/user-attachments/assets/9560762c-64b7-4865-8e86-4f382db258dc)

### Second Google Sheet ID  

**Results Output Sheet**

This sheet will contain the **execution results** from the workflow. The workflow will automatically populate this sheet with query results and processing logs.

![Results Sheet Example](https://github.com/user-attachments/assets/1ce7f2e0-6532-4965-9173-617de4a8961d)

## Additional Information

- **Supported databases**: Compatible with standard SQL databases
- **Scheduling**: Configure triggers in n8n for automated execution
- **Error handling**: Built-in error logging to results sheet
- **Security**: Uses OAuth 2.0 for secure Google Sheets access

## Troubleshooting

- Ensure Google Sheets API is enabled and properly configured
- Verify webhook URLs are correct and accessible
- Check that sheet IDs are valid and sheets are accessible
- Confirm database connection parameters are properly set
