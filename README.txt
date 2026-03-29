------------------------------------------------------------------
README for Electronic Patient Management System
------------------------------------------------------------------

To access the executable file:

EPMS1.exe

Login for administrator account:
username: admin
password: demo1234

Dummy patient data:
Medicare number/unique identifier: 1234567890

# EPMS — Electronic Patient Management System
**C++ | Qt6 | SQLite | TCP Networking | Healthcare Software**

A full-featured clinical desktop application for managing patient registration, medical records, appointments, inter-clinic document transfer, electronic messaging, and invoicing. Built from scratch in C++ using the Qt framework with a three-tier architecture and SQLite database backend.

Developed as a group software engineering project at Torrens University (Master of Software Engineering, AI), designed to professional clinical software standards including role-based access control, patient consent management, and HL7 awareness.

---

## Features

### Patient Management
- Register new patients with personal and medical details
- Search patients by Medicare number / unique identifier
- Upload and display patient photos
- Patient consent management — records can be hidden or restored based on consent status
- Edit, update, and soft-delete patient records

### Patient Letters & Images
- Create, view, and manage clinical letters linked to patient records
- Upload and manage patient medical images
- Print support for clinical documentation

### Appointment Scheduling
- Create and manage appointments per patient
- Appointment history visible across the system
- Shareable between clinic instances via shared SQLite database

### Invoice Generation
- Receptionist-facing invoice creation for patient billing
- Linked to patient records and appointment history

### Electronic Messaging (Chat)
- Real-time TCP/HTTP-based messaging between doctors and receptionists within a clinic
- Client-server architecture with automatic port assignment

### Role-Based Access Control
| Role | Access |
|---|---|
| Administrator | Full unrestricted access |
| Doctor | Patient records, letters, images, appointments |
| Receptionist | Patient search, appointments, invoicing |

---

## Architecture

```
┌─────────────────────────────────────┐
│         Qt6 GUI Frontend            │
│   (Widgets, Forms, Print Support)   │
└────────────────┬────────────────────┘
                 │
┌────────────────▼────────────────────┐
│         Application Logic           │
│  (C++ classes, Qt signals/slots)    │
└────────────────┬────────────────────┘
                 │
┌────────────────▼────────────────────┐
│         SQLite Database             │
│  (Shared via network file system    │
│   for multi-instance access)        │
└─────────────────────────────────────┘
```

TCP socket layer handles real-time clinic messaging independently of the database layer.

---

## Tech Stack

- **Language:** C++
- **Framework:** Qt 6 (Widgets, SQL, Network, PrintSupport, GUI)
- **Database:** SQLite (network file system shareable)
- **Networking:** TCP/HTTP via Qt6 Network for real-time chat
- **Build Tool:** Qt Creator
- **Platform:** Windows 10 (cross-platform compatible)

---

## Test Coverage

The application was tested against a comprehensive test plan covering:

| Module | Test Cases | Result |
|---|---|---|
| Login & Authentication | 5 | ✅ All Pass |
| Change Password | 6 | ✅ All Pass |
| Patient Search & Registration | 23 | ✅ All Pass |
| Patient Letters | Covered | ✅ All Pass |
| Patient Images | Covered | ✅ All Pass |
| Appointments | Covered | ✅ All Pass |
| Invoice Generation | Covered | ✅ All Pass |
| Chat / Messaging | Covered | ✅ All Pass |
| Non-Functional Requirements | Covered | ✅ All Pass |

Test severity classifications used: Critical, Important, Workaround.

---

## How to Run

### Pre-built Windows executable
Download the release package and run `EPMS1.exe`. All required Qt6 DLLs are included.

---

## Design Highlights

- **Patient consent first** — records cannot be accessed without consent; hidden records are protected from search
- **Soft delete** — patient records are hidden rather than permanently deleted, supporting re-registration
- **Shared database** — SQLite file can be placed on a network file system for multi-clinic, multi-instance access
- **HL7 aware** — designed with future HL7 integration in mind for inter-system interoperability
- **Print support** — clinical letters and documents printable directly from the application

---

## Future Enhancements

- HL7 integration for inter-system data exchange
- Mobile client for patient record viewing
- Cloud-hosted SQL Server for scalable multi-clinic deployment
- Third-party EMR system integration

---

## Author

**Kim Trieu**
Applied AI Engineer | LLM Evaluation | Healthcare AI
[LinkedIn](https://www.linkedin.com/in/ktrieu/) | Boston, MA
