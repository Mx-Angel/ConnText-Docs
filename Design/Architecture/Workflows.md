# Workflow Diagrams

Each workflow belongs to one of the diagram types below.

## Classification Rules

- **Sequence**: Shows ordered interactions between client, SDK, gateway, backend services, and database. Can only have one successful outcome, but may have multiple failure outcomes (e.g., invalid credentials, server error).
- **Activity**: Shows workflows with decisions leading to different *successful* outcomes, or explicit user choices (e.g., MFA yes/no, delete data or keep, E2EE vs plaintext routing).
- **State**: Shows how an entity or session changes states over time due to events. Tracks lifecycle (conditions and transitions).

## Sequence Diagrams

### Account Management
- Profile Picture Upload
- Profile Picture Modification
- Profile Picture Deletion
- Update Bio
- Update Description
- Delete Description
- Set Server Nickname
- Modify Server Nickname
- Account presence status modification
- Account information download
- Account information storage (Sync settings)

### Social & Connections
- User friend request sending
- User friend request acceptance
- User friend request rejection
- User friend removal
- User blocking
- User unblocking
- User muting
- User unmuting
- Other user account information viewing

### Servers & Channels
- Server joining
- Server user list viewing
- Server user list searching

### Messaging
- Private message sending
- Private message deleting
- Private message editing
- Private message viewing
- Message reactions
- Message reaction removal
- Media file sending
- Media file downloading
- Media file viewing

### Voice & Video Calls
- User-to-user voice call initiation
- User-to-user voice call termination
- User-to-user voice call acceptance
- User-to-user voice call rejection
- User-to-user video call initiation
- User-to-user video call termination
- User-to-user video call acceptance
- User-to-user video call rejection

### Group Chats
- User-to-user group chat creation
- User-to-user group chat invitation sending
- User-to-user group chat invitation acceptance
- User-to-user group chat invitation rejection
- User leaving group chat
- User adding participant to group chat
- User removing participant from group chat

### Notifications
- Notification sending
- Notification configuration

### Voice Channel Interaction (Setup)
- Voice channel participant list view (initial fetch)
- Screen sharing setup

## Activity Diagrams

- User Registration
    - Includes email verification flow and password strength validation.
- Account login
- Account logout
- Account deletion
- Account password change
- Server leaving
    - The user should have the option to delete all their data from a server when leaving it, unless they are removed by an administrator.
- Data Sync Preferences
    - Choose to store data on home server (accessible from any device) or only on this device.
- Message search
    - Differentiate between E2EE and non-E2EE message routing.
- Server user list searching

### Future Implementation [Pending Spec]
- Theming [Future]
- Plugins [Future]

## State Diagrams

- Account authentication and session state
- User presence status change
- Voice transmission in voice channel
- Video transmission in voice channel
- Friend request status
- Voice and video call state
- Message state
- Group chat invitation state
- Server membership state
- Server backup state
- Voice channel participant list state
- Screen sharing state