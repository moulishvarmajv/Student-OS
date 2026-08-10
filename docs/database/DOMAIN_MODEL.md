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

# 4. Opportunity Radar Domain

The Opportunity Radar provides a unified system for discovering, organizing, filtering, recommending, saving, and applying to student opportunities.

## Core Entities

- organizations
- recruiters
- opportunity_sources
- opportunities
- skills
- opportunity_skills
- tags
- opportunity_tags
- opportunity_eligibility
- opportunity_departments
- student_saved_opportunities
- applications
- opportunity_recommendations
- opportunity_feedback

## Core Relationships

```text
ORGANIZATION
   |
   +----< OPPORTUNITY
   |          |
   |          +----< OPPORTUNITY_SKILL >---- SKILL
   |          |
   |          +----< OPPORTUNITY_TAG >---- TAG
   |          |
   |          +---- OPPORTUNITY_ELIGIBILITY
   |          |
   |          +----< OPPORTUNITY_DEPARTMENT >---- DEPARTMENT
   |          |
   |          +----< APPLICATION >---- STUDENT
   |          |
   |          +----< STUDENT_SAVED_OPPORTUNITY >---- STUDENT
   |          |
   |          +----< OPPORTUNITY_RECOMMENDATION >---- STUDENT
   |          |
   |          +----< OPPORTUNITY_FEEDBACK >---- STUDENT
   |
   +----< RECRUITER

OPPORTUNITY_SOURCE
   |
   +----< OPPORTUNITY


# 5. Collaboration Network Domain

The Collaboration Network enables students to find teammates, collaborators, study partners, mentors, and project members.

## Core Entities

- projects
- project_members
- project_skills
- project_join_requests
- teams
- team_members
- collaboration_requests
- student_connections
- mentor_profiles
- mentorship_requests
- study_groups
- study_group_members
- collaboration_recommendations

## Core Relationships

```text
STUDENT
   |
   +----< PROJECT_MEMBER >---- PROJECT
   |                              |
   |                              +----< PROJECT_SKILL >---- SKILL
   |                              |
   |                              +----< PROJECT_JOIN_REQUEST
   |                              |
   |                              +----< TEAM
   |                                      |
   |                                      +----< TEAM_MEMBER >---- STUDENT
   |
   +----< COLLABORATION_REQUEST
   |
   +----< STUDENT_CONNECTION
   |
   +---- MENTOR_PROFILE
   |          |
   |          +----< MENTORSHIP_REQUEST >---- STUDENT
   |
   +----< STUDY_GROUP_MEMBER >---- STUDY_GROUP
   |
   +----< COLLABORATION_RECOMMENDATION
