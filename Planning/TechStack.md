# Tech Stack

## Overview
The ConnText project is built using a combination of technologies, the ones used for different parts of the project are listed below. The choice of technologies is made to ensure that the correct tools are used for the right job, and to ensure that the project is maintainable, scalable, and secure.

## ConnText-Desktop

| Layer / Area      | Technology / Tool             | Notes / Justification                         |
| ----------------- | ----------------------------- | --------------------------------------------- |
| Language          | C++                           | Native performance, flexibility               |
| UI Framework      | Qt                            | Cross-platform desktop GUI toolkit            |
| Realtime Media    | WebRTC                        | Peer-to-peer video, audio, data, screen share |
| Audio/Video Codec | libwebrtc                     | Media encoding/decoding support via WebRTC    |
| Build System      | CMake                         | Widely used in C++ ecosystems                 |
| Storage           | Local filesystem              | For cache, local media, temp user data        |
| Authentication    | Local certificates + tokens   | Validate user sessions if auth server is used |
| Notifications     | OS-level APIs (Qt wrappers)   | Integrate with native system notifications    |
| Plugin Support    | Custom Plugin Interface (TBD) | User-extensible features (client-side only)   |
| Version Control   | Git + GitHub                  | Project source management                     |

## ConnText-Server
| Layer / Area       | Technology / Tool             | Notes / Justification                        |
| ------------------ | ----------------------------- | -------------------------------------------- |
| Language           | Node.js / TypeScript          | Lightweight backend services, if needed      |
| Web Server         | Fastify or Express.js         | REST API support for auth or file management |
| Database           | PostgreSQL                    | Structured storage for accounts, metadata    |
| File Storage       | Local FS                      | For uploads or shared media                  |
| Auth / Security    | OAuth2 / Custom Login         | User authentication (if server-managed)      |
| Realtime Messaging | HTTPS + WebSockets            | Server fallback for signaling or messaging   |
| API Documentation  | OpenAPI / Swagger             | If public APIs are exposed                   |
| DevOps             | GitHub Actions                | CI/CD, test automation                       |
| Version Control    | Git + GitHub                  | Collaborative version control                |

Note: These technologies are subject to change based on project needs, community feedback, and advancements in the tech stack.