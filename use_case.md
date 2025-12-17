# Referral Intake and Tracking System (Cloud-Based)

## Problem Statement

Referral management is a common operational challenge in outpatient and specialty clinics. Referrals are often received through fax, email, or manual uploads, then tracked in spreadsheets or paper systems. This process makes it easy for referrals to be delayed, lost, or never scheduled. This problem is commonly referred to as *referral leakage*. When referrals are not followed up in a timely manner, patients may experience delays in care, worsening health outcomes, and frustration with the healthcare system.

This project proposes a cloud-based referral intake and tracking system that helps clinics reliably receive referrals, store and organize supporting documents, track referral status end-to-end, and identify overdue referrals before patients are forgotten about. 


## Users

The primary users of the system include:

* **Referring clinic staff** (front desk, MA, referral coordinator) who submit referrals and upload supporting documents.
* **Specialty clinic staff** who review referrals and update status (received, scheduled, completed, closed).
* **Schedulers** who coordinate appointment booking and may request missing documentation.
* **Clinic managers** who monitor throughput, backlog, and overdue referrals.

---

## Data Sources and Data Types (Real-World Scenario)

In a real implementation, this system would manage a mix of structured referral data and unstructured documents. These inputs would typically come from the EHR, eFax systems, and external provider offices.

### 1) Referral Intake Data (Structured)

Examples of fields that would be captured and stored in the database:

* **Patient identifiers (PHI)**: name, date of birth, MRN, contact information
* **Referral details**: specialty requested, referring provider, receiving clinic, reason for referral, urgency/priority
* **Clinical context (potential PHI)**: problem list summary, diagnosis codes (ICD-10), relevant vitals, key history notes
* **Operational fields**: referral creation date, due date/SLA target, status, assigned coordinator, scheduling notes

### 2) Supporting Documents (Unstructured)

Documents would typically be uploaded as PDF or images and stored in cloud object storage:

* Recent clinical note from referring provider (PHI)
* Lab results, imaging reports, pathology reports (PHI)
* Insurance authorization forms (PHI/PII)
* Prior visit summaries or discharge notes (PHI)

### 3) System-Generated Metadata (Operational/Audit)

Generated automatically as the referral moves through the workflow:

* Status change timestamps (received → in review → scheduled → completed)
* User/action logs (who updated status and when)
* Document upload metadata (file type, size, upload time)
* Overdue flags (days past due date)

---

## Basic Workflow (End-to-End Data Flow)

1. A referring clinic submits a referral through a web form or an API endpoint, entering referral details and attaching supporting documents.
2. The system stores the uploaded document(s) in cloud storage under a structured path (e.g., by referral ID and date).
3. The system writes the referral record into a managed SQL database, including a link to the stored document(s).
4. A serverless function is triggered when documents are uploaded to validate the file (type/size), confirm receipt, and update document metadata in the database.
5. Specialty clinic staff review the referral and update the referral status as it progresses (e.g., **RECEIVED**, **IN_REVIEW**, **SCHEDULED**, **COMPLETED**, **CLOSED**).
6. A scheduled job runs daily to identify referrals that have exceeded a due date or SLA target, flags them as overdue, and surfaces them to staff for action.
7. Staff can view referral queues by status (e.g., “received but not reviewed”) and quickly identify overdue or missing-document referrals.

---

## Why This Use Case Matters

This system addresses a real operational pain point that affects both quality of care and patient access. By centralizing referral intake, document handling, and status tracking, clinics can reduce lost referrals, shorten waits for appointments and improve accountability. The cloud-based design supports reliability while enabling automation that reduces manual work.

