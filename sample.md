# Non-Functional Requirements

The new system aims to address various non-functional needs to improve overall performance, usability, and security, moving beyond the limitations of current systems like AdvancedMD and CPU.

## Performance and Speed

### System Response Times
- **Page load times**: Maximum 2 seconds for standard pages
- **Search result returns**: Less than 1 second for patient/provider lookups
- **Report generation**: 
  - Simple reports (< 1000 records): Within 5 seconds
  - Complex reports (> 10,000 records): Within 30 seconds
  - Export to CSV/Excel: Within 10 seconds
- **Form submission and saves**: Less than 1 second response time
- **Minimal latency for all user interactions** with no buffering or system slowdown during data entry

### Performance Benchmarks
The system must handle:
- **14,000 dates of service per month** across all entities
- **8,000 electronic claims per month** processing capacity
- **200 new patients per day** during peak periods
- **Concurrent users**: Support minimum 50 simultaneous users without performance degradation

### Critical Performance Requirements
- Address the current AdvancedMD issue of being "slow and cluttered" with a responsive, streamlined interface
- Match or exceed CPU system's efficiency that allows experienced users to "fly through everything" without delays

## Usability and User Interface

### Interface Design Principles
- **Single-page consolidated views** for related information (emulating CPU's snapshot view)
- **Maximum 3 clicks** to reach any core function from the main dashboard
- **Consistent menu options** regardless of navigation path
- **Visual indicators** for:
  - Missing required fields (red borders)
  - Outstanding items requiring attention (badges/notifications)
  - Data validation errors with clear error messages
- **Tabbed interface** with logical grouping, minimizing total number of screens

### Data Entry and Workflow
- **Business rules and guardrails** to ensure required fields are completed before submission
- **Smart defaults and auto-population** where applicable to reduce manual entry
- **Bulk operations support**:
  - Bulk document signing with filtering by document type
  - Batch appointment scheduling
  - Mass status updates
- **Acronym expansion** for prepopulating notes in all text fields
- **Amendment capability** for notes with clear audit trail (date, user, reason) without impacting billing

### Template Management
- **Customizable templates** for notes and correspondence with ability to:
  - Pull any demographic or account field
  - Create body-part specific templates with embedded formulas
  - Save personalized versions of base templates
- **Template library** with search and categorization features

### Navigation and Access
- **Hyperlinking of related documents** (EOBs/ERAs) for easy access during payment posting
- **Timeline view** showing chronological patient visits and documents
- **Quick access toolbar** for frequently used functions
- **Keyboard shortcuts** for power users

## Reliability and Uptime

### Availability Requirements
- **99.9% uptime** during business hours (6 AM - 8 PM PST, Monday-Saturday)
- **Planned maintenance windows** only during off-hours with 72-hour advance notice
- **Maximum unplanned downtime**: 4 hours per month

### Disaster Recovery and Business Continuity
- **Recovery Time Objective (RTO)**: 4 hours
- **Recovery Point Objective (RPO)**: 1 hour
- **Automated backups**:
  - Incremental backups every hour
  - Full backups daily
  - Retention: 30 days for daily, 12 months for monthly, 7 years for annual
- **Geo-redundant data storage** with automatic failover
- **Documented disaster recovery procedures** with quarterly testing

## Security and Compliance

### Regulatory Compliance
- **HIPAA compliant** with documented security controls
- **ONC Certification Requirements** for EHR components
- **State-specific compliance** for California healthcare regulations
- **WCAG 2.1 Level AA compliance** for accessibility

### Security Controls
- **Encrypted data transmission** using TLS 1.3 or higher
- **Encrypted data storage** using AES-256 encryption
- **Multi-factor authentication (MFA)** for all users
- **Role-Based Access Control (RBAC)** with granular permissions:
  - Administrator roles
  - Provider roles (with co-signer capabilities)
  - Scheduler roles
  - Intake staff roles
  - Billing staff roles (read-only clinical access)
- **Session management**:
  - Automatic timeout after 15 minutes of inactivity
  - Secure session tokens
  - Prevention of concurrent sessions

### Audit and Monitoring
- **Comprehensive audit trails** tracking:
  - User login/logout events
  - Data creation, modification, and deletion
  - Document access and downloads
  - Report generation
  - Configuration changes
- **Audit log retention**: Minimum 7 years
- **Real-time security monitoring** with alerts for suspicious activities
- **Monthly security reports** for compliance review

### Data Governance
- **Data retention policies** aligned with California state requirements
- **Patient data privacy controls** beyond HIPAA:
  - Consent management
  - Data portability (patient data export)
  - Right to deletion requests handling
- **Inter-practice data segregation** ensuring complete isolation between entities
- **Data classification** system (PHI, PII, Public, Internal)

## Scalability

### Growth Capacity
- **Horizontal scaling** capability to add servers as volume increases
- **Database optimization** for handling:
  - 5-year data retention online
  - 10x current transaction volume
  - Sub-second query response for 5+ million patient records
- **Modular architecture** allowing feature additions without system redesign
- **API rate limiting** to prevent system overload from integrations

## Accessibility

### System Access
- **100% cloud-based architecture** with no on-premise requirements
- **Browser compatibility**:
  - Chrome (latest 2 versions)
  - Firefox (latest 2 versions)
  - Safari (latest 2 versions)
  - Edge (latest 2 versions)
- **Responsive design** adapting to different screen sizes
- **Offline capability** for critical functions with automatic sync when connected

### Accessibility Standards
- **Screen reader compatibility** for visually impaired users
- **Keyboard navigation** for all functions (no mouse-only features)
- **Color contrast ratios** meeting WCAG standards
- **Adjustable font sizes** without breaking layout
- **Alternative text** for all images and icons

### Cross-Practice Access
- **Consolidated master dashboard** replacing 12 separate "office keys"
- **Practice-specific views** with ability to switch contexts
- **Centralized notes repository** accessible across authorized practices
- **Unified reporting** across all entities with appropriate filtering

## Mobile/Tablet Support

### Device Support
- **Native iPad application** or fully responsive web interface for providers
- **Touch-optimized interface** for tablet users
- **Simplified mobile workflows** for:
  - Appointment scheduling
  - Note creation and signing
  - Patient lookup
  - Quick charge entry
- **Offline mode** for clinical documentation with automatic sync
- **Biometric authentication** (Face ID/Touch ID) for quick secure access

## Reporting

### Core Reporting Capabilities
- **Real-time data** for all reports (no batch processing delays)
- **Custom report builder** with drag-and-drop interface
- **Saved report templates** with scheduling capabilities
- **Export formats**: CSV, Excel, PDF, direct email
- **Drill-down capability** from summary to detail views

### Report Performance
- **Live filtering and sorting** without page refreshes
- **Pagination** for large datasets with configurable page sizes
- **Report caching** for frequently accessed reports
- **Background processing** for complex reports with email notification upon completion

### Required Reports
All reports must support filtering by posting/entry date and include:
- **Aging Report** with customizable aging buckets
- **Referral Log** with source tracking for marketing
- **Marketing Report** distinguishing new vs. returning patients
- **Reconciliation Report** for batch processing
- **Patient Appointment Report** (historical and future)
- **Patient/Employer History** with receipt generation
- **Provider Productivity Report** including co-signer metrics
- **Daily/Weekly/Monthly Summaries** with trend analysis

# Risk Management

MBC has identified several key risks associated with the system transition and new development, along with comprehensive mitigation strategies.

## Data Migration Risks

### Identified Risks
- **Incomplete historical data transfer** from AdvancedMD and CPU systems
- **Data mapping errors** between different system structures
- **Duplicate patient records** from multiple sources
- **Loss of document attachments** and scanned materials
- **Incorrect relationship mapping** (e.g., referrals to patients, providers to appointments)

### Mitigation Strategies
- **Phased migration approach**:
  1. Phase 1: Active patients (seen in last 12 months)
  2. Phase 2: Historical patients (12-36 months)
  3. Phase 3: Archived data (36+ months)
- **Data validation protocols**:
  - Automated reconciliation reports comparing source and target record counts
  - Sample audits of 10% of migrated records
  - Checksum verification for document attachments
- **Parallel run period**: 30 days with both systems operational
- **Rollback procedures** documented for each migration phase
- **Data cleansing** prior to migration to eliminate duplicates

### Success Metrics
- **99.9% data accuracy** for patient demographics
- **100% document attachment preservation**
- **Zero data loss** for financial transactions
- **Completion within 60 days** of project initiation

## User Adoption Risks

### Identified Risks
- **Resistance to change** from users comfortable with existing systems
- **Provider concerns** about losing control over CPT and diagnosis codes
- **Learning curve** for new interfaces and workflows
- **Productivity dip** during transition period
- **Shadow system usage** (reverting to paper or old systems)

### Mitigation Strategies
- **Change management program**:
  - Executive sponsorship and communication
  - Champion users in each department
  - Regular town halls for feedback
  - Success stories and quick wins communication
- **Gradual rollout**:
  - Pilot with willing early adopters
  - Department-by-department implementation
  - Overlap period with dual system access
- **Workflow optimization** before automation:
  - Simplify processes first, then digitize
  - Involve users in workflow design
  - Document and communicate improvements
- **Incentive programs** for early adoption and proficiency

### Success Metrics
- **95% active user adoption** within 30 days of go-live
- **80% user satisfaction** rating after 60 days
- **Return to baseline productivity** within 45 days
- **Less than 5% shadow system usage** after 90 days

## System Integration Risks

### Identified Risks
- **Delays in Practice Management integration** affecting billing operations
- **API incompatibilities** with external systems
- **Clearinghouse connection issues** with TriZetto and Jopari
- **Data synchronization errors** between EHR and PM
- **Multiple entity data segregation** challenges

### Mitigation Strategies
- **Integration architecture**:
  - API-first approach using REST/FHIR standards
  - Message queuing for asynchronous processing
  - Circuit breakers to prevent cascade failures
  - Comprehensive error handling and retry logic
- **Testing strategy**:
  - Unit testing for each integration point
  - Integration testing with test environments
  - Load testing for high-volume scenarios
  - User acceptance testing for end-to-end workflows
- **Vendor management**:
  - Service level agreements with all vendors
  - Regular status meetings during integration
  - Escalation procedures documented
  - Backup vendor identification for critical services
- **Technical solutions**:
  - Real-time data validation between systems
  - Automated reconciliation processes
  - Integration monitoring dashboard
  - Detailed logging for troubleshooting

### Integration Testing Scenarios
- **Patient registration** flowing from EHR to PM
- **Insurance eligibility** verification round-trip
- **Charge capture** from clinical documentation to billing
- **Payment posting** from clearinghouse to PM
- **Document attachment** synchronization
- **Provider schedule** updates across systems

### Success Metrics
- **99.5% message delivery rate** for integrations
- **Less than 5-second lag** for real-time integrations
- **100% financial transaction accuracy**
- **Zero duplicate claim submissions**

## Technical Infrastructure Risks

### Identified Risks
- **Cloud service outages** affecting system availability
- **Cybersecurity threats** including ransomware
- **Performance degradation** under peak load
- **Browser compatibility issues** with updates

### Mitigation Strategies
- **Multi-cloud architecture** with automatic failover
- **Comprehensive security program**:
  - Regular penetration testing
  - Security awareness training
  - Incident response plan
  - Cyber insurance coverage
- **Performance optimization**:
  - Database indexing and query optimization
  - Content delivery network (CDN) for static assets
  - Auto-scaling for peak periods
  - Performance monitoring and alerting
- **Browser testing automation** for all major updates

# Training and Support

Comprehensive training and ongoing support are vital for successful adoption and long-term system utilization.

## User Training Programs

### Role-Based Training Tracks

#### Intake Staff Training (16 hours)
- Patient demographics and insurance entry
- Referral management and documentation
- Document scanning and attachment
- Data validation and error correction
- Efficiency tips and shortcuts

#### Scheduler Training (12 hours)
- Calendar navigation and management
- Appointment scheduling and rescheduling
- Waitlist management
- Recurring appointment setup
- Resource and room management
- Report generation for scheduling

#### Provider Training (8 hours)
- Clinical documentation and templates
- Order entry and e-prescribing
- Chart review and navigation
- Signing and co-signing workflows
- Mobile/tablet usage
- Voice recognition setup (if applicable)

#### Billing Staff Training (20 hours)
- Charge capture and review
- Claims submission processes
- Payment posting
- Denial management
- Report generation and analysis
- Audit trail navigation

#### Administrator Training (24 hours)
- User management and permissions
- System configuration
- Template creation and management
- Report builder
- Audit and compliance tools
- Integration monitoring

### Training Delivery Methods
- **Instructor-led training** for initial rollout
- **Virtual training sessions** for remote staff
- **Self-paced e-learning modules** for ongoing education
- **Hands-on practice** in training environment
- **Competency assessments** with certification

## Training Materials

### Documentation
- **Quick Reference Guides** (2-page summaries for each role)
- **Comprehensive User Manuals** with screenshots
- **Workflow Diagrams** for complex processes
- **FAQs** updated based on support tickets
- **Tip Sheets** for efficiency improvements

### Multimedia Resources
- **Video Tutorials** (3-5 minutes each) for specific tasks
- **Interactive Simulations** for practice without affecting live data
- **Webinar Recordings** of training sessions
- **Screen Recording Library** of common workflows
- **Mobile App** with searchable help content

### Training Environment
- **Dedicated training database** with sample data
- **Refresh capability** to reset training environment
- **Scenario-based exercises** mimicking real situations
- **Performance metrics** to track learning progress

## Ongoing Support

### Support Structure

#### Tier 1 Support (Help Desk)
- **Hours**: 6 AM - 8 PM PST, Monday-Saturday
- **Response Time**: 
  - Critical issues: 15 minutes
  - High priority: 1 hour
  - Normal priority: 4 hours
  - Low priority: 24 hours
- **Channels**: Phone, email, chat, portal
- **Scope**: Password resets, basic navigation, simple troubleshooting

#### Tier 2 Support (Application Support)
- **Hours**: 7 AM - 6 PM PST, Monday-Friday
- **Escalation from Tier 1**: Within 30 minutes for critical issues
- **Scope**: Complex configuration, workflow issues, integration problems

#### Tier 3 Support (Technical/Development)
- **On-call rotation** for critical issues
- **Scope**: Bug fixes, system errors, performance issues

### Support Tools and Processes
- **Ticketing System** with:
  - Automatic ticket routing based on issue type
  - SLA tracking and escalation
  - Knowledge base integration
  - Customer satisfaction surveys
- **Remote Access Tools** for screen sharing and assistance
- **System Status Page** showing real-time system health
- **Scheduled Maintenance Calendar** with notifications

### Service Level Agreements (SLAs)
- **System Availability**: 99.9% uptime during business hours
- **First Response Times** as specified above
- **Resolution Times**:
  - Critical: 4 hours
  - High: 8 hours
  - Normal: 24 hours
  - Low: 72 hours
- **Monthly SLA Reports** with performance metrics

### Knowledge Management
- **Searchable Knowledge Base** with:
  - Solutions to common problems
  - How-to articles
  - Best practices
  - Video guides
- **Community Forum** for peer support
- **Monthly User Group Meetings** (virtual)
- **Quarterly Business Reviews** with stakeholders

## Provider Onboarding

### New Provider Onboarding Process (Week 1)

#### Day 1: System Access and Orientation
- Account creation and credential setup
- Basic navigation training
- Review of security policies
- Introduction to support resources

#### Days 2-3: Core Functionality Training
- Patient chart navigation
- Clinical documentation
- Order entry
- Prescription management

#### Days 4-5: Advanced Features and Integration
- Template customization
- Report generation
- Mobile access setup
- Integration with existing workflows

### Ongoing Provider Support
- **Dedicated Provider Liaison** for first 30 days
- **Weekly check-ins** during first month
- **Peer mentoring program** with experienced users
- **Provider-specific tip sheets** and resources
- **Quarterly provider feedback sessions**

### Success Metrics for Training
- **90% training completion rate** before go-live
- **85% pass rate** on competency assessments
- **80% user confidence rating** post-training
- **50% reduction in support tickets** after 60 days
- **95% satisfaction rate** with training materials

# Assumptions

## Technical Assumptions

### Platform and Architecture
- **Cloud-based deployment** on AWS, Azure, or Google Cloud Platform
- **OpenEMR** will serve as the base platform for EHR functionality, with extensive customization
- **API-first architecture** for all integrations
- **Browser-based access** with no desktop client requirements
- **Multi-tenant architecture** supporting practice segregation

### Integration Assumptions
- **TriZetto will be the primary clearinghouse**, replacing Change Healthcare
- **Jopari** will remain as secondary clearinghouse for specific payers
- **FHIR R4** standard will be used for healthcare data exchange
- **Real-time eligibility verification** will be available through clearinghouse APIs
- **Batch processing** will occur during off-peak hours (midnight to 5 AM PST)

## Operational Assumptions

### Timeline and Rollout
- **Target go-live date**: October 2026
- **Development completion**: August 2026 (2 months before go-live)
- **Parallel run period**: September 2026
- **Legacy system sunset**: December 2026
- **Phased rollout** by entity, starting with STR and LY

### Staffing and Resources
- **Dedicated project team** for implementation period
- **Business analysts** for concurrent PM and EHR requirements gathering
- **Super users** identified and trained from each department
- **Continued vendor support** for first 90 days post-implementation

### Workflow Assumptions
- **Initial patient intake** will be completed by:
  - Precision/California Diagnostics staff for house accounts
  - MBC staff for outside clients
- **Triple-booking capability** will be supported without hard limits initially
- **Virtual visits** are not required in the initial implementation
- **Paper processes** will be eliminated except where legally required

## Business Process Assumptions

### Billing and Financial
- **Patient statements** will be handled by either:
  - TriZetto directly
  - Outsourced statement vendor integrated with the system
- **Credit card processing** through integrated merchant services (e.g., Swipe Simple)
- **ERA/EFT enrollment** will be managed through clearinghouse
- **Collection activities** will remain manual with system support for tracking

### Clinical Documentation
- **Physical Therapy SOAP notes** will be the primary note type
- **Templates** will be standardized across providers where possible
- **Co-signature requirements** for PTA documentation will be enforced systematically
- **Amendment workflow** will maintain billing integrity
- **Voice recognition** is not required but system should support future addition

### Compliance and Regulatory
- **Read-only access to AdvancedMD** will be maintained for one year post-migration
- **Audit logs** will be retained for 7 years
- **HIPAA compliance** attestation will be required annually
- **State-specific requirements** for California will be configured

## Technology Enablement Assumptions

### Artificial Intelligence and Automation
- **AI-powered OCR** will be implemented for:
  - Reading referrals from email/fax
  - Extracting patient demographics
  - Identifying insurance information
  - Creating preliminary appointment requests
- **Automated workflow distribution** to balance scheduler workload
- **Predictive analytics** for appointment no-show risk (future phase)
- **Natural language processing** for clinical note suggestions (future phase)

### Data and Analytics
- **Data warehouse** will aggregate information across all practices
- **Real-time dashboards** for key performance indicators
- **Predictive analytics** capabilities will be added in Phase 2
- **Machine learning** for denial prediction and prevention (future phase)

## User Capability Assumptions

### Technical Proficiency
- Users have **basic computer skills** and internet familiarity
- **Typing speed** of at least 40 WPM for data entry staff
- Providers are comfortable with **tablet/iPad usage**
- All users have **reliable internet access** at work locations

### Change Readiness
- **Executive sponsorship** is committed and visible
- **Department heads** will actively support adoption
- Users are **willing to participate** in training and feedback sessions
- **Paper-based workarounds** will be actively discouraged

## External Dependencies

### Vendor Assumptions
- **Clearinghouse APIs** will remain stable and available
- **Statement vendor** will support required customizations
- **Merchant services** will provide necessary integration documentation
- **Laserfiche** will continue as document management system with API access

### Regulatory Assumptions
- **No major regulatory changes** affecting system requirements before go-live
- **ONC certification requirements** will remain substantially similar
- **California state requirements** will not change significantly
- **HIPAA regulations** will maintain current standards

## Financial Assumptions

### Budget and Resources
- **Adequate funding** is available for entire project lifecycle
- **Training budget** includes coverage for staff time
- **Contingency fund** of 20% for unforeseen requirements
- **Ongoing support costs** are approved for post-implementation

### ROI Expectations
- **Efficiency gains** of 30% in data entry time
- **Reduction in billing errors** by 50%
- **Decreased claim denials** by 25%
- **Improved collection rates** by 15%
- **ROI achievement** within 18 months of go-live