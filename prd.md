---
stepsCompleted: ['step-01-init', 'step-02-discovery', 'step-03-success', 'step-04-journeys', 'step-05-domain', 'step-06-innovation', 'step-07-project-type', 'step-08-scoping', 'step-09-functional', 'step-10-nonfunctional', 'step-11-polish']
inputDocuments: ['product-brief-bmad_project-2026-01-17.md', 'project-context.md', 'brainstorming-session-2026-01-17.md']
workflowType: 'prd'
documentCounts:
  briefCount: 1
  researchCount: 0
  brainstormingCount: 1
  projectDocsCount: 0
classification:
  projectType: 'web_app'
  domain: 'SaaS / Productivity'
  complexity: 'low'
  projectContext: 'greenfield'
---

# Product Requirements Document - Project Timeline Tool

**Author:** Admin
**Date:** 2026-01-17
**Status:** Draft

## 1. Executive Summary

### Product Vision
"The Anti-Jira." A minimalist timeline tool designed for the specific gap between "internal project management" and "external client communication." Unlike complex PM tools (Monday/Asana), this tool is a "Client Broadcaster"—a simple, read-only window into the project's high-level status.

### Unique Value Proposition
*   **Speed:** Create a timeline in < 2 minutes.
*   **Frictionless:** Zero login for clients. One-click access.
*   **Clarity:** Hides the sausage-making (internal subtasks) and shows only the meal (high-level phases).

### Target Audience
*   **Primary:** Project Leads/Freelancers who need to calm anxious clients.
*   **Secondary:** Clients (Executives/Stakeholders) who want instant reassurance.

## 2. Success Criteria

### User Success
*   **Update Velocity:** Project Leads can update a timeline in **< 60 seconds**.
*   **Zero-Friction Access:** Clients can view status in **1 click** (no login).

### Business Success
*   **Communication Efficiency:** Reduce "Status Update" support tickets/emails to **near zero**.
*   **Adoption:** **100%** of active internal projects migrated to the tool.

### Technical Success
*   **Performance:** Public share links load in **< 1 second** on 4G networks.
*   **Reliability:** **99.9% Uptime** for public links (clients must never see a broken page).
*   **Security:** Share IDs must be cryptographically random (UUID v4) and unguessable.

## 3. User Journeys

### Journey A: "The 5-Minute Setup" (Project Lead)
**Scenario:** New project kickoff. The Lead wants to set expectations immediately.
1.  **Login:** Lead logs in with shared credentials. Dashboard loads in < 1s.
2.  **Create:** Clicks "New Project", types "Website Redesign", hits Enter. Canvas opens.
3.  **Define:**
    *   Sets Project Start/End dates (visual span).
    *   Adds "Discovery" task (Status: Done).
    *   Adds "Design" task (Status: In Progress).
    *   Adds "Development" task (Status: Todo).
4.  **Refine:** Drags "Development" bar to start after "Design".
5.  **Share:** Clicks "Share", copies the generated link (`app.com/v/7x9-22a`).
6.  **Resolution:** Pastes link into client email. Done in 3 minutes.

### Journey B: "The Friday Panic" (Customer)
**Scenario:** 4:55 PM on Friday. VP asks the Client, "Is the website design done yet?"
1.  **Trigger:** Panic. Client searches email for "project link".
2.  **Access:** Clicks the link. No login prompt. No loading spinner.
3.  **Verification:** Gantt chart appears instantly. Client sees "Design" bar is green (Completed).
4.  **Resolution:** Screenshots the view, emails VP: "Yes, finished today."
5.  **Outcome:** Trust restored. No email sent to Project Lead.

### Journey C: "The Scope Change" (Lead)
**Scenario:** A dependency delayed the project by 2 weeks.
1.  **Update:** Lead opens tool, drags "Development" bar 2 weeks to the right.
2.  **Conflict:** Visual indicator shows the task now extends past the Project End Date.
3.  **Decision:** Lead drags the Project End Date to extend it. System auto-saves.
4.  **Verification:** Client refreshes their link 5 minutes later and sees the new timeline.
5.  **Outcome:** Single source of truth updated instantly.

### Journey Requirements Summary
*   **Performance:** Dashboard and Public View must load nearly instantly to support these flows.
*   **Interaction:** Drag-and-drop is synonymous with "editing" (no modal forms for simple date changes).
*   **Persistence:** Auto-save is critical; no "Submit" buttons to forget.

## 4. Project Scoping & Phased Development

### MVP Strategy & Philosophy
**MVP Approach:** "The Excel Killer." Focus entirely on speed of creation and ease of sharing. If it's faster than Excel, we win.
**Resource Requirements:** Small team (1-2 devs). Focus on frontend interactions (drag-and-drop) and reliable read-only view.

### MVP Feature Set (Phase 1)
**Core User Journeys Supported:**
*   Journey A: 5-Minute Setup (Lead)
*   Journey B: The Friday Panic (Customer)
*   Journey C: The Scope Change (Lead)

**Must-Have Capabilities:**
*   **Auth:** Shared Admin Login.
*   **Projects:** Create, Rename, Delete.
*   **Timeline:** Visual Start/End Project Dates. Drag-and-drop Tasks.
*   **Sharing:** Public Link Generator (UUID).
*   **Client View:** Read-only, mobile-responsive Gantt.

### Post-MVP Features (Growth & Expansion)
*   **Phase 2 (Growth):** Multi-User Auth, Project Archiving, Branding (logo upload).
*   **Phase 3 (Expansion):** iFrame Embeds, Templates, API access.

### Risk Mitigation Strategy
*   **Technical:** Drag-and-drop complexity -> Prototype with mature library (dnd-kit/Framer Motion).
*   **Market:** Scope creep -> Stay "Opinionated" (simple > complex).
*   **Resource:** Backend too complex -> Use Backend-as-a-Service (Supabase/Firebase).

## 5. Web App Specific Requirements

### Project-Type Overview
As a **Single-Page Application (SPA)**, the tool prioritizes app-like responsiveness and instant interactivity (drag-and-drop) over traditional page-based navigation.

### Technical Architecture Considerations
*   **Architecture:** SPA (React/Vue/Svelte) for rich client-side interactions.
*   **Real-Time:** WebSockets/Polling for live updates ("Broadcaster" capability).
*   **Browser Support:** Modern Evergreen Browsers only. No IE11.
*   **SEO Strategy:** **Explicitly Blocked.** `robots.txt` and meta tags to prevent indexing.

### Implementation Considerations
*   **Responsive Design:** Public View fully responsive for mobile. Admin Dashboard optimized for Desktop.
*   **Performance:** Critical path rendering for Public View < 1s.
*   **Accessibility:** WCAG 2.1 AA target for Public View.

## 6. Functional Requirements

### 1. Authentication & Accounts
*   **FR1:** Admin can log in via email/password credentials.
*   **FR2:** System maintains a persistent session token until explicit logout.

### 2. Project Management
*   **FR3:** Admin can create a new project with a Title and Start/End Date.
*   **FR4:** Admin can rename an existing project.
*   **FR5:** Admin can delete a project (Permanent Destructive Action).
*   **FR6:** Admin can view a list of all active projects on a dashboard.

### 3. Timeline Management (The Core Time-Series Engine)
*   **FR7:** Admin can add a Task with Title, Status (Todo/In Progress/Done), and Date Range.
*   **FR8:** Admin can visually drag a Task bar to change its Start/End dates.
*   **FR9:** Admin can resize a Task bar to extend/shorten duration.
*   **FR10:** Admin can delete a specific Task.
*   **FR11:** System automatically saves changes ("Auto-Save") after any edit interaction.
*   **FR12:** Admin can modify the Project's Reference Start/End lines.

### 4. Sharing & Distribution
*   **FR13:** Admin can generate a specific "Public Link" for a project.
*   **FR14:** System ensures Public Links use a cryptographically unguessable ID (UUID).
*   **FR15:** Admin can revoke/regenerate a link (effectively "Private" -> "Public" toggle).

### 5. Client Access (Read-Only)
*   **FR16:** Public User can view the Project Title, Dates, and Gantt Timeline via the shared link.
*   **FR17:** Public User *cannot* edit, drag, or modify any data.
*   **FR18:** Public User requires *no login* to view the link.

## 7. Non-Functional Requirements

### Performance
*   **Public View Load:** < 1 second Time-to-Interactive on 4G networks.
*   **Interaction Latency:** Drag-and-drop operations update UI within 16ms (60fps target).
*   **API Response:** Standard API endpoints respond in < 200ms.

### Security
*   **Link Entropy:** Public Access Links uses UUID v4 (122 random bits).
*   **Authentication:** All Admin routes protected by secure session.
*   **Data Isolation:** Public View endpoint returns ONLY read-only data for the specific project.

### Reliability
*   **Uptime:** 99.9% Availability target.
*   **Data Integrity:** Auto-save persists immediately.

### Accessibility
*   **Compliance:** Public View targets WCAG 2.1 AA standards.
*   **Assistive Tech:** Gantt chart accessible via screen readers.
