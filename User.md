# User Roles, Permissions, and Authorization

This document defines the comprehensive user ecosystem within our Gamified Learning Platform. It breaks down granular roles, specific permissions, and provides a clear authorization matrix for platform governance.

---

## 1. Granular Role Specifications

### 🧑‍🎓 Student (Learner)
The primary consumer of the platform, focused on upskilling through gamified learning.
- **Core Focus**: Consuming content, completing challenges, climbing the leaderboard, and earning badges.
- **Data Ownership**: Owns their personal profile, enrollment history, and payment ledger. Can only view public data of other users (like Leaderboard stats).

### 👨‍🏫 Mentor (Instructor/Creator)
Industry professionals and educators who create and moderate content.
- **Core Focus**: Creating courses, reviewing student submissions, hosting Q&A sessions, and answering doubts.
- **Data Ownership**: Owns the courses they create. Can view progress data *only* for students enrolled in their specific courses.

### 🛡️ Administrator (Moderator)
Platform managers responsible for maintaining content quality and handling disputes.
- **Core Focus**: Reviewing reported content (spam/abuse), processing refund requests, and managing community health.
- **Data Ownership**: Can view and edit all courses, process transactions, and moderate users, but cannot alter core gamification algorithms or system settings.

### 👑 Super Admin
The platform owners and system architects.
- **Core Focus**: Global platform configuration, financial auditing, API management, and role assignment.
- **Data Ownership**: Full unrestricted CRUD (Create, Read, Update, Delete) access to all database collections, including destructive actions.

---

## 2. Permissions Specification

Permissions are mapped to specific database resources and platform actions.

| Resource | Action | Description |
| :--- | :--- | :--- |
| **Profile** | `profile:read` | View a user's public profile and badges. |
| | `profile:update:own` | Edit own profile details. |
| | `profile:delete:own` | Delete own account (GDPR compliance). |
| **Course** | `course:read` | View course details and syllabus. |
| | `course:create` | Create a new course draft. |
| | `course:update:own`| Edit a course authored by the user. |
| | `course:delete:own`| Unpublish a course authored by the user. |
| | `course:moderate` | Force-unpublish or edit any course violating guidelines. |
| **Enrollment**| `enroll:create` | Enroll in a course (often requires payment success). |
| | `enroll:read:own` | View own course progress. |
| | `enroll:read:org` | View progress of students in a specific mentor's course. |
| **Payments** | `payment:create` | Initiate a checkout session. |
| | `payment:read:own` | View own transaction history. |
| | `refund:request` | Submit a refund request. |
| | `refund:process` | Approve or reject a refund request. |
| **Admin** | `role:assign` | Promote or demote users (e.g., Student -> Mentor). |
| | `system:config` | Change global variables (e.g., XP multipliers). |

---

## 3. Authorization Matrix

This matrix defines exactly which roles have access to which permissions. 
*(Key: ✅ = Allowed, ❌ = Denied, 👤 = Allowed only on own/owned resources)*

| Permission Category | Action | Student | Mentor | Admin | Super Admin |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **Users & Profiles** | Read Public Profile | ✅ | ✅ | ✅ | ✅ |
| | Update Profile | 👤 | 👤 | ✅ | ✅ |
| | Delete Account | 👤 | 👤 | ❌ | ✅ |
| **Courses** | Read Course | ✅ | ✅ | ✅ | ✅ |
| | Create Course | ❌ | ✅ | ✅ | ✅ |
| | Update Course | ❌ | 👤 | ✅ | ✅ |
| | Delete Course | ❌ | 👤 | ✅ | ✅ |
| **Enrollments & Learning**| Enroll in Course | ✅ | ❌ | ❌ | ✅ |
| | View Progress | 👤 | 👤 | ✅ | ✅ |
| | Grade/Review Submissions| ❌ | 👤 | ✅ | ✅ |
| **Payments & Refunds** | Make Payment | ✅ | ❌ | ❌ | ✅ |
| | View Ledger | 👤 | 👤 | ✅ | ✅ |
| | Request Refund | 👤 | ❌ | ❌ | ❌ |
| | Process Refund | ❌ | ❌ | ✅ | ✅ |
| **System Administration** | Assign Roles | ❌ | ❌ | ❌ | ✅ |
| | Configure Global XP Rules| ❌ | ❌ | ❌ | ✅ |

---

## Team Contributions

- **Aashika Jain** - Feature thinking + MVP Definition
- **Abhishek Joy** - Wireframes + Workflow Diagram
- **Agampreet Singh** - Code & Database Architecture
