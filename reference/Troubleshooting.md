# ✅ **3. Troubleshooting.md**

🧹 General Debugging Checklist

1. Check Run History

2. Inspect Inputs and Outputs of failing action

3. Use “Compose” to peek at variables

4. Validate your OData filter syntax

5. Test with sample JSON

6. Disable/enable flow if stuck

7. Export and re-import flows if they become corrupted



# ❌ Issue 1: Planner Due Date Format Error

Error: The value '45981' does not match expected format 'String/date-time'

### 💡 Cause:
Excel stored date as a **serial number** instead of ISO date.

### ✅ Fix:
Use the date conversion expression:

```text
formatDateTime(
  addDays('1899-12-30', int(item()?['DueDate'])),
  'yyyy-MM-ddTHH:mm:ssZ'
)

❌ Issue 2: Duplicate Tasks Appearing in Planner
💡 Cause:

Flow D didn’t detect the row as already processed.

✅ Fix:

Ensure Flow D:

Filters only rows where Status eq 'New'

Updates each row to Pushed_to_Planner immediately after creation

❌ Issue 3: Calendar Events or Emails Reprocessed Multiple Times
💡 Cause:

Duplicate check missing or broken.

🔧 Fix:

For every flow:
Source eq '<System>' and SourceId eq '<ID>'

❌ Issue 4: Canvas API — 401 Unauthorized
Reasons:

Token expired

Token missing or mis-typed

Using “BearerXYZ” instead of “Bearer XYZ”

Fix:

Header must be:
Authorization: Bearer YOUR_TOKEN

❌ Issue 5: Canvas API — 403 Forbidden
Reasons:

Token does not have permission

You are not enrolled in the course

Wrong course_id

Fix:

Verify:

Course access

Token scope

Token expiration

❌ Issue 6: Excel Connector Cannot Find File
Reasons:

You moved/renamed the file

Two files with the exact name exist in OneDrive

File not in a supported connector location

Fix:

Put the LIVE file in OneDrive or SharePoint

Rebind Excel actions to the correct file

❌ Issue 7: Slow Planner Task Creation
Reasons:

Too many tasks in a single run

Planner API rate limiting

Checklist items causing extra loops

Fix:

Increase recurrence interval

Reduce number of tasks processed

Batch creation (advanced)

