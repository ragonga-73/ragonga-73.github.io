---
title: "Online School Transport Child Safety Monitoring and Alert System"
date: 2026-02-20
tags: [android, firebase, firestore, mobile-development, system-design]
---

🔗 [View Source Code on GitHub](https://github.com/ragonga-73/ONLINE_SCHOOL_TRANSPORT_CHILD_SAFETY_MONITORING_AND_ALERT_SYSTEM)

## Overview

This project is a mobile-based safety monitoring system designed to improve visibility and accountability in school transport operations. The goal was to ensure that parents receive real-time confirmation when their children are picked up and dropped off from school transport vehicles.

The system focuses on safety, communication, and structured data tracking.

---

## Problem Statement

In many school transport systems, parents lack real-time confirmation about their child’s pickup and drop-off status. This creates anxiety and increases the risk of delayed incident detection.

The solution was to build a mobile application that:

- Captures pickup and drop-off events
- Notifies parents instantly
- Maintains structured student and vehicle records
- Allows emergency reporting

---

## Technologies Used

- **Java (Android Studio)**
- **Firebase Authentication**
- **Cloud Firestore**
- **Firebase Cloud Messaging**
- **Firebase Storage**

---

## Key Features

### 1. Live Tracking Interface
A real-time vehicle tracking screen allowing parents to monitor transport movement.

### 2. Pickup & Drop-off Confirmation
When a student boards or exits a vehicle:
- Event is recorded in Firestore
- A push notification is triggered
- Timestamp is stored for reporting

### 3. Role-Based Authentication
Users are assigned roles:
- Parent
- Driver
- Admin

Firebase Authentication and security rules were configured to enforce access control.

### 4. Messaging Interface
Parents can communicate directly with administrators or transport attendants.

### 5. Emergency Alert Button
Parents can raise urgent safety concerns through a dedicated alert feature.

---

## Architecture Decisions

### Firestore Data Modeling

Data was structured hierarchically:

- Students collection
- Vehicles collection
- Drivers collection
- Notifications subcollections

This structure ensured scalability and efficient queries.

---

## UI/UX Design Decisions

- Tab-based navigation for clean separation of features
- Minimalist design
- Gradient theme consistency
- Custom animated tab transitions
- Custom calendar view with highlighted period dates

---

## Challenges & Solutions

### Challenge: Real-time consistency
Solution: Used Firestore snapshot listeners for real-time updates.

### Challenge: Structured reporting
Solution: Stored pickup and drop-off timestamps in a structured format to enable reporting and historical analysis.

---

## Impact

- Improved parent visibility into transport operations
- Reduced uncertainty and communication delays
- Established a scalable structure for future expansion

---

## Key Learnings

- NoSQL data modeling at scale
- Android lifecycle management
- Real-time event-driven architecture
- Secure role-based access implementation
