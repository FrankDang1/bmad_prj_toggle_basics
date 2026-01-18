# Project Context: Internal Project Timeline Tool

## 1. Project Overview
A lightweight, manual-control project management tool designed for internal teams to view timelines and share specific views with clients.
**Core Philosophy:** Simplicity > Features. Trust > Permissions.

## 2. Core Entities
### 2.1 Projects
- **Attributes:**
    - `name` (String)
    - `timeline` (Start Date, End Date) - *Manual visual reference only.*
- **Behavior:**
    - Serves as a grouping container for tasks.
    - Generates a unique, secure "Share Link" for external viewing.

### 2.2 Tasks
- **Attributes:**
    - `title` (String)
    - `description` (Text)
    - `time_range` (Start DateTime, End DateTime)
    - `status` (Enum: Todo, In Progress, Testing, Pending, Completed)
- **Constraints:**
    - No `Assignee` field.
    - No `Priority` field.
    - Can strictly exist *outside* the Project Timeline (no validation error, just visual indication).

## 3. User Roles & Access
### 3.1 Internal Team
- **Authentication:** Standard Login.
- **Permissions:** Full Admin/CRUD on ALL Projects and Tasks.
- **Trust Model:** Everyone is equal; no "Manager" vs "Member" roles.

### 3.2 Clients (External)
- **Authentication:** None (Link capability).
- **Access:** View-Only.
- **Scope:** Restricted to the *specific project* associated with the link.
- **Isolation:** Cannot navigate to other projects or see internal comments (if any added later).

## 4. Key Views
### 4.1 Gantt Chart
- **Filter:** Single or Multiple Projects.
- **Visuals:**
    - **Project Line:** A thin, reference background line or bar showing the "Planned Timeline".
    - **Task Bars:** Rendered above/on the timeline.
    - **Conflict:** If a Task bar extends past the Project Line, it is rendered as-is (e.g., sticking out). No clippings.

## 5. Technical Constraints
- **Stack:** (TBD - Standard Web App)
- **Security:** "Share Links" must be unguessable (e.g., UUIDs) and revocable.
