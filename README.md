# Neptune Plumbing Estimation System (PES)

**Current Phase**: Scoping  
**Client**: [Neptune Plumbing and Heating](https://neptuneplumbing.net)  
**Project Start**: November 2025

---

## Project Overview

The Plumbing Estimation System (PES) is a unified digital platform designed to improve Neptune Plumbing and Heating's service and estimation workflow. The system eliminates re-keying, reduces intake delays, and standardizes quoting with WinSupply-backed materials data and guideline-driven checklists.

### Problem Statement

Neptune Plumbing's service teams routinely identify follow-up work that cannot be completed within the scheduled visit. Historically, technicians submit a "Not Completed" form (often PDFs, images, or ad-hoc notes) that the back office must interpret, verify, and convert into a customer-facing quote. This process creates delays, re-keying, and inconsistencies—especially around materials identification and missing site details.

### Solution

PES introduces two core components:

1. **PES Onsite** – A technician-friendly mobile web application for:
   - Creating digital "Not Completed" forms
   - Capturing photos, measurements, and customer signatures
   - Selecting materials using WinSupply-backed search
   - Creating "Change Order" forms
   - Referencing guideline documents

2. **PES Back-Office** – A structured desktop environment for:
   - Review, validation, and approval of submissions
   - Checklist-driven review workflow
   - Product matching and material validation
   - Generation of final quote artifacts (Excel, Word, Materials Request Spreadsheet)

---

## Key Contacts

### Client
- **Adam Wallenstein** - President
- **Michael Wallenstein** - Reviewer

### TomorrowToday LLC
- **Dave Foster** - Partner, CTO

---

## Project Goals

- Reduce re-keying and intake errors by capturing structured data at the source
- Improve materials accuracy and consistency via WinSupply-backed product selection
- Standardize reviews with guideline-driven checklists and explicit statuses
- Streamline generation and packaging of final quote artifacts

---

## Timeline

**Estimated Duration**: 7–8 weeks
- 5–6 weeks: Build phase
- 2 weeks: Joint beta testing

---

## Key Features

### PES Onsite (Mobile Web App)
- Digital "Not Completed" form creation
- Photo and measurement capture
- Customer signature capture
- WinSupply-backed material selection
- Change Order form creation with OCR support
- Guideline document reference library

### PES Back-Office (Desktop Web App)
- Structured review queue with explicit statuses (New, In Review, Canceled, Approved, Downloaded, Old)
- Checklist-driven review workflow
- Guideline-driven annotations and validation
- Product matching and SKU validation
- Quote generation (Internal Excel, Client Word Doc, Materials Request Spreadsheet)
- User authentication and role management (admin and standard users)
- Configurable templates for quote generation

### System Capabilities
- WinSupply product data integration
- Guideline and checklist library
- OCR for Change Order form pre-population
- Session-based authentication with emailed One-Time Password (OTP)
- Configurable session lifetime
- Operational alerts for system issues

---

## Out of Scope

- Chatbot functionality (referenced in discovery documents as potential future capability)
- Post-launch support (beyond what is defined in Discovery document)
- Travel expenses

---

---

## System Architecture

The application follows a client-server architecture, dividing responsibilities between a React frontend and a FastAPI backend using Domain-Driven Design (DDD) principles.

### Architecture Overview

- **Frontend (React + Vite)**: A unified web application that serves both the **PES Onsite** (mobile-optimized for field technicians) and **PES Back-Office** (desktop-optimized for review and management).
- **Backend (FastAPI)**: Implements DDD with isolated `domain/models`, `domain/repositories`, and `domain/services`. 
- **Data Persistence**: Uses repositories for data management, currently configured for rapid prototyping and file-based caching.
- **External Integrations**:
  - **WinSupply Search**: Uses Playwright for headless scraping of the WinSupply website to iteratively extract facets and search products.
  - **AI / LLM / OCR**: Uses LangChain and OpenAI/Google GenAI for parsing handwritten forms and extracting structure.

### Access & User Roles
1. **Technician**: Accesses mobile screens to submit "Not Complete" or "Change Order" forms.
2. **Back Office**: Reviews, adjusts, and finalizes forms submitted by technicians. Forms are locked from technician edits once submitted.
3. **Admin**: Manages system settings and user administration.

---

## Project Structure

```text
neptune-plumbing-estimator-2025/
├── notebooks/                 # Documentation and scoping documents
│   ├── discovery/             # Discovery phase documents
│   ├── scoping/               # Architecture and SOW requirements
│   └── toto-code-review/      # Code review materials
├── src/                       # Application Source Code
│   ├── backend/               # FastAPI backend
│   │   ├── domain/            # Domain models, repositories, services (DDD approach)
│   │   ├── email_bot/         # Email processing worker
│   │   ├── prompts/           # LLM prompts
│   │   ├── routes/            # API endpoints
│   │   ├── templates/         # Export templates (Word, Excel)
│   │   └── workers/           # Background workers
│   ├── frontend/              # React/Vite frontend (PES Mobile and Back-Office)
│   ├── persist/               # Initial data models and seed data
│   └── totodev/               # Development utilities
├── tests/                     # Pytest suite
│   ├── fixtures/              # Test fixtures
│   ├── repositories/          # Repository tests
│   └── services/              # Service tests
├── volatile/                  # Temporary files and credentials (git-ignored)
├── docker-compose.yml         # Container configuration
├── pyproject.toml             # Python dependencies and project settings
└── README.md                  # This file
```

---

## Additional Information

### LucidSpark Board
[Project Collaboration Board](https://lucid.app/lucidspark/a032c081f-e4b2-4e09-8094-a7cbc6dab0e5/edit?viewport_loc=-25576%2C-14812%2C38568%2C21524%2C0_0&invitationId=inv_ba4d5357-bd17-4d7d-b75b-f126b8409326)

### Development Environment
- **Python Version**: 3.11.9
- **Package Manager**: `uv`
- **Virtual Environment**: `.venv/` (activated with `source .venv/bin/activate`)
- **Source Path**: `src/` is in PYTHONPATH
- **Testing**: pytest (tests located in `tests/`)
- **Configuration**: Environment-specific config via `config._THIS_IS_DEVDAVE_ENV_.sh`

### Hosting
Production environment will be hosted within TomorrowToday's managed hosting infrastructure.

---

## Notes

- This is a scoping/discovery project repository
- All features, workflows, and data models are defined in the Discovery document
- The Discovery document is incorporated by reference into the SOW and governs the functional scope
