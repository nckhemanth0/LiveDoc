# Online Collaborative Text Editor

## Table of Contents
1. [Introduction](#introduction)
2. [Features](#features)
3. [Tech Stack](#tech-stack)
4. [Prerequisites](#prerequisites)
5. [How to Run](#how-to-run)
6. [Screenshots](#screenshots)
7. [Algorithm](#algorithm)
8. [Contributors](#contributors)
9. [References](#references)

## Introduction
We have designed and implemented an online real-time collaborative text editor. This type of software enables multiple users on different machines to edit the same document simultaneously, similar to popular tools like Google Docs.

## Features

### User Management
- **User Registration** and **Authentication**: Register and login to user accounts.

### Document Management
- **File Management**: Create, open, rename, and delete files.
- **Access Control**: Share documents with permissions (viewer or editor); ensure security with owner-only file deletion.
- **List Documents**: View owned and shared documents.

### Real-time Collaborative Editing
- **Support File Editing**: Edit document text with bold and italic formatting.
- **Support Concurrent Edits**: Enable multiple users to edit simultaneously; manage conflicts effectively.
- **Real-time Updates**: Track edits in real-time; see other users' cursors and active sessions.

### UI
- **Simple UI**: Includes login, sign up, intuitive file management (create, list, delete, rename, share, open), and text editing capabilities.

## Tech Stack
- **Backend:** 
    - Java 17
    - Spring Boot 3.2.4
    - Spring Security
    - STOMP Web Sockets
    - H2 In-memory Database
- **Frontend:** 
    - React.js 18.2.0
    - Vite
    - Quilljs
    - TailwindCSS

## Prerequisites
- **Java Development Kit (JDK)**: Version 17 required
  - On Mac: `brew install openjdk@17`
- **Node.js**: Version 16.x or higher
- **npm**: Included with Node.js

## How to Run

### Backend
```bash
# Navigate to backend directory
cd backend

# Clean and build the project
./gradlew clean build

# Run the Spring Boot application
./gradlew bootRun
```

### Frontend
```bash
# Navigate to frontend directory 
cd frontend

# Install dependencies (first time only)
npm install

# Start the development server
npm run dev
```

The backend server runs on http://localhost:3000
The frontend application runs on http://localhost:5173

## Screenshots
#### When you sign in
![](/Images/Login.png)
#### Sign up window
![](/Images/SignUp.png)
#### Homepage
![](/Images/Homepage.png)
#### Doc editor
![](/Images/Edit.png)
#### Share the doc
![](/Images/Share.png)
![](/Images/SharedDocument.png)
#### Edit Collaboratively
![](/Images/ActiveEditors.png)
#### Real time editing with shared users
![](/Images/ActiveUsers.png)

## Algorithm: Real-Time Conflict Resolution (CRDT)

To handle real-time collaboration, we use a CRDT (Conflict-free Replicated Data Type) approach, similar to a doubly linked list.

Each character (node) stores:
- A unique ID (e.g. `h@user`)
- Left and right node IDs (for ordering)
- The character itself
- Bold/Italic flags
- A deleted flag

### How It Works

- **Insert**: New characters are placed between left and right node IDs. If multiple users insert at the same place, the username decides the order (alphabetically).
- **Delete**: Characters are marked as deleted (not removed).
- **Bold/Italic**: Formatting flags are stored on each character node.
- **Conflict Resolution**: CRDT ensures edits from multiple users merge cleanly, without overwriting.

All nodes are stored in a map for fast lookup by ID, allowing real-time updates and consistent state for all users.