# 🏆 Online Judge Problems Handler

<div align="center">

![Platform](https://img.shields.io/badge/Platform-Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Language](https://img.shields.io/badge/C%23-.NET-512BD4?style=for-the-badge&logo=csharp&logoColor=white)
![UI](https://img.shields.io/badge/UI-Windows%20Forms-68217A?style=for-the-badge&logo=dotnet&logoColor=white)
![Database](https://img.shields.io/badge/Database-MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-28a745?style=for-the-badge)

**A full-featured backend management system for curating, reviewing, and publishing competitive programming problems — built for seamless integration with online judge platforms.**

</div>

---

## 📌 Table of Contents

- [Overview](#-overview)
- [System Architecture & Workflow](#-system-architecture--workflow)
- [User Roles & Responsibilities](#-user-roles--responsibilities)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [Database Design Highlights](#-database-design-highlights)
  
---

## 🧭 Overview

The **Online Judge Problems Handler** is a desktop application that simulates and manages the complete lifecycle of a competitive programming problem — from initial submission by a problem setter, through multi-level review, all the way to final contest-ready approval.

This project addresses a real-world need in competitive programming communities (like Codeforces, ICPC regional judges, etc.) where problem quality control requires a structured, role-based pipeline involving multiple stakeholders.

> 💡 **Core Goal:** Eliminate ad-hoc problem management and replace it with a structured, auditable, role-driven workflow that ensures every contest problem meets quality standards before publication.

---

## 🔄 System Architecture & Workflow

```
Problem Setter
     │
     │  Submits Problem
     ▼
Co-ordinator ◄──────────────────────────────────────────┐
     │                                                   │
     │  Accept / Reject / Provide Guidance               │
     ▼                                                   │
Sub Co-ordinator                                         │
     │                                                   │
     ├──► Assigns to ──► Problem Setter (revisions)      │
     ├──► Assigns to ──► Test Case Generator             │
     ├──► Assigns to ──► Tester                          │
     └──► Assigns to ──► Editorial Writer                │
                                                         │
     All Tasks Completed & Approved ────────────────────►┘
                                                         │
                                               Final Problem Pool
                                                         │
                                               Co-ordinator Arranges Contest
```

> 📐 **For a comprehensive visual understanding of the system, detailed UML diagrams are available in the [`/docs`](./docs) directory, including:**
>
> - **[Use Case Diagram](docs/Use-Case-Diagram.png)** — illustrates all actor interactions and system boundaries across every user role.
> - **[Class Diagram](docs/Class-Diagram.png)** — defines the object-oriented structure, entity relationships, and core system components.
> - **[Activity Diagram](docs/Activity-Diagram.png)** — maps the end-to-end flow of a problem through the entire curation and approval pipeline.
> - **[Package Diagram](docs/Package-Diagram.png)** — presents the high-level modular organization of the system, showing how components and namespaces are grouped and their dependencies structured.
>
> *Reviewing these diagrams is strongly recommended for a full picture of the system's architecture and design decisions.*

---

## 👥 User Roles & Responsibilities

| Role | Access Level | Responsibilities |
|------|-------------|-----------------|
| **Co-ordinator** | 🔴 Superior / Admin | Accept or reject problems, provide guidance, distribute tasks to Sub Co-ordinators, arrange final contests |
| **Sub Co-ordinator** | 🟠 Intermediate | Assign tasks to Problem Setters, Testers, and Generators; review feedback; supervise problem progress |
| **Problem Setter** | 🟡 Contributor | Create and submit new problems; revise based on feedback from Co-ordinators and Sub Co-ordinators |
| **Tester** | 🟢 Reviewer | Verify problem correctness; test against edge cases; report issues back to Sub Co-ordinator |
| **Test Case Generator** | 🔵 Contributor | Generate comprehensive test cases after a problem receives preliminary acceptance |
| **Editorial Writer** | 🟣 Contributor | Write detailed editorial/solution explanations after final problem acceptance |

---

## ✨ Key Features

### 🔐 Role-Based Access Control
- Each user type has a tailored dashboard with only the relevant permissions and actions visible.
- Secure login system with role-specific session management.

### 📋 Problem Lifecycle Management
- Full CRUD operations for problems (Create, Read, Update, Delete).
- Multi-stage approval pipeline with status tracking at every step.
- Audit trail: every action (accept, reject, feedback) is logged with timestamps.

### 💬 Feedback & Communication System
- Co-ordinators and Sub Co-ordinators can leave structured feedback on any problem.
- Problem Setters can view revision requests and resubmit updated versions.

### 📊 Task Distribution Engine
- Sub Co-ordinators can assign and reassign tasks dynamically.
- Real-time status updates reflect the current state of each problem in the pipeline.

### 🏁 Contest Preparation Module
- Co-ordinators can compile a curated list of fully approved problems.
- Built-in tools to organize problems by difficulty, topic, and status for contest arrangement.

### ✅ Data Validation Layer
- Client-side and database-level validation ensures data integrity throughout the system.
- Prevents duplicate submissions and enforces required fields at every stage.

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend / UI** | Windows Forms Application (WinForms) |
| **Backend Logic** | C# (.NET Framework) |
| **Database** | MySQL |
| **Data Access** | ADO.NET (MySQL Connector) |
| **IDE** | Visual Studio |

---

## 🗄 Database Design Highlights

- **Normalized relational schema** — minimizes redundancy across Users, Problems, Tasks, Feedbacks, and Contests tables.
- **Foreign key constraints** enforce referential integrity across all role-to-problem relationships.
- **Status flags and timestamps** on every problem record enable complete lifecycle tracking.
- **Efficient query design** — stored procedures and parameterized queries used for core operations to prevent SQL injection and improve performance.

---

