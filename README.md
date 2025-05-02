# Archive_Sent_Mail_to_SharePoint

Automate the archiving of communication emails sent from a shared IT service account into a SharePoint Online document library, with metadata updates based on project categories (e.g., app name).

## Introduction

In the IT support team, communications to business entities are regularly sent using a common service email address such as `noreplyIT@company.com`. These emails are usually CC’d to the sender for traceability. However, archiving them manually in SharePoint folders related to each application (e.g., app name) is time-consuming and prone to human error.

This Power Automate flow automates:
- Detection of new emails in the sender's inbox
- Categorization based on the email subject
- Archiving in the appropriate SharePoint folder
- Updating metadata (sender, subject, date, category)

## 1. Business Problem

• How to ensure systematic and structured archiving of outgoing IT communications?  
• How to categorize and tag these emails automatically by project or application ?  
• How to maintain traceability and compliance with internal documentation policies?

## 2. Flow Logic (Power Automate)

### 1. **Trigger:**  
`When a new email arrives` in the sender's inbox (usually the IT team member CC’ing themselves).

### 2. **Condition: Application Identifier**  
Check if the email subject contains key identifiers ( app name) like:
- **ABC**
- **DEF**
...
- (Additional apps can be configured)

### 3. **If True:**
- **Export Email:** Save the message body and attachments.
- **Create File in SharePoint:**  
  Save the exported message in the appropriate SharePoint folder (e.g., `/Shared Documents/LAUREAT`).

### 4. **Condition: Project Folder Structure**
- Nested conditions to target correct subfolders or tag with project-specific metadata.

### 5. **Update File Properties:**
- Add metadata to the SharePoint file:
  - **Sender:** Extracted from the email
  - **Subject:** Email subject
  - **Date of Modification**
  - **Category:** Based on subject match

## Example Workflow

```plaintext
[When email arrives in inbox]
         ↓
[Condition: subject contains “ABC”?]
         ↓
      [True] ──► Export email
         ↓
      Create file in SharePoint folder COmmunication archive: "ABC"
         ↓
      Update metadata: Sender, Subject, Date, Category = “ABC”

## 2. Overview flow (Power Automate)

![image](https://github.com/user-attachments/assets/2fdcdd9d-49bd-4626-abbf-9ee8273f9595)
