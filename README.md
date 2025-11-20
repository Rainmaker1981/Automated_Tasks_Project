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

File (template in this repo):
excel/Student_Tasks_Template.xlsx

Live file:
Must live in OneDrive or SharePoint for Power Automate.

Table name:
Tasks

Key columns (see reference/Excel_Table_Design.md for details):

TaskId – unique ID (OUTLOOK-…, CAL-…, CANVAS-…)

Title – short task title

Description – longer body text / instructions

Checklist – parsed sub-tasks (multi-line text)

StartDate – when to start working (parsed or fallback to utcNow())

DueDate – deadline (real date/time)

Source – Outlook, Calendar, or Canvas

SourceId – raw ID from the source (MessageId, EventId, AssignmentId)

Course – course name/code

Status – New, Pushed_to_Planner, Archived

CreatedOn – when the row was first created

⚙️ Flows

Detailed docs live in /flows:

FlowA_Outlook_to_Excel.md

Trigger: new email

Filters for relevant messages

Builds TaskId, StartDate, DueDate, Checklist

Inserts into Excel Tasks table with Source = Outlook

FlowB_Calendar_to_Excel.md

Trigger: calendar event added/updated

Uses event start/end as StartDate/DueDate

Upserts into Excel with Source = Calendar

FlowC_CanvasAPI_to_Excel.md

Trigger: recurrence (e.g. hourly)

Calls Canvas API for assignments

Uses unlock_at as StartDate, due_at as DueDate

Upserts into Excel with Source = Canvas

FlowD_Excel_to_Planner.md

Trigger: recurrence (e.g. every 15 minutes)

Selects rows where Status = New

Creates Planner tasks

Writes Planner checklist items from the Checklist column

Sets row Status = Pushed_to_Planner

🌐 Canvas API

Docs and helper files live in /canvas_api:

Canvas_API_Setup.md – how to get the base URL, token, and course IDs

example_canvas_json.json – sample assignments response

ParseJSON_Schema.json – schema used by the Parse JSON action in Flow C

📚 Reference Docs

The /reference folder contains:

Excel_Table_Design.md – exact column layout and types for Tasks

PowerAutomate_Tips.md – expressions, OData filters, duplicate protection patterns

Troubleshooting.md – common error causes and fixes (dates, Canvas auth, duplicates, etc.)

🚀 How to Use This Project

Create the live Excel file in OneDrive/SharePoint based on Student_Tasks_Template.xlsx.

Build Flow A, B, C, and D in Power Automate using the docs in /flows.

Configure Canvas API using /canvas_api/Canvas_API_Setup.md.

Test each flow individually (email → Excel, calendar → Excel, Canvas → Excel, Excel → Planner).

Turn all flows on.

From that point:

Outlook + Calendar + Canvas → Excel → Planner

Excel Status and columns in Tasks become your single source of truth.
