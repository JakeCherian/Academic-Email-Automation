# Academic Email Automation

## Smart Email Management System for Students using FastAPI, UiPath RPA, and LLMs

### Overview

This project demonstrates an intelligent email-automation platform designed to help students manage the overwhelming volume of placement-related communication. Students at VIT receive dozens of emails every week containing recruitment announcements, deadlines, shortlists, and general academic notifications. Monitoring these manually is time-consuming and often leads to missed opportunities.

This system automates the entire workflow:

* Extracting emails
* Classifying important messages
* Performing eligibility checks
* Reading shortlist/selection attachments
* Summarising long emails using an LLM
* Generating ICS calendar invites via UiPath
* Displaying all results through a clean web interface

The solution integrates **UiPath RPA** for inbox automation and **FastAPI + SQLite + HTML/JS** for backend and frontend logic, creating a fully functional end-to-end academic email assistant.

---

# Table of Contents

1. [Project Motivation](#project-motivation)
2. [Key Features](#key-features)
3. [Architecture](#architecture)
4. [Tech Stack](#tech-stack)
5. [System Workflow](#system-workflow)
6. [UiPath Workflow Integration](#uipath-workflow-integration)
7. [Email Classification Logic](#email-classification-logic)
8. [Limitations & Future Work](#limitations--future-work)
9. [Contributors](#contributors)

---

# Project Motivation

Students are exposed to an overwhelming volume of daily emails, and manually identifying critical placement-related communication is inefficient and error-prone. Important details such as eligibility criteria, deadlines, interview schedules, and shortlists are often missed.

This project solves that problem by creating an automated system that transforms raw inbox data into **structured, actionable insights** that students can trust.

---

# Key Features

### 1. Automated Email Extraction (UiPath)

* Reads unread inbox emails
* Downloads and scans attachments
* Sends extracted data to backend for analysis

### 2. Intelligent Email Classification

Emails are automatically categorized into:

1. **New Company Announcement**
2. **Shortlist / Round Progression**
3. **Final Selection**
4. **General Academic Notices**

Classification uses both keyword logic and LLM-based semantic understanding.

### 3. Eligibility Checker

* Extracts CGPA, branch, 10th/12th marks from the user profile (SQLite)
* Compares with company criteria
* Displays “Eligible” / “Not Eligible” instantly

### 4. Excel Shortlist Processing

* Parses Excel sheets automatically
* Checks if student's name or registration number appears
* Works even when names are inside attachments

### 5. LLM-Based Email Summaries

Long announcements are summarized intelligently to quickly surface key information.

### 6. Calendar Automation (ICS Generation)

Via UiPath:

* Automatically identifies dates from emails
* Generates ICS files
* Sends them to student mailbox for one-click calendar import

### 7. Web Dashboard

Includes:

* Signup & login
* User profile view
* Dashboard showing categorized emails
* Embedded summaries, calendar buttons

---

# Architecture

<div class="image-container">
       <img src="Email Automation Architecture.jpg" alt="Logo" width="600" height="300"> 
    </div>
    
---

# Tech Stack

### Backend

* **Python**
* **FastAPI**
* **SQLite (users.db)**
* **SQLAlchemy ORM**

### Frontend

* HTML
* CSS
* JavaScript

### Automation (RPA)

* **UiPath Studio**
* Email Activities
* Excel Processing
* File Handling
* ICS Event Creation

### AI / NLP

* LLM-based summarization
* Semantic extraction
* Deadline recognition

# System Workflow

### 1. UiPath Workflow

* Fetch unread emails
* Extract content & attachments
* Send POST request to FastAPI

### 2. FastAPI Processing

* Parse email
* Detect category
* Run eligibility logic
* Scan Excel files if needed
* Generate summary using NLP
* Store results into SQLite DB

### 3. User Dashboard

* Students view categorized alerts
* Can add deadlines to calendar
* Can view summaries & decisions instantly

---

# UiPath Workflow Integration

Two main workflows are used:

### 1. **Email Extraction Bot**

* Reads student inbox
* Downloads Excel/PDF attachments
* Sends content to FastAPI using HTTP Request activity

### 2. **ICS Calendar Bot**

* Creates ICS file
* Sends it to student mailbox
* Triggered via backend request

The workflows correspond to `.nupkg` files included in the repo.

---

# Email Classification Logic

### **Type 1 — Company Announcements**

* Extracts CGPA, backlog criteria
* Matches with user data
* Returns **Eligible / Not Eligible**


### **Type 2 — Shortlist Notifications**

* Reads Excel attachments
* Checks for student registration number


### **Type 3 — Final Selection**

* Detects student name in selection lists


### **Type 4 — General Academic Notices**

* LLM generates readable summary


---

# Limitations & Future Work

### Current Limitations

* Not yet deployed for large-scale multi-user usage
* Limited to VIT-style email formats
* Backend uses SQLite, not cloud database
* LLM integration is local; cloud models can be added later

### Planned Improvements

* Mobile app with push notifications
* Multi-user authentication system
* Cloud deployment with PostgreSQL
* Advanced deadline extraction with NER
* Batch processing of emails

---

# Contributors

| Name                       |Email ID                         |
| -------------------------- | --------------------------------|
| **Nidhish Balasubramanya** | nidhishbalasubramanya@gmail.com |
| **A Nathania Rachael**     | nathaniarachael@gmail.com       |
| **Allen Reji**             | allenreji@gmail.com             |
| **Jacob Cherian M**        | jakecherian10@gmail.com         |





