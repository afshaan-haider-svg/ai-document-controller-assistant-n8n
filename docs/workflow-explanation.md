# Workflow Explanation

## Workflow Summary

The AI Document Controller Assistant workflow starts when a new email is received in Gmail.

The system checks whether the email contains a PDF attachment. If an attachment is found, the PDF is processed and analyzed using AI. If no attachment is found, the workflow creates a draft reply requesting the sender to resend the email with a PDF document.

## 1. Email Intake

The workflow starts with the Gmail Trigger node.

The system receives a new email and checks whether the email contains an attachment.

## 2. PDF Processing

If a PDF attachment is found, the workflow prepares the binary file and extracts text from the PDF.

## 3. AI Metadata Extraction

The AI Information Extractor reads the extracted PDF text and extracts important document control metadata.

Extracted fields include:

- Project name
- Project code
- Document type
- Discipline
- Document number
- Document title
- Revision
- Submitted by
- Submission date
- Status
- Priority

## 4. Missing Information Check

The workflow checks whether required fields are missing.

Required fields include:

- Project name
- Document type
- Discipline
- Document number
- Document title
- Revision

If any required field is missing, the workflow logs the issue and creates a Gmail draft reply.

## 5. Duplicate and Revision Check

The workflow reads the existing Document_Log sheet and checks whether the document already exists.

Duplicate checking is based on:

Document Number + Revision

## 6. Dynamic Google Drive Routing

The workflow selects the correct Google Drive folder based on document type.

Examples:

- MIR goes to 03_MIR
- WIR goes to 04_WIR
- RFI goes to 05_RFI
- Material Submittal goes to 07_Material_Submittals

## 7. Google Sheets Logging

The workflow updates different Google Sheets tabs:

- Document_Log
- Revision_History
- Missing_Info
- Approval_Status
- Email_Replies

## 8. Gmail Draft Replies

The workflow creates professional Gmail draft replies for:

- Successful document registration
- Duplicate document submission
- Missing information
- No attachment submission

## Final Result

The workflow automatically manages project document submissions and keeps document control records organized.