# Architecture Notes

## Overview

This is a supporting document that provides details about the system architecture. We use a reduced [C4 model](https://c4model.com/) to represent the architecture across three levels: system context, containers, and components.

Supporting diagrams: [System Context](Images/SystemContextDiagram.png), Container, and Component diagrams.

---

## Design Notes

### Minimal Viable Architecture (MVA)
Diagrams represent the minimal viable architecture (MVA) of the system.

### Admin Panel
A web-based interface for administrators to manage and monitor the system. Development will not begin until the backend reaches MVP state.

### ConnText SDK
Presented as a "sub-component" diagram rather than full code diagrams. The overview provides sufficient detail without excessive noise.

### Federation
**Status**: Deferred until post-MVP

Deferred due to complexity of implementation and the need to focus on core functionality first.

### Selective Forwarding Unit (SFU)
Used instead of mesh networks for two key reasons:
- **Privacy**: Participants only see the server's IP address rather than each other's, preventing IP exposure.
- **Scalability**: Mesh networks degrade beyond 4-5 participants as each client must upload separate streams to every peer.

### Encryption
- Content field contains ciphertext for E2EE channels (ADR-005).
- Local search indexing of E2EE messages still require data to be encrypted at rest.

### WebSocket Use
**Status**: Deferred

WebSocket usage patterns will be determined during implementation.

---

## Microservices

### Gateway Service
**Purpose**: Entry point for all client requests

- Routes requests to appropriate microservices
- Validates user identity and permissions via Authentication Service before request processing

### Authentication Service
**Purpose**: User authentication, authorization, and session management

- Handles user login and token generation
- Manages permission checks and user sessions
- Implements OPAQUE protocol (RFC 9807) for secure password handling—server never receives plaintext passwords
- Supports all privileged actions across the system

### Notification Service
**Purpose**: User notifications

Delivers notifications via:
- Email
- Push notifications

### Social Service
**Purpose**: Social interactions between users

- Manages friend requests, blocking, and other social features
- Stores and retrieves social data

### Audit Service
**Purpose**: Logging and auditing of user actions

- Maintains secure, tamper-proof log of all user activities
- Supports compliance and security purposes

### Messaging Service
**Purpose**: Message sending, receiving, and management

- Stores, delivers, and retrieves messages
- Handles message editing
- Ensures timely and reliable message delivery

### Media Service
**Purpose**: Handling media files (images, videos, audio)

- Manages storage, retrieval, and processing of media files
- Performs media transcoding and optimization for different devices and network conditions
- Ensures timely and reliable delivery
- For E2EE channels, the server stores and serves encrypted blobs only, so media processing is handled client-side by the SDK before encryption (ADR-005).

### Real-Time Communication Service
**Purpose**: Real-time communication (voice and video calls)

- Manages setup, management, and teardown of communication sessions
- Uses SFU architecture for timely and reliable delivery

### Server Management Service
**Purpose**: Server moderation and management

- Provides secure interface for server moderators
- Handles user moderation and administrative tasks
- Enables moderators to configure and customize their servers

### System Management Service
**Purpose**: System-wide administration

- Monitors system health
- Manages system infrastructure
- Performs administrative tasks
- Provides interface for system administrators to ensure smooth operation