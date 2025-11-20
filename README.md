# Automated Tasks Integration Project

this repo documents an automation system that turns school “stuff” into actionable tasks:

- outlook emails → excel master task table  
- outlook calendar events → excel master task table  
- canvas lms assignments (via api) → excel master task table  
- excel master task table → microsoft planner tasks  

once it’s running, new tasks show up in one place (planner), but the source of truth is the excel table.

---

## Architecture Overview

```mermaid
flowchart LR
    A[Outlook Email] -->|Flow A| D[Excel: Tasks Table]
    B[Outlook Calendar] -->|Flow B| D
    C[Canvas API] -->|Flow C| D
    D -->|Flow D| E[Microsoft Planner]

