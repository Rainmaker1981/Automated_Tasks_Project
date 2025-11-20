✅ Corrected README.md (Copy & Paste This Directly)
# Automated Tasks Integration Project

This project automates capturing tasks from multiple sources:

- Outlook emails  
- Outlook calendar events  
- Canvas LMS assignments  
- …into a master Excel task table  
- …then into Microsoft Planner tasks

Once everything is wired up, Planner becomes your “single pane of glass” for all school tasks, while Excel is the central source of truth.

---

## 🧱 Architecture Overview

```mermaid
flowchart LR
    A[Outlook Email] -->|Flow A| D[Excel Tasks Table]
    B[Outlook Calendar] -->|Flow B| D
    C[Canvas API] -->|Flow C| D
    D -->|Flow D| E[Microsoft Planner]

📁 Repo Structure
Automated_Tasks_Project/
│
├── README.md
│
├── excel/
│   └── Student_Tasks_Template.xlsx
│
├── flows/
│   ├── FlowA_Outlook_to_Excel.md
│   ├── FlowB_Calendar_to_Excel.md
│   ├── FlowC_CanvasAPI_to_Excel.md
│   └── FlowD_Excel_to_Planner.md
│
├── canvas_api/
│   ├── Canvas_API_Setup.md
│   ├── example_canvas_json.json
│   └── ParseJSON_Schema.json
│
└── reference/
    ├── Excel_Table_Design.md
    ├── PowerAutomate_Tips.md
    └── Troubleshooting.md

📊 Excel Master Task Table

Template file: excel/Student_Tasks_Template.xlsx
Live file: Must live in OneDrive or SharePoint for Power Automate.

Table name:
Tasks

Key columns (see reference/Excel_Table_Design.md for full details):

TaskId – unique ID (OUTLOOK-…, CAL-…, CANVAS-…)

Title – short task title

Description – longer body text / instructions

Checklist – parsed sub-tasks (multi-line text)

StartDate – parsed or fallback to utcNow()

DueDate – deadline

Source – Outlook / Calendar / Canvas

SourceId – raw ID from the source

Course – course name/code

Status – New, Pushed_to_Planner, Archived

CreatedOn – when the row was created

⚙️ Flows

Documentation stored in /flows:

FlowA_Outlook_to_Excel.md

Trigger: new email

Filters relevant messages

Builds TaskId, StartDate, DueDate, Checklist

Inserts into Excel with Source = Outlook

FlowB_Calendar_to_Excel.md

Trigger: calendar event added/updated

Uses event start/end as StartDate/DueDate

Upserts into Excel with Source = Calendar

FlowC_CanvasAPI_to_Excel.md

Trigger: recurrence

Calls Canvas API for assignments

Uses unlock_at (StartDate), due_at (DueDate)

Upserts into Excel with Source = Canvas

FlowD_Excel_to_Planner.md

Trigger: recurrence

Selects rows where Status = New

Creates Planner tasks

Builds Planner checklist from Excel Checklist

Sets Status = Pushed_to_Planner

🌐 Canvas API

Docs and helper files located in /canvas_api:

Canvas_API_Setup.md — how to get base URL, token, course IDs

example_canvas_json.json — sample assignment data

ParseJSON_Schema.json — schema for Canvas Parse JSON action

📚 Reference Docs

Stored in /reference:

Excel_Table_Design.md — exact table structure for Tasks

PowerAutomate_Tips.md — expressions, OData filters, duplicate-protection patterns

Troubleshooting.md — common error causes and fixes (dates, Canvas auth, duplicates, etc.)

🚀 How to Use This Project

Create the live Excel file in OneDrive/SharePoint, based on Student_Tasks_Template.xlsx.

Build Flows A, B, C, and D using the documentation in /flows.

Configure Canvas API access using /canvas_api/Canvas_API_Setup.md.

Test each flow individually:

Email → Excel

Calendar → Excel

Canvas → Excel

Excel → Planner

Turn all flows ON.

After setup:

Outlook + Calendar + Canvas → Excel → Planner
Excel’s Status column controls when rows are sent to Planner.
Planner becomes your unified student task dashboard.


---

# 🟢 Summary of What Was Fixed

### 1. **Closed the mermaid code block**  
You were missing the closing ``` which breaks rendering of everything after it.

### 2. **Repo structure formatted as proper code block**  
GitHub was not rendering it correctly.

### 3. **Converted section labels into headings**  
Your sections like “📁 Repo Structure” were plain text; now they are proper `##` headings.

### 4. **Added spacing and separators for clean GitHub display**

---

If you want, I can also:

- Validate **your flows**  
- Validate **your reference files**  
- Validate **your canvas_api setup files**  
- Generate a combined master documentation file

Just tell me **which folder you'd like validated next.**
