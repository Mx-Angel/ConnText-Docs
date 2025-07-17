# Ideas for ConnText Software

> This is an unfiltered idea dump used during early planning. It’s not meant to be exhaustive, correct, or refined—just a central list of brainstormed possibilities. It feeds into user stories, NFRs, and design planning later in the SDLC. For future reference, I have implemented the MoSCoW prioritization method, but this should not happen until after all the requirements have been gathered and the user stories have been created. 

## Overview
This document is a collection of raw ideas for features and functionalities that could be included in the ConnText software. These ideas are intended to be refined and prioritized based on user needs and technical feasibility.

## Feature Dump

### Must-Have Features

#### User Specific Features
- Must support creating user accounts
- Must support deleting user accounts
- Must support two-factor authentication
- Must be able to create/edit account image
- Must be able to create/edit account name
- Must be able to create/edit account description
- Must support user blocking
- Must support user muting
- Must support password recovery
- Must add support for video chats in voice chat channels
- Must add support for screen sharing in voice/video chats *(Complex - may require deeper planning)*
- Must be able to join multiple servers
- Must be able to leave servers
- Must be able to delete data when leaving a server

#### Server Specific Features
- Must be able to create servers
- Must be able to create/edit server image
- Must be able to create/edit server name
- Must be able to create/edit server description
- Must add server role feature
- Must add server access level control
- Must be able to tie server roles to access levels
- Must be able to assign permissions directly without using server roles
- Must add creating chat channels to send text messages
- Must add creating voice chat channels to allow for audio communication
- Must provide a way to host your own server for handling server traffic for communication
- Must add server moderation functions such as adding, removing, timing out, kicking, and banning users
- Must add the ability to pin, reply to, delete, and edit messages

#### Miscellaneous Features
- Must provide a way to search through messages

### Should-Have Features

#### User Specific Features
- Should support multiple users having the same username
- Should support user presence/status indicators with user-controlled modification
- Should support server-specific usernames

#### Server Specific Features
- Should provide a simple GUI for managing the backend server

#### Miscellaneous Features
- Should support notifications for notable events
- Should allow users to export their data
- Should provide a server library for storing files and searching through them

### Could-Have Features

#### User Specific Features
- (To be explored)

#### Server Specific Features
- (To be explored)

#### Miscellaneous Features
- Could add private message support
- Could support message reactions
- Could provide theming support through a standard process
- Could support custom plugins