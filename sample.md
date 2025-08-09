# MBC Scheduling, EHR, and Clinical System - Functional Requirements

## Overview
As a foundational component of the MBC Scheduling, EHR, and Clinical system, these functional requirements define the core capabilities needed to streamline patient intake, referral management, scheduling, clinical documentation, and supporting processes. These requirements directly address current pain points, such as manual dual entry and fragmented workflows, while promoting efficiency, data accuracy, and user-friendly interfaces for intake coordinators, schedulers, providers, and billing staff. Prioritization focuses on MVP features essential for house accounts like STR and LY, with desired enhancements noted for future scalability.

## 1. Patient Intake and Demographics

This module facilitates the efficient capture and management of patient demographic, insurance, and related information through an intuitive, tabbed interface that minimizes navigation and supports automated data population to eliminate redundancies.

### Patient Demographics Tab
- **Core Demographics Capture:**
  - Name (First, Middle Initial, Last)
  - Date of Birth (DOB) with auto-calculated Age
  - Sex (dropdown: Male, Female, Other)
  - Address (structured fields: Street, City, State, Zip Code, optional Address Line 2/Suite)
  - Phone Numbers (Home, Cell, Work)
  - Social Security Number (SSN)
  - Chart # automatically assigned starting from 1
  - Status dropdown (ACTIVE, NO-SHOW, DISCHARGED, DECEASED) with associated Status Date field
  - Emergency Contact details: Name and Phone (required), optional Relationship field

- **Patient Management Features:**
  - SMS Opt-Out toggle/checkbox for patient preferences
  - Patient Alerts for critical notifications (e.g., allergies, special needs)
  - Notes field with date/time stamps, types (DISPLAY for pop-up alerts, COMMON for general notes), user attribution, and editable content; displayed in reverse chronological order
  - Incomplete data indicated by red border and checkbox in upper right
  - Support for Consent Forms and HIPAA

### Insurance/Payer Tab
- **Insurance Details:**
  - Carrier, Subscriber ID, Group Number, Policy Holder (defaulting to patient where applicable)
  - Auto-populate Carrier Address and Phone from pre-configured directory upon selection
  - Patient Financial Class dropdown (MEDICARE, PRIVATE, PERSONAL INJURY, WORK COMP, SELF PAY/CASH) to drive conditional workflows
  - Collapsible sections for financial class-specific details to reduce screen clutter

- **Additional Party Information:**
  - Responsible Party/Attorney Information from searchable directory (supports firm names, auto-populates contact details, non-mandatory during initial intake)
  - Employer Name for Workers' Compensation cases (with optional address fields and directory-based auto-complete)

### Referrals Tab

#### Multi-Referral Capability
- Unlimited referrals per patient in numbered, collapsible sections (Referral #1, Referral #2, etc.)
- Expand All/Collapse All actions for quick review
- Add Referral button to append new blank referral entries
- Remove individual referrals via trash-can icon with confirmation prompt

#### Core Referral Fields (per referral)
- **RX Type** (dropdown) - Prescription/referral types (e.g., LAND, ACUP, AQUATIC, WORK CONDITIONING)
- **RX Date** (date picker) - Date referral was issued
- **Frequency × Duration** (text, max 110 characters) - Free-form entry for treatment frequency and duration
- **Referral Status** (dropdown) - Authorized, Denied Claim, Denied Body Part, Denied MPN, Denied Medical Necessity, OIA, Lien Pending, Lien Signed, Self Pay, Pending Approval, Hold
- **Approved Visits** (numeric) - Number of visits authorized
- **Authorization Number** (text, max 20 characters) - Payer/insurer authorization reference
- **Effective Date** (date picker) - Start date of referral validity
- **Expiration Date** (date picker) - End date of referral validity
- **Referring MD** (text with NPI search link) - Manual entry or lookup to auto-populate provider details
- **Treating Location** (dropdown) - Tied to scheduler's location master for billing place of service
- **Treating Provider** (dropdown) - From provider directory; required for scheduling and billing
- **ICD** (text/multi-code support) - ICD-10 codes relevant to referral (up to 12 codes)
- **Select Tags** (multi-select dropdown) - Classification tags for filtering, reporting, and marketing attribution

#### Additional Referral Metadata
- Referral Entry Date - System-captured date/time of record creation (for reporting)
- Flags/Checkboxes - Required Authorization, Lien, or OIA indicators (triggers automated daily flagged reports)
- Linked Documents - Upload/attach scanned/faxed/email referral documents directly to specific referral record

### General Patient Management
- Lookup existing patients by Name, DOB, or Medical Record Number (MRN)
- Clear workflows for creating new patient records and updating existing ones
- Validation to prevent duplicates
- Document upload (referral faxes/emails) and association with patient records
- **Desired:** Automated data entry from referral documents via OCR/parsing
- **Desired:** Patient web portal for self-service intake forms (kiosk functionality not required)

## 2. Scheduling Workflow

This module delivers flexible, visual scheduling tools tailored to multi-provider, multi-location environments, with color-coding and automation to support payer-specific needs.

### Core Scheduling Features
- Calendar View segmented by Provider and Location
- Color-coding of appointments by Payer Type (PI, Work Comp, Private) and Reason for Visit
- Support for multiple locations and providers with configurable availability
- Assign appointments to specific Provider Licenses for billing accuracy
- Capture Appointment Type (e.g., initial evaluation)
- New RX/Appointment Function
- Waitlist Functionality for managing overflow
- Recurring Scheduling for ongoing therapies
- Automated text-based Appointment Reminders
- Patient Check-In processes
- Display Provider Availability clearly
- Support double or triple booking as needed
- Differentiate between new and returning patients for scheduling and reporting
- Simplify setup by linking providers via notes rather than rigid calendar-based licensing
- **Desired:** Timeline View showing patient appointments and form statuses

## 3. EHR/Clinical Documentation

Exclusive to STR (Rehab) and LY entities, this module streamlines provider workflows with intuitive templates, auto-populated data, and seamless charge generation.

### Documentation Features
- Provider documentation for encounters/visits
- Support for various Note Types (SOAP Notes, Daily Notes, Initial Evaluation, Re-evaluation)
- Pull patient/encounter data into templates automatically
- Single-page note views consolidating sections (History, Exam, Goals, Assessment, Plan)
- Easy editing of existing notes with "amended" indicators and dates
- Acronym auto-complete for common phrases, editable for customization

### Template Management
- Customizable templates, often body-part specific with embedded formulas
- Simplified base templates (e.g., PIP, ISS) that providers can edit and save

### Clinical Data Capture
- Vitals
- Assessments and Questionnaires
- Medical History (Allergies, Medications, Family/Social History)
- Care Plans
- RFA (DWC Form) generation
- Proof of Service document generation
- Digital Charge Slips/Superbills

### Coding and Billing Integration
- Efficient CPT/ICD-10 Code Selection within workflow
- Auto-transfer ICD-10 from intake to notes
- House codes in PM with EHR selection of codes and units (PM handles fees)
- Clinical notes and charges flow automatically to PM billing queue
- Document linking (reports/authorizations to charges) for Workers' Comp compliance

### Provider Sign-Off Workflow
- Persistent notifications for unsigned items (e.g., dashboard bar)
- Bulk signing for similar documents (e.g., all notes)
- Clustering by type (e.g., intakes vs. referrals)
- Mandatory signer fields with audit trails (timestamp, user)
- PT oversight for PTA documentation

### Additional Clinical Features
- Access to Patient Charts/Reports from clinical side
- Centralized patient notes for one-click access
- Minimize repetitive entry through smart data propagation

## 4. Provider Management

This module maintains a robust provider directory to support licensing, scheduling, and role-based access.

- Setup and maintain Provider Directory (e.g., NPI, licenses) housed in PM but accessible to EHR
- Assign Licenses to Providers for billing
- Configure Provider Availability and Schedules
- Manage Roles (e.g., Signers, Assistants, Lead PT, Co-signer)
- Ensure PT oversight for PTA documentation

## 5. Integrations

These requirements ensure interoperability to support data flow and future expansions.

### Core Integrations
- Integration with Practice Management (PM) for seamless charge flow
- Real-time Eligibility Checks
- Clearinghouse integration (TriZetto, Jopari)
- Internal messaging (if required)

### Desired/Future Integrations
- External integrations via FHIR/REST APIs
- Web voice/video calls (not MVP)
- Statement/merchant services integration
- API with Laserfiche for scanned batches

## 6. Audit and Monitoring

These features promote compliance and oversight.

- Track user actions for compliance (e.g., data entry, note sign-offs)
- Audit trails for patient record access and modifications (timestamp, user)
- Monitor referral/authorization status changes with logs

## 7. Data Requirements

### Data Entities
Core entities include: Patient, Referral, Appointment, Encounter, Provider, Location, Insurance, and Code (CPT, ICD-10)

### Data Fields
As specified in Functional Requirements, with emphasis on:
- Structured fields (e.g., Addresses)
- Financial details (e.g., Charges, Payments, Write-Offs)

### Data Directories
Maintain directories for:
- Codes (with bulk CSV imports)
- Carriers
- Providers
- Locations
- Financial Classes
- Payment Codes
- Referral Sources
- Marketers
- Appointment Types

*Note: Primarily maintained in PM, shared with EHR/Scheduler*

### Data Flow
- Bidirectional flow: Intake data auto-populates EHR/PM; charges/notes flow to billing
- For external clients: support manual Laserfiche entry with desired API automation
- Copy data to warehouse for cross-practice reporting

### Data Storage
- Separate database instances per practice (e.g., OpenEMR)
- Centralized MBC access via interfaces and data warehouse

### Data Migration Needs
- Migrate historical data from AdvancedMD/CPU via CSV/spreadsheet uploads
- Testing for completeness required

## 8. Reporting Requirements

Robust, customizable reporting is critical for operational insights, with focus on posting dates for financial accuracy and cross-practice views.

### Report Types

#### Referral Logs
- Generate reports by Referral Entry Date, Source, etc., for marketing

#### Scheduling Reports
- Track appointment volume
- Provider schedules
- Patients awaiting scheduling (exportable to Excel)
- Daily/weekly/monthly summaries
- New Patient Logs

#### Provider Productivity Reports
- Analyze encounters/notes
- Patient volumes per provider (including co-signers)
- Marketing/referral metrics

### General Reporting Features
- Custom report building with filters/sorting (e.g., by location, financial class)
- Pull by posting date for reconciliation
- Batch reconciliation
- Audit trails
- Hyperlinked data (e.g., to EOBs)
- Cross-practice reporting via data warehouse
- Data export support to CSV/XLS