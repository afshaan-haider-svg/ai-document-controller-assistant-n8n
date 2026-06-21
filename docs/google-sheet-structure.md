# Google Sheet Structure

## Google Sheet Name

AI Document Controller Register

The workflow uses this Google Sheet as the main document control register.

## 1. Document_Log

This tab stores all successfully registered documents.

## Columns

- Log_ID
- Date_Received
- Time_Received
- Project_Name
- Project_Code
- Document_Type
- Discipline
- Document_Number
- Document_Title
- Revision
- Submitted_By
- Sender_Email
- Status
- Priority
- File_Name
- New_File_Name
- Google_Drive_Link
- Review_Due_Date
- Days_Pending
- Duplicate_Check
- Latest_Revision
- AI_Remarks
- Action_Required
- Created_By

## Purpose

This tab works as the main document register.

## 2. Revision_History

This tab stores revision records.

## Columns

- History_ID
- Document_Number
- Document_Title
- Old_Revision
- New_Revision
- Previous_Status
- New_Status
- Received_Date
- Updated_Date
- Submitted_By
- Remarks

## Purpose

This tab tracks old and new revisions.

## 3. Missing_Info

This tab stores incomplete document submissions.

## Columns

- Missing_ID
- Date_Received
- Sender_Email
- Document_Title
- File_Name
- Missing_Fields
- Issue_Type
- AI_Message
- Draft_Status

## Purpose

This tab helps track documents with missing required information.

## 4. Approval_Status

This tab stores approval and review tracking details.

## Columns

- Approval_ID
- Document_Number
- Document_Title
- Revision
- Document_Type
- Discipline
- Submitted_By
- Review_Status
- Reviewer
- Received_Date
- Due_Date
- Approved_Date
- Remarks

## Purpose

This tab tracks document review and approval status.

## 5. Email_Replies

This tab stores records of AI-generated draft replies.

## Columns

- Reply_ID
- Date
- Sender_Email
- Subject
- Document_Number
- Reply_Type
- AI_Draft_Message
- Status

## Purpose

This tab keeps a record of all Gmail draft replies created by the workflow.

## Google Drive Folder Structure

The workflow uses the following Google Drive folders:

- 01_Incoming_Documents
- 02_Drawings
- 03_MIR
- 04_WIR
- 05_RFI
- 06_NCR
- 07_Material_Submittals
- 08_Method_Statements
- 09_Transmittals
- 10_Rejected_or_Missing_Info
- 11_Approved_Documents