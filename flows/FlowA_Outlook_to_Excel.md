# Flow A — Outlook Email → Excel Tasks Table

## 🎯 Purpose
Convert qualifying emails into structured task rows in the master Excel table, including:

- Title  
- Description  
- Checklist (parsed from the email if present)  
- StartDate (parsed or auto-generated)  
- DueDate (parsed or default)  
- Source tracking  
- Duplicate protection  

This is the first entry point of the automated multi-system task workflow.

---

# 🔔 Trigger: When a New Email Arrives (V3)

**Connector:** Outlook  
**Folder:** Inbox (or a dedicated “School” folder)

Recommended trigger settings:
- Include Attachments: No  
- Only With Attachments: No  
- Importance: Any  

---

# 🧠 Flow Steps Breakdown

## 1️⃣ **Trigger fires on new email**

---

## 2️⃣ **Filter which emails become tasks**

Add a **Condition** after the trigger.  
Good filtering options:

### Option A — Subject tag
