# automated tasks integration project

this repo documents an automation system that turns school “stuff” into actionable tasks:

- outlook emails → excel master task table  
- outlook calendar events → excel master task table  
- canvas lms assignments (via api) → excel master task table  
- excel master task table → microsoft planner tasks  

once it’s running, new tasks show up in one place (planner), but the source of truth is the excel table.

---

## architecture overview

```mermaid
flowchart lr
    a[outlook email] -->|flow a| d[excel: tasks table]
    b[outlook calendar] -->|flow b| d
    c[canvas api] -->|flow c| d
    d -->|flow d| e[microsoft planner]
