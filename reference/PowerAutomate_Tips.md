# Power Automate Tips — Expressions, Patterns, and Best Practices

These tips apply to every flow in this project (A, B, C, D).  
Use this file as a quick reference while editing or debugging flows.

---

# ⚙️ Useful Expressions

### ✅ Concatenate strings
```text
concat('OUTLOOK-', triggerOutputs()?['body/messageId'])

utcNow()

formatDateTime(
  addDays('1899-12-30', int(item()?['DueDate'])),
  'yyyy-MM-ddTHH:mm:ssZ'
)
