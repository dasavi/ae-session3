# Cloud Architecture Overview

A simple system context diagram for the monorepo: React frontend, Express API, and an in-memory data store.

```mermaid
flowchart TB
    %% Actors
    user[End User]

    %% Client
    subgraph Client (Browser)
        frontend[React SPA (packages/frontend)]
    end

    %% Server
    subgraph Server (Node.js)
        api[Express API Server (packages/backend)]
        store[(In-Memory Data Store)]
    end

    %% Flows
    user --> frontend
    frontend --> api
    api --> store

    %% Notes
    %% - Frontend runs in the browser
    %% - Backend runs in Node.js and uses in-memory storage
    %% - Data persists only for the life of the process
```

## Sequence: Create a TODO

```mermaid
sequenceDiagram
    autonumber
    participant U as End User
    participant B as React SPA (Browser)
    participant A as Express API (Server)
    participant S as In-Memory Store

    U->>B: Open app / click "Add Task"
    B->>B: Render Task Form (title, priority, dueDate)
    U->>B: Enter details and submit
    B->>A: POST /tasks {title, priority, dueDate}
    A->>A: Validate payload (title required, dueDate ISO YYYY-MM-DD)
    alt Valid payload
        A->>S: Save task
        S-->>A: OK
        A-->>B: 201 Created {task}
        B->>B: Update list UI
    else Invalid payload
        A-->>B: 400 Bad Request {error}
        B->>B: Show inline validation message
    end
```
