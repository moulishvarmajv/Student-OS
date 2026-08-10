# Student OS — Entity Relationship Model

## 1. Purpose

This document defines the approved Entity Relationship Model for the Student OS database.

The system is initially deployed for IIIT Kottayam but uses a multi-college architecture.

---

# 2. Identity Relationships

```text
COLLEGE 1:N USER
COLLEGE 1:N DEPARTMENT

DEPARTMENT 1:N STUDENT
DEPARTMENT 1:N FACULTY

USER 1:0..1 STUDENT
USER 1:0..1 FACULTY

USER N:N ROLE
