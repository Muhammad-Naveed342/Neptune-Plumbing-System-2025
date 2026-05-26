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

## Reference Documents

- **[Plumbing Estimation Discovery Phase Recommendations](./notebooks/discovery/deliverable/Plumbing%20Estimation%20Discovery%20Phase%20Recommendations.md)** (October 28, 2025) - Detailed functionality and feature scope
- **[Statement of Work (SOW)](./notebooks/scoping/REQ_SOW.md)** (November 7, 2025) - Contract and scope definition

---

## Project Structure

```
neptune-plumbing-estimator-2025/
├── notebooks/
│   └── scoping/
│       ├── arch/              # Architecture documentation
│       ├── discovery/         # Discovery phase documents
│       └── REQ_SOW.md        # Extracted SOW requirements
├── volatile/                  # Temporary files (git-ignored)
│   ├── tmp/                  # Temporary working files
│   └── credentials/          # Credentials (git-ignored)
└── README.md                 # This file
```

---

## Additional Information

### LucidSpark Board
[Project Collaboration Board](https://lucid.app/lucidspark/a0dc081f-e4b2-4e09-8094-a7cbc6dab0e5/edit?viewport_loc=-25576%2C-14812%2C38568%2C21524%2C0_0&invitationId=inv_ba4d5357-bd17-4d7d-b75b-f126b8409326)

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
