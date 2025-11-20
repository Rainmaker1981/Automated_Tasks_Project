# Canvas API Setup

## 🧭 Goal

Allow Power Automate to call the Canvas API to pull assignments for your courses and feed them into the Excel `Tasks` table (via **Flow C**).

---

## 1️⃣ Find Your Canvas Base URL

Examples:

- `https://unk.instructure.com`
- `https://your-school.instructure.com`

This becomes the prefix for all API calls, e.g.:

```text
https://unk.instructure.com/api/v1/...

