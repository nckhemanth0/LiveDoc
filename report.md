# LiveDoc: Real-Time Collaborative Text Editor

## CS9053 – Spring 2025 Final Project Report

**Team Members:**
- Chenna Kesava Hemanth Reddy Narala (cn2507)
- Rahul Mallidi (rm7020)
- Harshit Ojha (ho2228)

---

## 1. Introduction

LiveDoc is a real-time collaborative text editor that allows multiple users to edit documents simultaneously, with instant updates for all participants. The project is built using advanced Java technologies, distributed systems, and modern web development. The backend is implemented entirely in Java, leveraging the Spring Boot framework and Java concurrency features.

---

## 2. Advanced Java Concepts

- **Multi-threading and Concurrency:**
  - The backend uses Java's multi-threaded architecture, where each HTTP request and WebSocket session is handled by a separate thread managed by the Spring Boot framework.
  - Java concurrency utilities such as `ConcurrentHashMap` and `CopyOnWriteArrayList` are used to safely manage shared state (active sessions, document nodes) across threads.
  - Synchronized blocks and atomic operations in Java ensure that concurrent document edits (insert, delete, format) are applied without race conditions.
  - Background tasks (auto-save, session cleanup) are implemented using Java's `ScheduledExecutorService` for periodic execution without blocking main threads.

- **Networking (Java-based):**
  - RESTful APIs are implemented using Java Spring Boot's `@RestController`, `@RequestMapping`, and related annotations, providing endpoints for user authentication, document CRUD, and sharing.
  - Real-time collaboration is achieved using Java's WebSocket support in Spring (`@EnableWebSocketMessageBroker`, `@MessageMapping`, `@SendTo`), with STOMP protocol for message routing.
  - Java's session and security management (Spring Security) is used for authentication, authorization, and session persistence.

- **Database Integration (Java Persistence):**
  - The backend uses Java's JPA (Java Persistence API) with Spring Data JPA for ORM, mapping Java entity classes to H2 database tables.
  - Entities such as `User`, `Document`, and `CRDTNode` are defined as Java classes annotated with `@Entity`, `@Id`, and related JPA annotations.
  - Transactional integrity is ensured using Spring's `@Transactional` annotation, so concurrent edits are committed atomically.
  - All data access and modification is performed through Java repository interfaces extending `JpaRepository`.

- **Security (Java/Spring Security):**
  - User authentication and authorization are managed using Java-based Spring Security, with password encoding, session management, and role-based access control.
  - Secure endpoints are protected using `@PreAuthorize` and other security annotations.

- **GUI (Java Integration):**
  - While the frontend is in React.js, all communication with the backend is via Java-based REST and WebSocket endpoints.
  - The backend validates and processes all document operations, user actions, and permission checks in Java.

---

## 3. Real-Time Collaboration & CRDT (Java Implementation)

- The CRDT (Conflict-free Replicated Data Type) is implemented as a set of Java classes, with each character node represented as a Java object containing unique ID, formatting, and status fields.
- Insertions and deletions are managed using Java's collection classes and are resolved deterministically based on node IDs and user information.
- All CRDT operations are broadcast to clients using Java's WebSocket message handling.
- The document state is reconstructed on the backend using Java algorithms that traverse and merge CRDT nodes.

---

## 4. Key Features (Java-Focused)

- Multi-user, real-time editing with Java WebSocket backend.
- Live cursor tracking and collaborative awareness managed by Java message broadcasting.
- Document sharing and permissions enforced by Java security and access control logic.
- Rich text formatting (bold, italic) stored and processed in Java CRDT nodes.
- Secure authentication and session management using Java Spring Security.
- Robust error handling and recovery using Java exception handling and transaction management.

---

## 5. Technical Challenges & Java Solutions

- Consistency: Achieved with Java CRDT logic and thread-safe collections.
- Network latency/disconnections: Java queues and replays updates for reliability.
- Conflict resolution: Java CRDT algorithms eliminate merge conflicts.
- Data persistence: Java JPA and transactional methods ensure all changes are stored and recoverable.
- Concurrent access: Java atomic operations and synchronized blocks prevent data corruption.

---

## 6. System Architecture (Java Emphasis)

- **Backend (Java):**
  - Java 17, Spring Boot 3.2.4, Spring Security, STOMP WebSockets, H2 Database
  - Java classes for entities, services, controllers, and CRDT logic
  - Java concurrency and scheduling for background tasks
- **Frontend:** React.js 18.2.0, Vite, QuillJS, TailwindCSS
- **Deployment:** Backend on http://localhost:3000, Frontend on http://localhost:5173

---

## 7. Conclusion

LiveDoc demonstrates advanced Java programming, including multi-threading, networking, persistence, and security. The project delivers real-time collaboration, robust conflict resolution, and a smooth user experience, all powered by Java technologies.

---

## 8. References

- [Project GitHub Repository](https://github.com/nckhemanth0/LiveDoc)
- [README Documentation](https://github.com/nckhemanth0/LiveDoc#readme) 