# Non-Functional Requirements Register

## Overview
This document will outline the non-functional requirements of the ConnText software. The non-functional requirements go over requirements that aren't directly related to the functionality of the software, but rather how the software should perform or execute certain functionality. This document will use [UserStories](UserStories) as a reference for features and functionalities. Additionally, these non-functional requirements will be split by their types to make it easier to find the requirements you are looking for and to make future modifications easier.

## Glossary
- RBAC: Role-Based Access Control
- OWASP: Open Web Application Security Project
- WCAG: Web Content Accessibility Guidelines
- zlib: A standard data compression library
- GDPR: General Data Protection Regulation
- PWA: Progressive Web App

## Non-Functional Requirements (NFRs)

### Security
- **NFR-SEC-01**: All data in transit must be encrypted using industry-standard end-to-end encryption protocols (e.g., TLS 1.3 or higher).
- **NFR-SEC-02**: All user data stored on disk must be encrypted at rest using AES-256 or a similar secure standard.
- **NFR-SEC-03**: The system must support multi-factor authentication mechanisms for user accounts.
- **NFR-SEC-04**: Server-side access to administrative functions must be protected through role-based access controls (RBAC).
- **NFR-SEC-05**: Password storage must follow best practices, including salting and hashing using a strong algorithm like bcrypt or Argon2.
- **NFR-SEC-06**: Recovery mechanisms for lost passwords must not expose user data and must follow secure token-based reset procedures.
- **NFR-SEC-07**: The software must be designed in alignment with OWASP Top 10 security best practices to prevent common vulnerabilities.
- **NFR-SEC-08**: The system must support granular permission assignment, allowing both role-based and direct user permissions without compromising security isolation.
- **NFR-SEC-09**: Logs must not contain sensitive information (e.g., passwords, full tokens) and must be protected from unauthorized access.

### Privacy
- **NFR-PRIV-01**: The software must allow server-level moderation (blocking, banning, etc.) without exposing user activity or private data to unauthorized parties.
- **NFR-PRIV-02**: Users must have control over their personal data, including the ability to export, modify, or delete their information.
- **NFR-PRIV-03**: The system must provide granular privacy controls, allowing users to choose what information is shared and with whom.
- **NFR-PRIV-04**: Users must be able to block and mute other users privately, without the blocked/muted users being notified or able to detect this action.
- **NFR-PRIV-05**: The software must provide server admins the ability to configure data residency preferences to keep data within specific jurisdictions.
- **NFR-PRIV-06**: Users must be able to view and revoke active sessions/devices for their account.
- **NFR-PRIV-07**: The system must support configurable data retention periods for all user-generated content.
# Backup and restore features will violate user privacy so changes to the planning need to be made to prevent this.

### Capacity
- **NFR-CAP-01**: The system must support a minimum of 1,000 concurrent users per deployed server instance under expected operating conditions.
- **NFR-CAP-02**: Each server must be capable of handling at least 100 active text chat channels and 100 active voice channels.
- **NFR-CAP-03**: The software must support up to 10 concurrent video streams and 10 concurrent voice participants per voice channel.
- **NFR-CAP-04**: Each deployed server must be able to store a minimum of 5TB of data (messages, media, metadata, etc.).
- **NFR-CAP-05**: The platform should be designed to handle growth to tens of thousands of users per deployment, assuming appropriate hardware.

### Compatibility and Portability
- **NFR-COMPA-01**: ConnText must be compatible with modern versions of major operating systems: Windows, macOS, Linux, FreeBSD, iOS, and Android.
- **NFR-COMPA-02**: The software must support 64-bit system architectures, including both x86 and ARM.
- **NFR-COMPA-03**: The system must be portable across containerized environments, with support for deployment on Docker and Kubernetes.
- **NFR-COMPA-04**: ConnText must be able to integrate with industry-standard authentication providers, including OAuth 2.0 and OpenID Connect.
- **NFR-COMPA-05**: ConnText should support multiple backend database options (e.g., SQLite, PostgreSQL, MySQL) without major configuration changes.
- **NFR-COMPA-06**: Admins must be able to run the software on minimal system configurations, with defined hardware baselines for small (1–20 users) and large (20+ users) deployments.
- **NFR-COMPA-07**: The web-based version of ConnText must be compatible with all major web browsers (e.g., Chrome, Firefox, Safari, Edge).
- **NFR-COMPA-08**: The web-based version must support Progressive Web App (PWA) features, allowing users to install it on their devices without additional software.

### Reliability and Availability
- **NFR-REL-01**: The system must be able to recover from unexpected shutdowns or crashes without data loss using automated rollback or recovery procedures.
- **NFR-REL-02**: The platform must provide user-facing backup and restore capabilities, both manual and automated.
- **NFR-REL-03**: The system must offer export features in standard formats (e.g., JSON, CSV) to ensure data portability.
- **NFR-REL-04**: User access must resume seamlessly after temporary outages, assuming server uptime is restored.
- **NFR-REL-05**: No user or server data should be permanently lost without explicit deletion, even after hardware or software failure.
- **NFR-REL-06**: The system must support graceful degradation, ensuring that when certain features fail or network conditions worsen (e.g., low bandwidth), essential functionality remains accessible. For example, disabling video when audio quality drops, or prioritizing text delivery when media cannot load.
- **NFR-REL-07**: The system must provide centralized error logging and alerting for service-level failures

### Maintainability and Manageability
- **NFR-MAINT-01**: The system must offer a clear separation of configuration and runtime data to support safe upgrades and rollbacks.
- **NFR-MAINT-02**: System-level configuration must be accessible to system admins via a GUI or configuration files, supporting both novice and advanced administrators.
- **NFR-MAINT-03**: Server-level configuration must be accessible to server admins through intuitive management interfaces.
- **NFR-MAINT-04**: The software must support automated version checks and update mechanisms, with optional auto-updates.
- **NFR-MAINT-05**: Admins must be able to roll back to a previous stable version after an update failure, with user data remaining intact.
- **NFR-MAINT-06**: Plugins, themes, and other server customizations must be modular and sandboxed to prevent core application failures.
- **NFR-MAINT-07**: Configuration changes should require minimal downtime, ideally none, for most settings.
- **NFR-MAINT-08**: Permission changes must be applied immediately without requiring system restarts or significant downtime.

### Scalability
- **NFR-SCALE-01**: The system must support horizontal scaling, enabling additional instances of stateless services (e.g., chat, presence) to share workload.
- **NFR-SCALE-02**: The software must be designed to take advantage of additional server resources (CPU, RAM, disk) when vertically scaled.
- **NFR-SCALE-03**: ConnText must be compatible with standard load-balancing solutions (e.g., NGINX, HAProxy, cloud-native load balancers).
- **NFR-SCALE-04**: Policies for scaling should be modifiable, with admin-configurable thresholds for scale-up/down events.

### Usability
- **NFR-USAB-01**: All administrative UIs must follow usability heuristics (e.g., visibility of system status, error prevention, clear feedback).
- **NFR-USAB-02**: Users must be able to perform core actions (e.g., account setup, joining servers) in no more than 3 steps.
- **NFR-USAB-03**: Server admins must be able to perform community management actions (e.g., creating channels, managing roles) in no more than 3 steps.
- **NFR-USAB-04**: System admins must be able to perform technical operations (e.g., backup configuration, system monitoring) through intuitive interfaces.
- **NFR-USAB-05**: All interfaces must be accessible according to WCAG 2.2 guidelines, with at least Level AA compliance, including alternative text for images, focus indicators, and support for high-contrast mode.
- **NFR-USAB-06**: The system should support consistent theming and localization, allowing customization of appearance and language.
- **NFR-USAB-07**: Errors, warnings, and confirmations must be descriptive and non-technical for end users.
- **NFR-USAB-08**: The platform must provide comprehensive documentation, including user guides, API references, and troubleshooting tips.
- **NFR-USAB-09**: Server admins must be able to assign and modify user permissions (both role-based and direct) in no more than 3 steps.
- **NFR-USAB-10**: All user interfaces must be fully operable using keyboard-only navigation.

### Storage
- **NFR-STOR-01**: All stored data must be compressed using the zlib compression algorithm.
- **NFR-STOR-02**: Frequently accessed data (e.g., recent messages, active user profiles) must use zlib compression with low compression levels (1-3) to prioritize decompression speed.
- **NFR-STOR-03**: Infrequently accessed data (e.g., archived messages older than 30 days, inactive user data, etc) must use zlib compression with high compression levels (6-9) to maximize storage efficiency.
- **NFR-STOR-04**: The system must automatically categorize data access patterns and apply appropriate compression levels based on usage frequency.

### Performance
- **NFR-PERF-01**: The system must deliver chat message send/receive latency of less than 200ms under typical network conditions.
- **NFR-PERF-02**: The system must sustain a message throughput rate of at least 100 messages per second per server during peak usage.
- **NFR-PERF-03**: The platform should compress and decompress uploaded files efficiently, minimizing both server-side storage usage and client-side delays.
- **NFR-PERF-04**: Audio and video streaming must maintain under 250ms latency and less than 5% jitter under normal network load.
- **NFR-PERF-05**: UI interactions (e.g., navigation, message posting, switching views) must respond within 500ms in 95% of typical user operations.
- **NFR-PERF-06**: All data should be compressed before transmission to reduce bandwidth usage and improve performance.

### Compliance
- **NFR-COMPL-01**: The ConnText software must comply with major international data protection laws, including GDPR, where applicable.
- **NFR-COMPL-02**: The software must support user rights such as data access, deletion, and export, to comply with privacy regulations.
- **NFR-COMPL-03**: The software must maintain immutable audit logs of sensitive admin actions (e.g., user bans, permission changes) to support compliance audits.
- **NFR-COMPL-04**: The software should allow for regional compliance modules (e.g., HIPAA, COPPA, or country-specific legal notices) to be enabled or disabled based on server location or industry.

### Environmental
- **NFR-ENV-01**: The ConnText software must be designed to use CPU, memory, and disk resources efficiently, minimizing power usage and hardware strain on host systems.
- **NFR-ENV-02**: The software must support deployment on energy-efficient architectures, including ARM-based systems.
- **NFR-ENV-03**: The software should allow dynamic scaling (e.g., sleep/idle modes for inactive services) to reduce resource use during off-peak hours.
- **NFR-ENV-04**: The software must be deployable in containerized environments (e.g., Docker) to enable efficient resource allocation and consolidation.
- **NFR-ENV-05**: The software should offer an optional resource usage dashboard to help admins monitor and optimize energy consumption.
- **NFR-ENV-06**: Inactive containers or processes should automatically enter a low-power sleep state when idle for a configurable threshold period.
