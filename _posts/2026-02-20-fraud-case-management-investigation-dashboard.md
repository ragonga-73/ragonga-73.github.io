---
title: "Fraud Case Management & Investigation Dashboard"
date: 2026-02-20
tags: [javascript, firestore, dashboard, workflow-design, system-architecture]
---

# Fraud Case Management & Investigation Dashboard

## Overview

This project is a web-based administrative dashboard designed to manage fraud investigations across multiple branches and subsidiaries.

The primary goal was to create a structured, scalable system for tracking investigations from assignment to report completion.

---

## Problem Statement

Fraud investigations often lack standardized workflow tracking. Cases can become disorganized, difficult to assign, and challenging to monitor across multiple investigators.

The solution was to build a dashboard that:

- Assigns cases to investigators
- Tracks investigation milestones
- Maintains hierarchical branch structures
- Generates structured reports

---

## Technologies Used

- **JavaScript (Modular Firebase SDK)**
- **Cloud Firestore**
- **HTML / CSS**
- **Role-based UI logic**

---

## Key Features

### 1. Hierarchical Data Structure

Data was stored in Firestore hierarchically:

- Countries
  - Branches
    - Cases
      - Investigation milestones

This improved organization and scalability.

---

### 2. Multi-Investigator Assignment

Implemented a multi-select dropdown that:
- Allows assigning one or multiple investigators
- Stores assignments as arrays in Firestore
- Supports collaborative investigations

---

### 3. Investigation Progress Milestones

Each case includes structured stages:

- Evidence Collection
- Interviews Conducted
- Evidence Analysis
- Report Drafting

This transformed investigations into measurable workflows.

---

### 4. Dynamic User Cards

Horizontally scrollable user cards allow administrators to:
- Select investigators
- Load user data dynamically
- Edit or manage assignments

---

## Architecture Decisions

### Structured Workflow Modeling

Instead of storing simple case notes, I designed milestone-based progress tracking to provide visibility and measurable stages.

### Modular JavaScript

Used modular Firebase SDK to maintain separation of concerns and scalability.

---

## Challenges & Solutions

### Challenge: Managing complex data relationships
Solution: Used nested collections and structured referencing in Firestore.

### Challenge: Flexible investigator assignment
Solution: Implemented array-based storage for multiple assignees.

---

## Impact

- Improved investigation visibility
- Reduced workflow ambiguity
- Enabled structured reporting
- Increased scalability across branches

---

## Key Learnings

- Designing scalable admin systems
- Translating business processes into technical workflows
- Data hierarchy modeling in NoSQL
- Building dynamic UI components
