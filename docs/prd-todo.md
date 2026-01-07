# Product Requirements Document (PRD) - TODO App Upgrade: Due Dates, Priorities, Filters

## 1. Overview

We are upgrading the basic TODO app (currently tasks have title and completed status) to support due dates, priorities, and quick filters so users can better organize tasks and focus on what’s urgent. The MVP remains client-only (local storage) to keep the solution simple and teachable.

---

## 2. MVP Scope

- Data model and validation
  - `title`: required
  - `priority`: enum "P1" | "P2" | "P3"; default "P3"
  - `dueDate`: optional ISO date string `YYYY-MM-DD`; invalid values are ignored (treated as absent)
- Filters and visibility
  - Tabs: All, Today, Overdue
  - Completed tasks are visible in All
  - Today and Overdue show incomplete tasks only
- Priority display
  - Show priority on each task with simple badges; use color cues if feasible (P1 red, P2 orange, P3 gray)
- Storage and architecture
  - Persist tasks in browser local storage only; no backend or external storage
- Existing behaviors retained
  - Maintain existing ability to add, edit, mark complete/incomplete, and delete tasks

---

## 3. Post-MVP Scope

- Overdue highlighting
  - Visually emphasize overdue tasks (e.g., red highlight or accent)
- Sorting rules
  - Order list by: overdue first → priority (P1→P3) → due date ascending → undated last

---

## 4. Out of Scope

- Notifications
- Recurring tasks
- Multi-user support
- Keyboard navigation (advanced accessibility work)
- External storage or backend changes (stay local-only)
