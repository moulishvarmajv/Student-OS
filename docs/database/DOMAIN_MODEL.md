# Student OS — Database Domain Model

## 1. Purpose

This document defines the initial database domain model for Student OS.

The first implementation targets IIIT Kottayam, while the database architecture is designed to support multiple colleges in the future.

---

# 2. Database Domains

Student OS is divided into the following database domains:

1. Identity & Access
2. College / Organization
3. Academic
4. Student Profile
5. Opportunities
6. Collaboration
7. Clubs & Communities
8. Events
9. Companies & Recruiters
10. Notifications
11. LMS Integration
12. AI / Knowledge Base
13. Audit & Security

This document currently defines domains 1–3.

---

# 3. Multi-Tenant Architecture

The root organizational entity is `college`.

Every college-owned entity must be associated with a college.

```text
COLLEGE
   |
   +-- DEPARTMENT
   +-- USER
   +-- COURSE
   +-- CLUB
   +-- EVENT
   +-- DOCUMENT
   +-- OPPORTUNITY
   +-- ...

