# HHA504 Final Project: Cloud Integration Mini-Capstone

**Referral Intake & Tracking System (GCP)**

## Overview

This project presents the design of a cloud-based referral intake and tracking system for a healthcare clinic. The goal is to demonstrate how multiple cloud services can be integrated to support a realistic healthcare workflow using concepts learned throughout the course.

This submission follows the **Design-Only Track**, with a defined use case, architecture diagram, implementation plan, and reflection.

---

## Project Structure

```
hha504_final/
│
├─ README.md                 # High-level overview and instructions (this file)
├─ use_case.md               # Healthcare use case description and workflow
├─ architecture_plan.md      # Architecture design, service mapping, data flow
├─ architecture_diagram.png  # Visual architecture diagram
├─ reflection.md             # Reflection on design choices and learning
│
```

---

## How to Review This Project

### 1. Read the Use Case

Start with **`use_case.md`** to understand:

* The healthcare problem being addressed
* Who the system is for (clinic staff, schedulers, managers)
* What types of data would be used in a real implementation
* The step-by-step workflow of the referral process

---

### 2. Review the Architecture Design

Open **`architecture_plan.md`** to see:

* A table mapping each part of the system to specific GCP services
* A narrative explaining how data flows through the system
* High-level discussion of security, governance, and cost considerations

Refer to **`architecture_diagram.png`** alongside this file to visually follow the system components and their interactions.

---

### 3. Read the Reflection

The **`reflection.md`** file discusses:

* Which parts of the design felt most comfortable based on course content
* Areas that were more challenging or uncertain
* Alternative approaches that were considered
* What could be improved or expanded with more time and experience

---

## Cloud Services Used (Design)

This project design integrates the following GCP services:

* **Compute Engine VM** — hosts a Flask application (access layer)
* **Cloud Storage** — stores uploaded referral documents
* **Cloud SQL (MySQL)** — stores structured referral and status data
* **Cloud Functions** — handles event-driven automation
* **Cloud Scheduler** — supports daily overdue referral checks
* **Cloud Logging** — provides basic monitoring and logs

These services were selected to align closely with course assignments and learning objectives.

---

## Notes on Data and Security

This project is a design and educational exercise only.
No real patient data is used or required.

The use case explains what types of data *would* be involved in a real healthcare deployment and includes high-level considerations for handling sensitive information responsibly.

