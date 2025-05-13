# 🛠️ Automation_Leave_Request_System

## 📌 Project Overview

**Automation_Leave_Request_System** is a mini project that automates the employee leave request process using Microsoft 365 tools. It removes manual workflows and integrates Microsoft Forms, Power Automate, SharePoint, and Outlook to streamline the leave request and approval process.

---

## 🚀 Platforms & Technologies Used

| Tool              | Purpose                                                                 |
|-------------------|-------------------------------------------------------------------------|
| Microsoft Forms   | To collect leave requests from employees                                |
| SharePoint        | To store and track leave request data                                   |
| Power Automate    | To automate the request approval process and notifications              |
| Microsoft Outlook | To send automated approval/rejection emails to employees and managers   |

---

## 📝 Steps to Build the System

### ✅ Step 1: Create the Leave Request Form

1. Go to [Microsoft Forms](https://forms.microsoft.com).
2. Click **New Form** and name it **Leave Request Form**.
3. Add the following fields:
   - **Full Name** (Short answer)
   - **Email Address** (Short answer)
   - **Leave Type** (Dropdown: Annual, Sick, Study)
   - **Start Date** (Date)
   - **End Date** (Date)
   - **Reason for Leave** (Long answer)

---

### 📁 Step 2: Set Up SharePoint List

1. Open your **SharePoint** site.
2. Create a **new blank list** and name it **Leave Requests**.
3. Add the following columns:
   - **Full Name** (Text)
   - **Email Address** (Text)
   - **Leave Type** (Choice)
   - **Start Date** (Date)
   - **End Date** (Date)
   - **Reason** (Multiple lines of text)
   - **Status** (Choice: Pending, Approved, Rejected)

---

### ⚙️ Step 3: Create a Flow in Power Automate

1. Open [Power Automate](https://flow.microsoft.com).
2. Click **Create > Automated cloud flow**.
3. Name the flow: `Leave Request Approval Flow`.
4. Choose trigger: **When a new response is submitted** (Microsoft Forms).

---

### 🔧 Step 4: Configure the Flow

#### A. Get Form Response Details
- **Action**: Get response details
- **Form ID**: Select your form
- **Response ID**: Use dynamic content

#### B. Add to SharePoint List
- **Action**: Create item
- **Site Address**: Your SharePoint site
- **List Name**: Leave Requests
- **Map form responses** to corresponding SharePoint columns

#### C. Start Approval
- **Action**: Start and wait for an approval
- **Approval Type**: Approve/Reject - First to respond
- **Title**: `Leave request from [Full Name]`
- **Assigned To**: Manager’s email
- **Details**: Include leave type, reason, start and end dates

#### D. Condition Based on Outcome
- **Condition**: If Outcome is **Approve**
  - Send email to requester (Approved)
  - Update SharePoint item status to **Approved**
- **Else** (Rejected)
  - Send email to requester (Rejected)
  - Update SharePoint item status to **Rejected**

---

### 🧪 Step 5: Test the Workflow

- Submit a leave request via the form.
- Verify:
  - Item appears in SharePoint list with **Pending** status
  - Manager receives an approval email
  - Upon decision:
    - Requester receives email
    - SharePoint list updates to **Approved** or **Rejected**

---

## ✅ Benefits

- No manual intervention
- Instant email notifications
- Centralized request tracking
- Fast approvals with a complete audit trail

---

## 📌 Author

**Mini Project Contributor Team**  
Automation with Microsoft 365 Tools
