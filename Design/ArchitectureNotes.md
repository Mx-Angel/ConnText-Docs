# Architecture Notes

## Overview
This is a supporting document that will provide rationale for decisions made with the architecture. This supports the [ArchitectureDiagram.drawio](Diagrams/BackendArchitectureDiagram.drawio)/[ArchitectureDiagram.png](Diagrams/BackendArchitectureDiagram.png) files.

The backend diagram will use the concept of an architecture diagram to show the different services that make up the server. Whilst the frontend diagram will use a component diagram to show the different components that make up the client application.

### Frontend Services


### Backend Services
The ConnText backend is designed to be modular and scalable so each service is designed to handle a specific aspect of the system. The services communicate with each other mainly using HTTP or WebSockets, depending on the nature of the communication.

#### Gateway Service
The gateway service is the main entry point for the ConnText server. This service handles incoming requests, routes them to the appropriate services, and manages basic authentication and authorization.

#### System Management Service
The system management service is responsible for managing the overall state of the ConnText server. It handles auditing, logging, and system-level operations. It will also provide metrics and health checks for the server. This service ensures that the server runs smoothly and problems can be diagnosed quickly.

#### Authorisation & Authentication Service
The authorisation and authentication service is responsible for verifying user credentials and managing user sessions. It will create validation tokens for users and ensure that only authenticated users can access administrative features/actions.

#### Messaging & Media Service
The messaging and media service is responsible for handling text communications, and file transfers. It manages the storage and retrieval of messages, media files, and other related data. This service ensures that users can communicate effectively and securely.

#### Real-time Communication Service
The real-time communication service is responsible for managing connections between users for voice and video calls. It will handle the process of establishing, maintaining, and terminating these connections. This service ensures that users can communicate in real-time without interruptions.

### Backend Databases
This section describes the databases used by the ConnText backend services. Each database is designed to support specific set of microservices and functionalities.

#### Audit Database
The audit database is connected to the system management service and is used to store logs and audit trails of system operations. This database is essential for monitoring the health of the ConnText server and diagnosing issues.

#### Server Details Database
The server details database is connected to the Authorisation & Authentication service and the Server Management service. Its purpose is to store encrypted validation tokens and user session information. Additionally, it will store details about the server's configuration and state, e.g. server channels, user roles, and permissions. This database is crucial for managing user access and ensuring that the server operates securely. It is easy to confuse this with the Audit Database, but the Server Details Database is focused on user sessions and server configuration, while the Audit Database is focused on system operations and logs.

#### Communication Database
The communication database is connected to the Messaging & Media service and the Realtime Communication service. It is used to store messages, media files, communication information, and other related data. This database is essential for ensuring that users can access their communication history and media files. It will also store metadata about the communications, such as timestamps, sender/receiver information, and message status.