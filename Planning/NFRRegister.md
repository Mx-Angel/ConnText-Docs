# Non-Functional Requirements Register

## Overview
This document will outline the non-functional requirements of the ConnText software. The non-functional requirements go over requirements that aren't directly related to the functionality of the software, but rather how the software should perform or behave under certain conditions. This document will use [UserStories](UserStories) as a reference for features and functionalities. Additionally, these functional requirements will be split by there types to make it easier to find the requirements you are looking for and to make future modifications easier.

## Non-Functional Requirements (NFRs)

### Security
- All data in transit must be encrypted using industry-standard end-to-end encryption protocols (e.g., TLS 1.3 or higher).
- All user data stored on disk must be encrypted at rest using AES-256 or a similar secure standard.
- The system must support multi-factor authentication mechanisms for user accounts.
- Server-side access to administrative functions must be protected through role-based access controls (RBAC).
- Password storage must follow best practices, including salting and hashing using a strong algorithm like bcrypt or Argon2.
- Recovery mechanisms for lost passwords must not expose user data and must follow secure token-based reset procedures.
- The software must allow server-level moderation (blocking, banning, etc.) without exposing user activity or private data to unauthorized parties.
- The software must be designed in alignment with OWASP Top 10 security best practices to prevent common vulnerabilities.

### Capacity
- The system must support a minimum of 1,000 concurrent users per deployed server instance under expected operating conditions.
- Each server must be capable of handling at least 100 active text chat channels and 100 active voice channels.
- The software must support up to 10 concurrent video streams and 10 concurrent voice participants per voice channel.
- Each deployed server must be able to store a minimum of 5TB of data (messages, media, metadata, etc.).
- The platform should be designed to handle growth to tens of thousands of users per deployment, assuming appropriate hardware.

### Compatibility and Portability
- ConnText must be compatible with modern versions of major operating systems: Windows, macOS, Linux, FreeBSD, iOS, and Android.
- The software must support 64-bit system architectures, including both x86 and ARM.
- The system must be portable across containerized environments, with support for deployment on Docker and Kubernetes.
- ConnText must be able to integrate with industry-standard authentication providers, including OAuth 2.0 and OpenID Connect.
- ConnText should support multiple backend database options (e.g., SQLite, PostgreSQL, MySQL) without major configuration changes.
- Admins must be able to run the software on minimal system configurations, with defined hardware baselines for small (1–20 users) and large (20+ users) deployments.

### Reliability and Availability
- The system must be able to recover from unexpected shutdowns or crashes without data loss using automated rollback or recovery procedures.
- The platform must provide user-facing backup and restore capabilities, both manual and automated.
- The system must offer export features in standard formats (e.g., JSON, CSV) to ensure data portability.
- User access must resume seamlessly after temporary outages, assuming server uptime is restored.
- No user or server data should be permanently lost without explicit deletion, even after hardware or software failure.

### Maintainability and Manageability
- The system must offer a clear separation of configuration and runtime data to support safe upgrades and rollbacks.
- Server-side configuration must be accessible via a GUI or configuration files, supporting both novice and advanced administrators.
- The software must support automated version checks and update mechanisms, with optional auto-updates.
- Admins must be able to roll back to a previous stable version after an update failure, with user data remaining intact.
- Plugins, themes, and other server customizations must be modular and sandboxed to prevent core application failures.
- Configuration changes should require minimal downtime, ideally none, for most settings.

### Scalability
- The system must support horizontal scaling, enabling additional instances of stateless services (e.g., chat, presence) to share workload.
- The software must be designed to take advantage of additional server resources (CPU, RAM, disk) when vertically scaled.
- ConnText must be compatible with standard load-balancing solutions (e.g., NGINX, HAProxy, cloud-native load balancers).
- Policies for scaling should be modifiable, with admin-configurable thresholds for scale-up/down events.

### Usability
- All administrative UIs must follow usability heuristics (e.g., visibility of system status, error prevention, clear feedback).
- Users must be able to perform core actions (e.g., account setup, server creation) in no more than 3 steps.
- All interfaces must be accessible according to WCAG 2.2 guidelines, including keyboard navigation and screen reader support.
- The system should support consistent theming and localization, allowing customization of appearance and language.
- Errors, warnings, and confirmations must be descriptive and non-technical for end users.
- The platform must provide comprehensive documentation, including user guides, API references, and troubleshooting tips.

### Performance
- The system must deliver chat message send/receive latency of less than 200ms under typical network conditions.
- The system must sustain a message throughput rate of at least 100 messages per second per server during peak usage.
- The platform should compress and decompress uploaded files efficiently, minimizing both server-side storage usage and client-side delays.
- Audio and video streaming must maintain under 250ms latency and less than 5% jitter under normal network load.
- UI interactions (e.g., navigation, message posting, switching views) must respond within 500ms in 95% of typical user operations.

### Compliance
- The ConnText software must comply with major international data protection laws, including GDPR, where applicable.
- The software must support user rights such as data access, deletion, and export, to comply with privacy regulations.
- The software must provide server admins the ability to configure data residency preferences to keep data within specific jurisdictions.
- The software must maintain **audit logs** of sensitive admin actions (e.g., user bans, permission changes) to support compliance audits and these should be immutable.
- The software should allow for regional compliance modules (e.g., **HIPAA**, **COPPA**, or country-specific legal notices) to be enabled or disabled based on server location or industry.

### Environmental
- The ConnText software must be designed to use **CPU, memory, and disk resources efficiently**, minimizing power usage and hardware strain on host systems.
- The software must support deployment on **energy-efficient architectures**, including ARM-based systems.
- The software should allow dynamic scaling (e.g., sleep/idle modes for inactive services) to reduce resource use during off-peak hours.
- The software must be deployable in **containerized environments (e.g., Docker)** to enable efficient resource allocation and consolidation.
- The software should offer an optional **resource usage dashboard** to help admins monitor and optimize energy consumption.
