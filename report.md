# LiveDoc: Real-Time Collaborative Text Editor

## CS9053 – Spring 2025 Final Project Report

**Team Members:**
- Chenna Kesava Hemanth Reddy Narala (cn2507)
- Rahul Mallidi (rm7020)
- Harshit Ojha (ho2228)

---

## 1. Introduction

LiveDoc is a real-time collaborative text editor that allows multiple users to edit documents simultaneously, with instant updates for all participants. The project applies advanced Java concepts, distributed systems, and modern web development.

---

## 2. Advanced Java Concepts

- **Multi-threading:**
  - Spring Boot backend handles HTTP requests and WebSocket connections concurrently.
  - Thread-safe data structures (`ConcurrentHashMap`, `CopyOnWriteArrayList`) manage sessions and document state.
  - Atomic operations and background tasks (auto-save, session cleanup) ensure consistency and responsiveness.

- **Networking:**
  - RESTful APIs for user and document management.
  - Real-time updates via STOMP over WebSocket.
  - Frontend (React.js, QuillJS) communicates with backend using HTTP and WebSocket.

- **Database Integration:**
  - H2 in-memory database with Spring Data JPA for persistence.
  - Stores user accounts, document metadata, sharing permissions, and CRDT nodes.
  - Transactional operations for consistent concurrent edits.

- **GUI:**
  - React.js frontend with QuillJS for rich text editing.
  - Features: registration, login, document management, real-time editing, live cursor tracking, sharing, and access control.
  - Responsive design with TailwindCSS.

---

## 3. Real-Time Collaboration & CRDT

- CRDT (Conflict-free Replicated Data Type) manages document state.
- Each character is a node with unique ID, formatting, and status.
- Insertions/deletions resolved deterministically; all operations broadcast to clients.
- Ensures consistent document state for all users, even with concurrent edits.

---

## 4. Key Features

- Simultaneous multi-user editing with real-time updates.
- Live cursor tracking for collaborative awareness.
- Document sharing with viewer/editor permissions.
- Rich text formatting (bold, italic) at character level.
- Secure authentication and session management (Spring Security).
- Robust error handling and recovery from network issues.

---

## 5. Technical Challenges & Solutions

- Consistency across users: CRDT and thread-safe operations.
- Handling network latency/disconnections: queued updates and recovery.
- Conflict resolution: CRDT eliminates merge conflicts.
- Data persistence: all changes stored in database for recovery.
- Concurrent access: atomic updates and thread-safe structures.

---

## 6. System Architecture

- **Backend:** Java 17, Spring Boot 3.2.4, Spring Security, STOMP WebSockets, H2 Database
- **Frontend:** React.js 18.2.0, Vite, QuillJS, TailwindCSS
- **Deployment:** Backend on http://localhost:3000, Frontend on http://localhost:5173

---

## 8. Conclusion

LiveDoc demonstrates advanced Java, distributed systems, and modern web development. The project delivers real-time collaboration, robust conflict resolution, and a smooth user experience.

---

## 9. References

- [Project GitHub Repository](https://github.com/nckhemanth0/LiveDoc)
- [README Documentation](https://github.com/nckhemanth0/LiveDoc#readme) 