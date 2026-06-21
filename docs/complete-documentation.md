# AI Document Controller Assistant - Complete Documentation

## 1. Project Title

AI Document Controller Assistant using n8n

## 2. Project Overview

AI Document Controller Assistant is an industry-based automation workflow built using n8n, Gmail, Google Drive, Google Sheets, and AI.

This agent is designed for construction companies, engineering consultants, contractors, QA/QC teams, and document control departments. It automates the process of receiving project documents through email, checking attachments, extracting PDF text, identifying document metadata using AI, checking duplicates and revisions, uploading files to the correct Google Drive folder, updating Google Sheets registers, creating approval tracking records, generating Gmail draft replies, and marking processed emails as read.

The main purpose of this project is to reduce repetitive manual document control work and improve accuracy in project documentation.

## 3. Problem Statement

In construction and engineering projects, document controllers receive a large number of documents every day through email.

These documents may include:

* Material Submittals
* RFIs
* MIRs
* WIRs
* NCRs
* Drawings
* Method Statements
* Transmittals
* Invoices
* Contract Documents

The manual document control process usually includes:

* Opening the email
* Checking whether a PDF document is attached
* Downloading the attachment
* Reading the PDF
* Finding project name
* Finding document number
* Finding revision number
* Identifying document type
* Identifying discipline
* Checking whether the document is duplicate
* Checking whether it is a new revision
* Renaming the file
* Uploading it to the correct folder
* Updating the document register
* Updating revision history
* Updating approval status
* Preparing reply emails

Doing all these tasks manually takes time and can create errors.

This workflow automates the first stage of document control using AI and automation.

## 4. Main Objective

The main objective of this project is to build an AI-powered document control assistant that can automatically process incoming project documents and support document controllers in their daily work.

The workflow helps to:

* Save time
* Reduce manual errors
* Improve document tracking
* Maintain revision history
* Organize files properly
* Generate professional draft replies
* Keep Google Sheets registers updated

## 5. Tools and Technologies Used

## n8n

n8n is used as the automation platform. It connects Gmail, AI model, Google Drive, Google Sheets, and custom JavaScript logic.

## Gmail

Gmail is used to receive document submission emails and create draft replies.

## Google Drive

Google Drive is used to store documents in proper folders according to document type.

## Google Sheets

Google Sheets is used as a digital document control register.

## AI Information Extractor

AI Information Extractor is used to classify the document and extract metadata from PDF text.

## Groq Chat Model

Groq Chat Model is used as the AI model connected with the Information Extractor.

## Extract From File Node

This node is used to extract readable text from PDF attachments.

## JavaScript Code Nodes

Code nodes are used for data normalization, duplicate checking, revision checking, folder routing, reply preparation, and Gmail message ID preparation.

## 6. Who Can Use This Agent

This AI Document Controller Assistant can be used by:

* Document Controllers
* Engineering Consultants
* Construction Companies
* Contractors
* QA/QC Teams
* Project Management Teams
* Technical Office Teams
* Admin Teams
* Site Engineers
* Project Coordinators
* Companies managing large document submissions

## 7. Benefits of This Agent

## Time Saving

The agent reduces the time spent on manual document checking, logging, uploading, and reply drafting.

## Accuracy Improvement

AI extracts metadata and the workflow validates important fields, reducing human mistakes.

## Better Document Organization

Documents are automatically routed to the correct Google Drive folder based on document type.

## Duplicate Control

The workflow checks existing records and prevents the same document revision from being uploaded again.

## Revision Tracking

If a new revision is submitted, the workflow adds it to Revision_History and keeps proper tracking.

## Professional Communication

The workflow creates professional Gmail draft replies for successful registration, duplicate documents, missing information, and no attachment cases.

## Centralized Register

All document records are saved in Google Sheets tabs, making the process easy to monitor.

## Real-World Industry Use

The workflow follows a practical construction document control process.

## 8. Supported Document Types

The agent supports the following document types:

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

## 9. Google Drive Folder Structure

The workflow uses the following Google Drive folder structure:

* 01_Incoming_Documents
* 02_Drawings
* 03_MIR
* 04_WIR
* 05_RFI
* 06_NCR
* 07_Material_Submittals
* 08_Method_Statements
* 09_Transmittals
* 10_Rejected_or_Missing_Info
* 11_Approved_Documents

## 10. Google Sheets Register Structure

The workflow uses one Google Sheet named:

AI Document Controller Register

It contains five main tabs:

## 10.1 Document_Log

This is the main document register.

Columns:

* Log_ID
* Date_Received
* Time_Received
* Project_Name
* Project_Code
* Document_Type
* Discipline
* Document_Number
* Document_Title
* Revision
* Submitted_By
* Sender_Email
* Status
* Priority
* File_Name
* New_File_Name
* Google_Drive_Link
* Review_Due_Date
* Days_Pending
* Duplicate_Check
* Latest_Revision
* AI_Remarks
* Action_Required
* Created_By

Purpose:

This tab stores all successfully registered documents.

## 10.2 Revision_History

Columns:

* History_ID
* Document_Number
* Document_Title
* Old_Revision
* New_Revision
* Previous_Status
* New_Status
* Received_Date
* Updated_Date
* Submitted_By
* Remarks

Purpose:

This tab stores old and new revision records.

## 10.3 Missing_Info

Columns:

* Missing_ID
* Date_Received
* Sender_Email
* Document_Title
* File_Name
* Missing_Fields
* Issue_Type
* AI_Message
* Draft_Status

Purpose:

This tab stores submissions where required information is missing.

## 10.4 Approval_Status

Columns:

* Approval_ID
* Document_Number
* Document_Title
* Revision
* Document_Type
* Discipline
* Submitted_By
* Review_Status
* Reviewer
* Received_Date
* Due_Date
* Approved_Date
* Remarks

Purpose:

This tab tracks approval and review status.

## 10.5 Email_Replies

Columns:

* Reply_ID
* Date
* Sender_Email
* Subject
* Document_Number
* Reply_Type
* AI_Draft_Message
* Status

Purpose:

This tab stores records of all Gmail draft replies created by the workflow.

## 11. High-Level Workflow

The workflow follows this process:

Gmail Trigger
→ Check Attachment
→ Prepare PDF Binary
→ Extract PDF Text
→ AI Metadata Extraction
→ Normalize AI Output
→ Missing Information Check
→ Duplicate and Revision Check
→ Dynamic Folder Routing
→ Google Drive Upload
→ Google Sheets Logging
→ Approval Status Tracking
→ Gmail Draft Reply
→ Mark Email as Read

## 12. Detailed Node-by-Node Explanation

## 12.1 Gmail Trigger - Receive Document Email

Actual Node Type:

Gmail Trigger

Working:

This node listens for new incoming emails in Gmail. Whenever a new document submission email is received, the workflow starts automatically.

Why Used:

This is the starting point of the workflow. In real document control systems, documents are usually submitted through email, so Gmail Trigger is used to automatically capture incoming document submissions.

Output:

The node provides:

* Email ID
* Sender details
* Subject
* Email body
* Attachment information
* Binary attachment data if download attachment is enabled

## 12.2 Check Attachment Available

Actual Node Type:

IF Node

Working:

This node checks whether the incoming email contains an attachment.

Condition checks whether binary data exists.

If attachment exists:

The workflow continues to PDF processing.

If attachment does not exist:

The workflow goes to the no-attachment reply branch.

Why Used:

A document control submission must include an actual document file. If no PDF is attached, the workflow should not continue with AI extraction or Google Drive upload.

Branches:

True branch:

PDF found.

False branch:

No attachment found.

## 12.3 Prepare PDF Binary

Actual Node Type:

Code Node

Working:

This node checks the binary attachments and finds the PDF file. It standardizes the binary file name to `data` so that the next PDF extraction node can process it correctly.

Why Used:

Gmail may provide attachment binary names such as `attachment_0` or another dynamic name. The Extract From File node needs a fixed binary field name. This node solves that issue by renaming the selected PDF binary to `data`.

Output:

* Original file name
* PDF mime type
* Standard binary field named `data`

## 12.4 Extract PDF Text

Actual Node Type:

Extract From File

Operation:

Extract From PDF

Working:

This node extracts readable text from the attached PDF document.

Why Used:

AI cannot classify or extract document metadata unless the PDF content is converted into text. This node prepares the raw text for AI processing.

Output:

Extracted PDF text.

## 12.5 AI Extract Document Metadata

Actual Node Type:

AI Information Extractor

Connected Model:

Groq Chat Model

Working:

This node reads the extracted PDF text and extracts structured document control metadata.

Extracted fields include:

* Project name
* Project code
* Document type
* Discipline
* Document number
* Document title
* Revision
* Submitted by
* Sender company
* Submission date
* Status
* Priority
* Missing fields
* Duplicate key
* New file name
* AI remarks
* Action required

Why Used:

Manual extraction of document details is time-consuming. AI makes this process faster and more intelligent.

## 12.6 Groq Chat Model

Actual Node Type:

Groq Chat Model

Working:

This model provides AI capability to the Information Extractor.

Why Used:

The AI model helps classify document type and extract metadata from unstructured PDF text.

Recommended Setting:

Temperature should be low, preferably 0, so the output remains stable and consistent.

## 12.7 Normalize AI Metadata

Actual Node Type:

Code Node

Working:

This node cleans and normalizes AI output.

It prepares:

* Log ID
* Date received
* Time received
* Review due date
* New file name
* Duplicate key
* Status
* Priority
* Created by field

Why Used:

AI output can vary slightly. Before saving data into Google Sheets, it is important to normalize the values.

Output:

Clean JSON object ready for validation and logging.

## 12.8 Check Missing Required Information

Actual Node Type:

IF Node

Working:

This node checks whether required fields are missing.

Required fields:

* Project name
* Document type
* Discipline
* Document number
* Document title
* Revision

If missing information exists:

The workflow goes to the missing information branch.

If information is complete:

The workflow continues to duplicate and revision checking.

Why Used:

A document should not be registered if key document control fields are missing.

## 12.9 Get Existing Document Register

Actual Node Type:

Google Sheets Node

Operation:

Get Row(s)

Working:

This node reads all existing rows from the Document_Log tab.

Why Used:

The workflow needs previous document records to detect duplicate submissions and new revisions.

Output:

Existing document register rows.

## 12.10 Check Duplicate and Revision

Actual Node Type:

Code Node

Working:

This node compares the current document with existing records.

Logic:

* Same document number and same revision = Duplicate
* Same document number and higher revision = New revision
* Same document number and lower revision = Old revision
* New document number = New document

Why Used:

Duplicate and revision tracking is one of the most important parts of document control.

Output:

* Duplicate check status
* Latest revision status
* Previous latest revision
* Exact duplicate found
* Revision status
* Action required

## 12.11 Set Target Drive Folder

Actual Node Type:

Code Node

Working:

This node selects the correct Google Drive folder based on document type.

Folder mapping examples:

* RFI → 05_RFI
* MIR → 03_MIR
* WIR → 04_WIR
* Material Submittal → 07_Material_Submittals
* Drawing → 02_Drawings
* NCR → 06_NCR

Why Used:

In real projects, documents are stored in separate folders based on category. This node automates folder routing.

Output:

* Target folder name
* Target folder ID

## 12.12 Check Duplicate Document

Actual Node Type:

IF Node

Working:

This node checks whether the document is an exact duplicate.

Condition:

If exact_duplicate_found is Yes, the workflow goes to duplicate handling.

If No, the workflow continues.

Why Used:

Duplicate files should not be uploaded again or logged again.

## 12.13 Check New Revision

Actual Node Type:

IF Node

Working:

This node checks whether the document is a new revision.

If duplicate_check is New Revision:

The workflow updates Revision_History.

If not:

The workflow treats it as a new document.

Why Used:

New revisions must be tracked separately in document control.

## 12.14 Append Revision History

Actual Node Type:

Google Sheets Node

Operation:

Append Row

Working:

This node adds a revision record to the Revision_History tab.

Why Used:

Revision history is important to track document updates over time.

Saved data includes:

* Old revision
* New revision
* Document title
* Submitted by
* Remarks

## 12.15 Reattach PDF Binary

Actual Node Type:

Code Node

Working:

This node reattaches the original PDF binary file before uploading to Google Drive.

Why Used:

Some AI and Google Sheets nodes pass only JSON data and may not keep binary data. Google Drive upload needs the PDF binary. This node restores the binary file.

## 12.16 Upload Document to Google Drive

Actual Node Type:

Google Drive Node

Operation:

Upload File

Working:

This node uploads the PDF file to the selected Google Drive folder.

Important fields:

* Input binary field: data
* File name: new_file_name
* Parent folder: target_folder_id

Why Used:

This stores project documents in an organized cloud folder system.

## 12.17 Prepare Sheet Row With Drive Link

Actual Node Type:

Code Node

Working:

This node prepares the final document log data after file upload.

It adds:

* Google Drive file ID
* Google Drive link
* Uploaded file name

Why Used:

The Document_Log sheet should include the Google Drive link for easy access.

## 12.18 Append Document Log

Actual Node Type:

Google Sheets Node

Operation:

Append Row

Working:

This node adds a new row to the Document_Log sheet.

Why Used:

This is the main register entry for each successfully registered document.

## 12.19 Prepare Approval Status Row

Actual Node Type:

Code Node

Working:

This node prepares approval tracking data.

It creates:

* Approval ID
* Document number
* Revision
* Review status
* Reviewer
* Due date
* Remarks

Why Used:

Every registered document should have approval or review tracking.

## 12.20 Append Approval Status

Actual Node Type:

Google Sheets Node

Operation:

Append Row

Working:

This node adds a row to the Approval_Status sheet.

Why Used:

It helps track document review progress.

Default review status:

Pending Review

## 12.21 Prepare Registered Reply

Actual Node Type:

Code Node

Working:

This node prepares a professional confirmation message for successful document registration.

The message includes:

* Project name
* Document number
* Revision
* Document title
* Document type
* Discipline
* Review due date
* Google Drive link

Why Used:

The workflow should communicate back to the sender that the document has been received and registered.

## 12.22 Log Registered Reply

Actual Node Type:

Google Sheets Node

Operation:

Append Row

Working:

This node logs the registered reply into the Email_Replies sheet.

Why Used:

It keeps a record of all draft replies created by the workflow.

## 12.23 Create Registered Draft Reply

Actual Node Type:

Gmail Node

Resource:

Draft

Operation:

Create

Working:

This node creates a Gmail draft reply for successful document registration.

Why Used:

The workflow prepares a professional reply but does not send it automatically. This allows human review before sending.

## 12.24 Prepare Duplicate Reply

Actual Node Type:

Code Node

Working:

This node prepares the email response for duplicate submissions.

Message explains that the same document number and revision already exist in the register.

Why Used:

Duplicate submissions should be acknowledged professionally without uploading again.

## 12.25 Log Duplicate Reply

Actual Node Type:

Google Sheets Node

Operation:

Append Row

Working:

This node logs duplicate reply details into the Email_Replies sheet.

Why Used:

It keeps a communication record.

## 12.26 Create Duplicate Draft Reply

Actual Node Type:

Gmail Node

Resource:

Draft

Operation:

Create

Working:

This node creates a Gmail draft reply for duplicate document submission.

Why Used:

It informs the sender that the document already exists and does not need to be uploaded again.

## 12.27 Prepare Missing Info Reply

Actual Node Type:

Code Node

Working:

This node prepares a reply message when required information is missing.

It includes:

* Missing fields
* Document title
* Document number
* Revision
* Project name

Why Used:

The sender needs to know what information is missing before the document can be registered.

## 12.28 Append Missing Info Log

Actual Node Type:

Google Sheets Node

Operation:

Append Row

Working:

This node logs incomplete submissions into the Missing_Info sheet.

Why Used:

It helps track documents that could not be registered due to missing data.

## 12.29 Create Missing Info Draft Reply

Actual Node Type:

Gmail Node

Resource:

Draft

Operation:

Create

Working:

This node creates a Gmail draft reply requesting the missing information.

Why Used:

The workflow should not register incomplete documents. It requests correction from the sender.

## 12.30 Prepare No Attachment Reply

Actual Node Type:

Code Node

Working:

This node prepares a reply when the email has no attachment.

Why Used:

If no PDF is attached, the workflow cannot process the document.

## 12.31 Create No Attachment Draft Reply

Actual Node Type:

Gmail Node

Resource:

Draft

Operation:

Create

Working:

This node creates a Gmail draft asking the sender to resend the email with a PDF attachment.

Why Used:

This handles emails that contain document details but no actual file.

## 12.32 Log No Attachment Reply

Actual Node Type:

Google Sheets Node

Operation:

Append Row

Working:

This node logs the no-attachment response into the Email_Replies sheet.

Why Used:

It keeps a record of incomplete email submissions.

## 12.33 Mark Email as Read

Actual Node Type:

Gmail Node

Resource:

Message

Operation:

Mark as Read

Working:

This node marks the original incoming email as read after processing.

Why Used:

It helps identify that the email has already been handled by the workflow.

## 13. Branch Logic

## 13.1 No Attachment Branch

Condition:

Email does not contain a PDF attachment.

Flow:

Check Attachment Available
→ Prepare No Attachment Reply
→ Create No Attachment Draft Reply
→ Log No Attachment Reply
→ Mark Email as Read

Result:

No file is uploaded. No document is registered. A draft reply is created.

## 13.2 Missing Information Branch

Condition:

PDF exists but required document metadata is missing.

Flow:

Check Missing Required Information
→ Prepare Missing Info Reply
→ Append Missing Info Log
→ Create Missing Info Draft Reply
→ Mark Email as Read

Result:

Document is not uploaded. Document_Log is not updated. Missing_Info sheet is updated.

## 13.3 Duplicate Document Branch

Condition:

Same document number and same revision already exist.

Flow:

Check Duplicate Document
→ Prepare Duplicate Reply
→ Log Duplicate Reply
→ Create Duplicate Draft Reply
→ Mark Email as Read

Result:

Document is not uploaded again. Duplicate reply draft is created.

## 13.4 New Revision Branch

Condition:

Same document number with a higher revision is received.

Flow:

Check New Revision
→ Append Revision History
→ Reattach PDF Binary
→ Upload New Revision to Google Drive
→ Append New Revision Document Log
→ Append Approval Status
→ Create Registered Draft Reply
→ Mark Email as Read

Result:

Revision_History is updated and the new revision is registered.

## 13.5 New Document Branch

Condition:

Document number does not exist in the register.

Flow:

Check New Revision
→ Reattach PDF Binary
→ Upload Document to Google Drive
→ Append Document Log
→ Append Approval Status
→ Create Registered Draft Reply
→ Mark Email as Read

Result:

The document is uploaded, logged, tracked, and reply draft is created.

## 14. AI Metadata Extraction Prompt Logic

The AI is instructed to act as an AI Document Controller Assistant.

It must classify document type into:

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

It must classify discipline into:

* Architectural
* Civil
* Structural
* Mechanical
* Electrical
* Plumbing
* MEP
* QAQC
* Safety
* General

It must extract clean structured values only.

It must detect missing fields and decide the required action.

## 15. File Naming Logic

The workflow renames uploaded files using a professional document control naming format.

Example:

ABC-TWR_Material_Submittal_MS-ARC-001_0.pdf

Format:

ProjectCode_DocumentType_DocumentNumber_Revision.pdf

Benefits:

* Easy search
* Consistent naming
* Professional document control structure
* Better file organization

## 16. Duplicate and Revision Logic

The workflow uses the following key:

Document Number + Revision

Examples:

## Same Document Number + Same Revision

Result:

Duplicate document.

Action:

Do not upload again. Create duplicate draft reply.

## Same Document Number + Higher Revision

Result:

New revision.

Action:

Update Revision_History and register new revision.

## Same Document Number + Lower Revision

Result:

Old revision.

Action:

Manual review required.

## New Document Number

Result:

New document.

Action:

Upload and register document.

## 17. Dynamic Folder Routing Logic

The workflow maps document types to Google Drive folders.

Examples:

* RFI → 05_RFI
* MIR → 03_MIR
* WIR → 04_WIR
* Material Submittal → 07_Material_Submittals
* Drawing → 02_Drawings
* NCR → 06_NCR
* Method Statement → 08_Method_Statements
* Transmittal → 09_Transmittals
* Other → 01_Incoming_Documents

This makes storage automatic and organized.

## 18. Gmail Draft Reply Types

## 18.1 Registered Document Reply

Created when a document is successfully registered.

Includes:

* Project name
* Document number
* Revision
* Document title
* Document type
* Discipline
* Status
* Review due date
* Google Drive link

## 18.2 Duplicate Document Reply

Created when the same document number and revision already exist.

Includes:

* Document number
* Revision
* Project name
* Duplicate notice

## 18.3 Missing Information Reply

Created when required fields are missing.

Includes:

* Missing fields
* Document title
* Document number
* Revision
* Project name

## 18.4 No Attachment Reply

Created when no PDF file is attached.

Includes:

* Request to resend email with PDF attachment
* Required document information

## 19. Testing Summary

The workflow was tested with the following cases:

## New Document Registration

The workflow successfully registered a new document, uploaded it to Google Drive, updated Document_Log, updated Approval_Status, and created a draft reply.

## Duplicate Document Submission

The workflow detected duplicate document number and revision, stopped upload, and created a duplicate draft reply.

## New Revision Submission

The workflow detected a new revision, updated Revision_History, uploaded the new file, and registered the new revision.

## Missing Information

The workflow detected missing revision information, stopped registration, updated Missing_Info, and created a missing information draft reply.

## No Attachment

The workflow detected that no PDF attachment was available and created a no-attachment draft reply.

## RFI Folder Routing

The workflow detected RFI document type and uploaded the file to 05_RFI folder.

## MIR Folder Routing

The workflow detected MIR document type and uploaded the file to 03_MIR folder.

## WIR Folder Routing

The workflow detected WIR document type and uploaded the file to 04_WIR folder.

## 20. Real-World Value

This project is useful because it automates repetitive document control tasks that are common in construction and engineering projects.

It can help companies:

* Save time
* Improve accuracy
* Track revisions properly
* Avoid duplicate uploads
* Organize project documents
* Maintain clear registers
* Improve communication with contractors and consultants

## 21. Limitations

The workflow has some limitations:

* It depends on readable PDF text.
* Scanned PDFs may require OCR.
* Final approval still requires human review.
* AI extraction should be validated for critical documents.
* Folder IDs must be configured correctly.
* Gmail drafts are created, but final sending is manual.

## 22. Future Improvements

Future improvements can include:

* OCR support for scanned PDFs
* Dashboard analytics
* Reviewer assignment
* Overdue reminders
* Approval workflow
* Auto-transmittal generation
* Document status update emails
* Multi-project support
* Role-based review flow
* Integration with SharePoint or Autodesk Construction Cloud

## 23. Conclusion

AI Document Controller Assistant is a practical industry-based automation project that demonstrates how AI agents and n8n workflows can support real construction and engineering document control processes.

The workflow automates email intake, PDF processing, metadata extraction, duplicate checking, revision tracking, Google Drive storage, Google Sheets logging, approval tracking, and Gmail draft replies.

It does not replace document controllers. Instead, it supports them by reducing repetitive tasks and improving document control efficiency.
