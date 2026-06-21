# Test Cases

## Test Case 1: New Document Registration

## Input

Document Type: Material Submittal  
Document Number: MS-ARC-005  
Revision: 0  
Discipline: Architectural  

## Expected Output

- Attachment detected
- PDF text extracted
- AI metadata extracted
- Missing information check passed
- Duplicate check passed
- File uploaded to Google Drive
- Document_Log updated
- Approval_Status updated
- Gmail registered draft reply created
- Email marked as read

## Test Case 2: Duplicate Document Submission

## Input

Same document number and same revision submitted again.

Example:

Document Number: MS-ARC-001  
Revision: 0  

## Expected Output

- Duplicate detected
- File not uploaded again
- Document_Log not duplicated
- Duplicate draft reply created
- Email_Replies updated
- Email marked as read

## Test Case 3: New Revision Submission

## Input

Same document number with a higher revision.

Example:

Old Revision: 0  
New Revision: 1  

## Expected Output

- New revision detected
- Revision_History updated
- File uploaded to Google Drive
- Document_Log updated
- Approval_Status updated
- Registered draft reply created
- Email marked as read

## Test Case 4: Missing Information

## Input

Document submitted without revision or other required information.

Example:

Document Number: MS-ARC-002  
Revision: Missing  

## Expected Output

- Missing information detected
- File not uploaded to Google Drive
- Document_Log not updated
- Missing_Info sheet updated
- Missing information draft reply created
- Email marked as read

## Test Case 5: No Attachment Email

## Input

Email received without any PDF attachment.

## Expected Output

- Check Attachment goes to false branch
- No attachment draft reply created
- Email_Replies sheet updated
- Email marked as read

## Test Case 6: RFI Folder Routing

## Input

Document Type: RFI  
Document Number: RFI-CIV-003  
Revision: 0  

## Expected Output

- AI identifies document type as RFI
- Target folder selected as 05_RFI
- File uploaded to 05_RFI folder
- Document_Log updated
- Approval_Status updated
- Registered draft reply created

## Test Case 7: MIR Folder Routing

## Input

Document Type: MIR  
Document Number: MIR-MEP-001  
Revision: 0  

## Expected Output

- AI identifies document type as MIR
- Target folder selected as 03_MIR
- File uploaded to 03_MIR folder
- Document_Log updated
- Approval_Status updated
- Registered draft reply created

## Test Case 8: WIR Folder Routing

## Input

Document Type: WIR  
Document Number: WIR-ARC-001  
Revision: 0  

## Expected Output

- AI identifies document type as WIR
- Target folder selected as 04_WIR
- File uploaded to 04_WIR folder
- Document_Log updated
- Approval_Status updated
- Registered draft reply created

## Final Testing Status

The workflow was successfully tested for:

- New document registration
- Duplicate document detection
- New revision tracking
- Missing information handling
- No attachment handling
- RFI folder routing
- MIR folder routing
- WIR folder routing