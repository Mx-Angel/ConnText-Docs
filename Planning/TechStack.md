# Tech Stack

## Overview
The ConnText project is built using a combination of technologies, the ones used for different parts of the project are listed below. The choice of technologies is made to ensure that the correct tools are used for the right job, and to ensure that the project is maintainable, scalable, and secure.

## ConnText-SDK

| Layer / Area       | Technology / Tool                              | Notes / Justification                         |
| ------------------ | ---------------------------------------------- | --------------------------------------------- |
| Language           | Rust                                           | Native performance, flexibility, memory safety|
| Build System       | Cargo                                          | Widely used in Rust ecosystems                |
| Realtime Media     | WebRTC                                         | SFU video, audio, data, screen share          |
| Media Processing   | FFmpeg                                         | Media encoding/decoding support               |
| Storage            | SQLite                                         | For cache, local media, user data, etc.       |
| Transport Security | rustls (via reqwest)                           | For secure communication                      |
| Networking         | reqwest + tokio-tungstenite                    | For server communication                      |
| Auth / Security    | oauth2 + jsonwebtoken + opaque-ke              | User authentication                           |
| E2E Encryption     | OpenMLS                                        | For secure end-to-end encryption              |
| Language Bindings  | UniFFI (Kotlin, Swift, Python) + C FFI         | Exposes SDK to other languages                |

## ConnText-Desktop

| Layer / Area       | Technology / Tool             | Notes / Justification                         |
| ------------------ | ----------------------------- | --------------------------------------------- |
| Language           | C++                           | Native performance, flexibility               |
| UI Framework       | Qt                            | Cross-platform desktop GUI toolkit            |
| Build System       | CMake                         | Widely used in C++ ecosystems                 |
| Storage            | SQLite                        | For cache, local media, user data, etc.       |
| Credential Storage | QtKeychain                    | Stores login credentials in OS keyring        |
| Notifications      | OS-level APIs (Qt wrappers)   | Integrate with native system notifications    |
| Plugin Support     | Custom Plugin Interface (TBD) | User-extensible features (client-side only)   |

## ConnText-Server
| Layer / Area       | Technology / Tool              | Notes / Justification                        |
| ------------------ | ------------------------------ | -------------------------------------------- |
| Language           | TypeScript / Node.js           | Lightweight backend services                 |
| Web Server         | Express.js                     | REST API support for auth or file management |
| Database           | PostgreSQL                     | Structured storage for accounts, metadata    |
| File Storage       | fs (built-in)                  | For uploads or shared media                  |
| Auth / Security    | oauth2-server + jsonwebtoken + opaque-ke | User authentication                |
| Realtime Messaging | ws + http                      | Server fallback for signaling or messaging   |
| Media Processing   | FFmpeg (fluent-ffmpeg) + Sharp | Media encoding/decoding/modification support |
| API Documentation  | OpenAPI (Swagger UI)           | For the exposed APIs                         |

Note: These technologies are subject to change based on project needs, community feedback, and advancements in the tech stack.