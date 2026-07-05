# Architecture Notes

## Overview
This is a supporting document that will provide details about the system architecture. We will use a reduced [C4 model](https://c4model.com/) to represent the architecture; system context, containers, and components. This supports the [System Context](DiagramImages/Architecture/SystemContextDiagram.png), Container, and Component diagrams.

## Minimal Viable Architecture (MVA)
We will create the diagrams in a way that represents the minimal viable architecture (MVA) of the system.

## Admin Panel
The Admin Panel is a web-based interface that allows administrators to manage and monitor the system. Work towards it will not start until the backend is at least at a minimal viable product (MVP) state.

## ConnText SDK
The diagram for this will be a "sub-component" diagram, as the SDK has a lot of parts in of itself, but does not need a code diagram to represent it. The component diagram should give sufficient overview without being too detailed.

## Federation
Federation is deffered until post-MVP due to the complexity of the implementation and the need to focus on core functionality first.

## Selective Forwarding Unit (SFU)
We use this instead of a mesh network for two reasons: privacy, as participants only see the server's IP address rather than each other's, preventing IP exposure; and scalability, as mesh networks degrade beyond 4-5 participants due to each client needing to upload separate streams to every other peer.