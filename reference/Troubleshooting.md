# Troubleshooting Guide — Automated Tasks Project

This guide covers the most common issues for Flows A–D.

---

# ❌ Issue 1: Planner Due Date Format Error

Error:
The value '45981' does not match expected format 'String/date-time'.

💡 Cause: Excel returned a serial number  
✅ Fix:
formatDateTime(
  addDays('1899-12-30', int(item()?['DueDate'])),
  'yyyy-MM-ddTHH:mm:ssZ'
)

---

# ❌ Issue 2: Duplicate Tasks Appearing in Planner

Cause: Status not updated or duplicate check missing  
Fix:
- Filter Excel rows: Status eq 'New'  
- Update Status → Pushed_to_Planner after creation  

---

# ❌ Issue 3: Calendar/Email Items Reprocessed

Cause: No Source + SourceId duplicate check  
Fix:
Source eq '<System>' and SourceId eq '<ID>'

---

# ❌ Issue 4: Canvas API — 401 Unauthorized

- Token invalid/expired  
- Missing space in “Bearer TOKEN”  
- Wrong domain  

---

# ❌ Issue 5: Canvas API — 403 Forbidden

- Not enrolled in course  
- Token lacks permissions  
- Incorrect course_id  

---

# ❌ Issue 6: Excel File Not Found

Fix:
- Ensure file is in OneDrive/SharePoint  
- Rebind Excel connections  
- Avoid duplicate file names  

---

# ❌ Issue 7: Slow Planner Task Creation

Fix:
- Increase flow interval  
- Reduce volume  
- Checklist processing increases loops  

---

# 🧹 Debugging Checklist

1. Check Run History  
2. Inspect Inputs/Outputs  
3. Add Compose steps  
4. Check OData syntax  
5. Test JSON structures  
6. Disable/re-enable flows  
7. Export/import flows if needed  

---

# 🎯 Summary

This guide resolves issues involving:
- Planner  
- Canvas API  
- Excel connector  
- Duplicates  
- Date formatting  
