\# Flow B — Outlook Calendar Event → Excel Tasks Table



\## 🎯 Purpose

Turn new or updated calendar events into structured Excel task rows, including:



\- Title  

\- Description  

\- Checklist (if you attach one manually in event notes or parse it)  

\- StartDate (from event start, or fallback)  

\- DueDate (from event end)  

\- Source tracking  

\- Duplicate-proof upsert logic  



---



\# 🔔 Trigger: When an Event Is Added, Updated, or Deleted (V3)



\*\*Connector:\*\* Outlook  

\*\*Calendar:\*\* Main calendar or a dedicated “School” calendar



---



\# 🧠 Flow Steps Overview



1\. Trigger on event action  

2\. Ignore deleted events  

3\. Create TaskId and timestamps  

4\. Extract StartDate and DueDate  

5\. Extract Title, Description, Checklist  

6\. Check if row already exists in Excel  

7\. Insert new row OR update existing row  



---



\# 1️⃣ Filter: Ignore Deleted Events

Add a \*\*Condition\*\* checking event action:



Left:  

```text



triggerOutputs()?\['body/action']



