---
stepsCompleted: [1, 2, 3, 4, 5]
inputDocuments: ['project-context.md', 'brainstorming-session-2026-01-17.md']
date: 2026-01-17
author: frank
---

# Product Brief: bmad_project

<!-- Content will be appended sequentially through collaborative workflow steps -->

## Executive Summary

The **Internal Project Timeline Tool** is a purpose-built communication bridge designed to solve a single critical problem: keeping customers informed with up-to-date project timelines. Currently, no tool allows us to easily share live, visual progress with clients without accounts or friction. This tool provides a single-user interface for Project Leads to manage timelines and generates secure, live view links for customers, ensuring they always see the latest status without manual reporting.

---

## Core Vision

### Problem Statement

We currently lack a dedicated tool to effectively share project timelines with our customers. Existing methods (screenshots, emails, or complex PM tools) fail to provide a "live," up-to-date view associated with the project, leading to communication gaps and satisfied customers relying on stale information.

### Problem Impact

-   **Communication Gap:** Customers don't know the status unless manually informed.
-   **Stale Data:** Manual updates (e.g., sending a PDF) become outdated the moment they are sent.
-   **No specialized tool:** We strictly miss a facility designed for this specific "Client View" use case.

### Why Existing Solutions Fall Short

-   **Too Complex for Clients:** We can't ask customers to log into a JIRA or Asana just to see a date.
-   **No "Public View" Feature:** Most tools don't offer a simple, secure, read-only link for external stakeholders.

### Proposed Solution

A **Client-Facing Timeline Broadcaster**:
1.  **Shared internal maintenance:** A simple interface (single shared account) for Project Leads to update tasks and dates.
2.  **Live Customer View:** A persistent, up-to-date visual Gantt chart accessible via a unique link.
3.  **Zero-Friction Updates:** When a Lead updates a date, the customer sees it instantly.

### Key Differentiators

-   **Purpose-Built for Sharing:** The "Sharable Link" is the primary feature, not an afterthought.
-   **Single-Account Simplicity:** No user management overhead; just login and update.
-   **Live Sync:** Replaces static reports with dynamic, real-time views.

## Target Users

### Primary Users

#### 1. The Project Lead (Internal Admin)
-   **Role:** Project Manager or Team Lead responsible for delivery and client communication.
-   **Context:** Juggling multiple workstreams; hates administrative overhead and repetitive status reporting.
-   **Motivation:** Wants to set clear expectations at the start of a project and avoid "What's the status?" emails later.
-   **Pain Point:** Currently has to manually create and email timelines (PDF/Excel), which immediately become outdated.
-   **Success:** "I sent the link on Day 1, and the client never had to ask me for a schedule update again."

#### 2. The Customer (External Viewer)
-   **Role:** Client stakeholder or executive sponsor.
-   **Context:** Busy, external to the team's daily workflows. Does not want another login credentials.
-   **Motivation:** Needs reassurance that the project is on track and wants to know "When is X finishing?" without having to schedule a meeting.
-   **Success:** Clicking a bookmarked link and instantly seeing a clean, readable timeline.

### User Journey

#### The "Kickoff" Flow (Project Lead)
1.  **Creation:** Lead creates a new project: "Website Revamp Phase 1".
2.  **Definition:** Manually draws the high-level timeline and adds key tasks/milestones.
3.  **Sharing:** Generates the "Share Link" and includes it in the Welcome Email.
4.  **Maintenance:** As work progresses, Lead drags a task bar to a new date. (Done).

#### The "Check-in" Flow (Customer)
1.  **Curiosity:** Customer wonders, "Is the Design phase done yet?"
2.  **Access:** Clicks the link from the Welcome Email.
3.  **Validation:** Sees the live Gantt chart. "Ah, Design is 90% done, moving to Dev next week."
4.  **Satisfaction:** Closes the tab. Zero friction.

## Success Metrics

### User Success (The "Anti-Engagement" Metric)
Since the goal is efficiency, **less time spent** is better.
-   **Update Velocity:** Project Leads can update a project's timeline (e.g., drag a task, change a status) in **< 60 seconds**.
-   **Zero-Friction Access:** Customers can view the timeline in **1 click** (no login, no navigation steps).

### Business Objectives
-   **Communication Efficiency:** Eliminate ad-hoc "Status Update" emails. Success is defined by silence—clients have the info they need without asking.
-   **Standardization:** Migrate 100% of active project timelines from disparate Excel/PDF files to this unified tool.

### Key Performance Indicators (KPIs)
1.  **Metric:** Support Ticket/Email Volume regarding "Status".
    *   **Goal:** Reduce to near zero.
2.  **Metric:** Link Engagement.
    *   **Goal:** Confirm clients are actually viewing the links (unique views > 0 per week).
3.  **Metric:** Creation Time.
    *   **Goal:** New project setup (Create Project + Add 5 Tasks + Generate Link) takes **< 5 minutes**.

## MVP Scope

### Core Features
1.  **Authentication:** Simple Email/Password login for the single Project Lead account.
2.  **Project Dashboard:** Create, View, Rename, and Delete projects.
3.  **Visual Timeline Editor:**
    *   Manual Start/End date setting for Project Reference Line.
    *   CRUD operations for Tasks (Title, Status, Range).
    *   **Drag & Drop Interaction:** Visual moving/resizing of tasks on the timeline.
4.  **Sharing Engine:** Generate cryptographically secure, random public URLs (e.g., `/view/x82-92a`).
5.  **Client View:** Robust, mobile-friendly read-only Gantt display accessible via the public link.

### Out of Scope for MVP
To ensure rapid delivery and maintain "Simplexity":
*   **Multi-User Management:** Teams will share the admin credentials initially.
*   **Task Dependencies:** No auto-scheduling or "waterfall" logic.
*   **Notifications:** No email triggers; relying on pull-communication (checking the link).
*   **History/Undo:** Actions are immediate and destructive.
*   **Data Export:** No PDF/Excel export (the tool *is* the report).

### MVP Success Criteria
*   **Usability:** "Can I create a timeline and share it in < 2 minutes?"
*   **Reliability:** Share links must 100% work and show live data instantly.
*   **Adoption:** Team voluntarily abandoning spreadsheet timelines.

### Future Vision
If successful, V2 might introduce **Multiple Admin Accounts** (to remove shared password risk) and **Project Archiving**. However, we will strictly avoid adding "Project Management" features like assigning tasks or commenting, as those exist in other tools we specifically aim to complement, not replace.
