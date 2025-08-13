# Architecture Notes

## Overview
This is a supporting document that will provide about both the front and backend architecture. This supports the [FrontendArchitectureDiagram](Diagrams/FrontendArchitectureDiagram.png) and [BackendArchitectureDiagram](Diagrams/BackendArchitectureDiagram.png) diagrams.

The frontend diagram will use a component diagram to show the different components that make up the client application. Whilst the backend diagram will use the concept of an architecture diagram to show the different services that make up the server.

### Frontend
Each component will have a specific role and responsibility within the ConnText application, allowing for modular development and easier maintenance. Access of data will also be restricted to the relevant components, e.g. the user management component is the only component with access to user information.

#### Application Shell Component
This component will provide the main user interface for the ConnText application. It will be responsible for rendering the UI, managing user interactions, and coordinating communication between different frontend components.

#### Authentication Component
The authentication component will handle user login, registration, and session management. It will communicate with the authorisation and authentication service to verify user credentials and obtain JWT tokens passing these to the network component when making API requests.

#### Server Management Component
The server management component will be used to manage server configurations; text channels; user roles; bans; etc. This will allow server administrators to easily configure and maintain their servers.

#### Server Health Component
The server health component will monitor the health and performance of the ConnText application. It will provide real-time metrics and alerts for system administrators, helping to ensure the application remains responsive and reliable.

#### Real-Time Media Component
This service will handle real-time audio and video communication between users. It will use WebRTC for connections and provide features such as screen sharing. This component will work closely with the communication component to ensure seamless media transmission.

#### Communication Component
This component will facilitate both non-real-time and real-time communication between users. It will manage the sending and receiving of messages and will be coupled closely with the real-time media component. It will be the only component allowed to directly interface with the network component. Providing a single point of contact for all communication-related tasks.

#### Media Component
The media component will handle the uploading and processing of media files (images, videos, audio) within the ConnText application. It will ensure that media files are stored efficiently and can be accessed quickly by the user.

#### Data Management Component
The data management component will be responsible for managing the application's data storage and retrieval. It will handle database interactions, data caching, password storage and data synchronization between different services. This is the main component for data-related operations and will store application data on the users device with restrictions on access and sharing.

#### User Management Component
The user management component will handle user profiles, preferences, and settings. It will manage user data and ensure that user preferences are respected across the application. It will also be the point of contact for user-related operations as details about the user should be routed through this component.

#### Network Component
The network component will handle all requests between the frontend and backend services. It will manage API calls, WebSocket connections, and other network-related tasks.

### Backend
The ConnText backend is designed to be modular and scalable so each service is designed to handle a specific aspect of the system. The services communicate with each other mainly using HTTP or WebSockets, depending on the nature of the communication. The diagram will not show all connections, only a high level overview.

#### Gateway Service
The gateway service is the main entry point for the ConnText server. This service handles incoming requests, routes them to the appropriate services, and manages basic authentication and authorization. The gateway performs stateless JWT token validation using OAuth2-compliant access tokens, eliminating the need for constant communication with the A&A service for routine authentication checks.

#### System Management Service
The system management service is responsible for managing the overall state of the ConnText server. It handles auditing, logging, and system-level operations. It will also provide metrics and health checks for the server. This service ensures that the server runs smoothly and problems can be diagnosed quickly.

#### Authorisation & Authentication Service
The authorisation and authentication service is responsible for verifying user credentials and managing user sessions. It implements OAuth2 flows and issues JWT-based access and refresh tokens. The service handles complex authentication scenarios (2FA, password resets) and token lifecycle management, while the gateway service handles routine JWT validation for performance.

> Note: This service creates and manages OAuth2-compliant JWT tokens. The gateway service performs stateless validation of these JWTs for routine requests, only delegating to this service for token refresh, complex permissions, or new authentication events.

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