# Power Automate Tips — Expressions, Patterns, and Best Practices

These tips apply to every flow in this project (A, B, C, D).  
Use this file as a quick reference while editing or debugging flows.

---

# ⚙️ Useful Expressions

### ✅ Concatenate strings
concat('OUTLOOK-', triggerOutputs()?['body/messageId'])

### ✅ Current UTC Timestamp
utcNow()

### ✅ Convert Excel serial date → ISO 8601
formatDateTime(
  addDays('1899-12-30', int(item()?['DueDate'])),
  'yyyy-MM-ddTHH:mm:ssZ'
)

Use similar logic for StartDate.

---

# 🔍 Checking If Something Is Empty
empty(item()?['Checklist'])

# 🔢 Length of a list (duplicate check)
length(body('List_rows_present_in_a_table')?['value'])

---

# 🔐 Filter Queries (Excel)

Find a specific Canvas assignment:
Source eq 'Canvas' and SourceId eq '98765'

Find only new tasks:
Status eq 'New'

---

# 🛑 Duplicate Protection Pattern

1. List rows present in a table  
2. Filter by Source + SourceId  
3. Condition on length()  
4. If 0 → Insert  
5. If >0 → Update or Skip  

---

# 🧪 Debugging Tips

- Add “Compose” steps to inspect values  
- Use Run History to inspect failures  
- Validate OData filters  
- Test with sample JSON  
- Export/import flows if corrupted  

---

# 🚀 Performance Tips

- Use scheduled runs for reliability  
- Avoid overly frequent triggers  
- Canvas API rate-limits heavy polling  
- Keep loops minimal  

---

# 🔒 Connection Hygiene

Rename connectors:
- Excel - Tasks File  
- Outlook - Student Email  
- Planner - Student Plan  

---

# 🧹 Helpful Patterns

Normalize text:
toLower(item()?['Source'])

Replace HTML tags:
replace(replace(item()?['description'], '<p>', ''), '</p>', '')

Create multi-line text:
concat('- ', variables('step1'), '\n', '- ', variables('step2'))

---

# ✅ Summary

This reference covers:
- Expressions  
- OData filters  
- Duplicate patterns  
- Date conversion  
- Debugging tips  
- Connector hygiene  
