\# Flow C — Canvas API Assignments → Excel Tasks Table



\## 🎯 Purpose

Automatically fetch assignments from Canvas via API and insert or update rows in the Excel `Tasks` table:



Includes support for:

\- Title  

\- Description  

\- Checklist (parsed from HTML or notes)  

\- StartDate (uses `unlock\_at` or fallback)  

\- DueDate  

\- Duplicate prevention  

\- Course tracking  



Flow C runs on a \*\*schedule\*\* and keeps your Excel task list aligned with Canvas.



---



\# ⏱️ Trigger: Recurrence



Suggested schedule:

\- Every 1–4 hours  

\- Or daily if you want less noise  



Example:



