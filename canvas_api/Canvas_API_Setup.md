# Canvas API Setup

## 🎯 Purpose
Configure Canvas API access so Flow C can retrieve assignments and sync them into Excel.

---

## 1️⃣ Canvas Base URL
Example:
https://unk.instructure.com

---

## 2️⃣ Generate a Personal Access Token
1. Canvas → Account → Settings  
2. Scroll to **Approved Integrations** or **New Access Token**  
3. Name: *Power Automate Tasks*  
4. Set expiry  
5. Generate Token  
6. Copy and store safely  

Use in header:  
Authorization: Bearer YOUR_TOKEN

---

## 3️⃣ Course IDs
Find them from Canvas course URLs:
https://unk.instructure.com/courses/12345  
→ course_id = 12345

Add these IDs to `varCourseIds` in Flow C.

---

## 4️⃣ Assignments Endpoint
GET /api/v1/courses/:course_id/assignments

Example:
https://unk.instructure.com/api/v1/courses/12345/assignments?per_page=50

---

## 5️⃣ HTTP Request in Power Automate
- Method: GET  
- URI:
https://unk.instructure.com/api/v1/courses/@{items('Apply_to_each')}/assignments?per_page=50  
- Headers:
Authorization: Bearer YOUR_TOKEN

---

## 6️⃣ Parse JSON
Use the schema file:
ParseJSON_Schema.json

---

## 7️⃣ Common Errors
401 Unauthorized → bad or expired token  
403 Forbidden → no access to the course  
429 Too Many Requests → slow down the schedule  

