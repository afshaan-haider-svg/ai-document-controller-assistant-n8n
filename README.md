

# AI Document Controller Assistant | n8n Automation Workflow

## Project Overview

AI Document Controller Assistant is an industry-based automation workflow designed for construction, engineering consultancy, and project documentation teams. The system automates document receiving, classification, metadata extraction, duplicate checking, revision tracking, Google Drive storage, Google Sheets logging, approval tracking, and Gmail draft replies.

This project simulates a real-world Document Controller workflow commonly used in construction projects, engineering consultancies, contractors, and QA/QC departments.

---

## Problem Statement

In construction and engineering projects, document controllers receive many emails containing drawings, RFIs, MIRs, WIRs, NCRs, material submittals, method statements, and transmittals. Manually checking attachments, extracting document information, updating registers, tracking revisions, and replying to senders takes time and can lead to errors.

This workflow solves that problem by using AI and automation.

---

## Key Features

* Automatically receives document emails through Gmail.
* Checks whether the email has an attachment.
* Extracts PDF text from attached documents.
* Uses AI to classify document type and extract metadata.
* Extracts project name, project code, document number, revision, discipline, title, submitted by, and status.
* Detects missing required information.
* Checks duplicate documents using document number and revision.
* Detects new revisions and updates revision history.
* Uploads documents to Google Drive with professional file naming.
* Routes files to the correct Google Drive folder based on document type.
* Updates Google Sheets document register.
* Updates approval tracking sheet.
* Creates professional Gmail draft replies for:

  * Successful document registration
  * Duplicate document submission
  * Missing information
  * No attachment submission
* Marks processed emails as read.

---

## Tech Stack

* n8n
* Gmail Trigger
* Gmail Draft Node
* Google Drive
* Google Sheets
* Extract From File Node
* AI Information Extractor
* Groq / LLM Model
* JavaScript Code Nodes

---

## Supported Document Types

* Drawing
* MIR
* WIR
* RFI
* NCR
* Material Submittal
* Method Statement
* Transmittal
* Invoice
* Contract Document
* Other

---

## Google Sheet Structure

The workflow uses a Google Sheet named:

AI Document Controller Register

Tabs:

1. Document_Log
2. Revision_History
3. Missing_Info
4. Approval_Status
5. Email_Replies

---

## Workflow Logic

1. Gmail Trigger receives a new email.
2. IF node checks whether an attachment exists.
3. PDF binary is prepared.
4. PDF text is extracted.
5. AI extracts document control metadata.
6. Required fields are validated.
7. Existing document register is checked.
8. Duplicate and revision logic is applied.
9. Google Drive folder is selected dynamically.
10. PDF is uploaded to the correct folder.
11. Document_Log is updated.
12. Approval_Status is updated.
13. Gmail draft reply is created.
14. Original email is marked as read.

---

## Duplicate and Revision Logic

The workflow checks the existing Google Sheet register using:

Document Number + Revision

Rules:

* Same document number and same revision means duplicate.
* Same document number with higher revision means new revision.
* Same document number with lower revision means old revision and manual review required.
* New document number means new document registration.

---

## Dynamic Folder Routing

Documents are automatically stored in Google Drive folders according to their type:

* Drawing → 02_Drawings
* MIR → 03_MIR
* WIR → 04_WIR
* RFI → 05_RFI
* NCR → 06_NCR
* Material Submittal → 07_Material_Submittals
* Method Statement → 08_Method_Statements
* Transmittal → 09_Transmittals
* Other → 01_Incoming_Documents

---

## Test Cases

The workflow was tested with the following scenarios:

1. New document registration
2. Duplicate document submission
3. New revision submission
4. Missing revision information
5. Email without attachment
6. RFI dynamic folder routing

---

## Real-World Use Case

This workflow can be used by:

* Document Controllers
* Engineering Consultants
* Construction Companies
* Contractors
* QA/QC Teams
* Project Management Teams
* Technical Offices

---

## Project Outcome

The system reduces manual document control work by automating repetitive tasks such as document logging, revision checking, file storage, and reply drafting. It improves accuracy, saves time, and creates a structured project document control process.

---

## Author

Afshaan Haider
BS Computer Science Student
AI Automation | n8n | AI Agents | Document Control Automation
