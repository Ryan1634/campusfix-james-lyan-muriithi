# CampusFIX – Architecture Design Decisions

## Introduction
During the design of CampusFIX, we considered different ways of organizing the system and its components. The decisions below explain the options we considered, why we selected our final approaches, and the disadvantages we accepted.

## Decision 1: Choice of Architecture Pattern
**Driven by:** NFR-05 (Maintainability) and the need to keep the system organized as it grows.

### Options Considered
1. Three-Tier Layered Architecture.
2. Monolithic Architecture.

### Chosen Option and Reasons
We selected the Three-Tier Layered Architecture because it separates the system into the Presentation Layer, Application Layer and Data Layer.
This arrangement gives each layer a clear responsibility. For example, the User Interface handles interaction with users, the Application Layer processes maintenance activities, and the Data Layer manages stored information.
We felt this approach would make CampusFIX easier to understand, maintain and improve in the future.

### Trade-off Accepted
The layers depend on one another to complete operations. This may introduce additional communication steps compared to a simpler design. Also, a problem in an important layer may affect the services that depend on it.

### Requirements It Supports
- NFR-05: Maintainability.
- NFR-02: Performance, through organized separation of responsibilities.

---

## Decision 2: Centralized Authentication and Role-Based Access
**Driven by:** NFR-03 (Security), NFR-08 (Authorization) and the need to protect system operations.

### Options Considered
1. A centralized Authentication Component that checks user access and roles.
2. Implementing separate login and access-checking logic within individual system pages.

### Chosen Option and Reasons
We chose a centralized Authentication Component because CampusFIX will be used by different categories of users, including students and staff, maintenance workers, and administrators.
Having authentication and access checks handled centrally makes it easier to manage who can access particular features. It also reduces the need to repeat access-control logic throughout the system.

### Trade-off Accepted
The Authentication Component becomes an important dependency for protected operations. If it becomes unavailable or develops a problem, users may be unable to access features that require authentication. It also requires careful implementation and testing to ensure that permissions are correctly enforced.

### Requirements It Supports
- NFR-03: Security.
- NFR-08: Authorization.
- FR-01: Log In.
- FR-02: Log Out.
- FR-16: Role-Based Access Control.

---

## Decision 3: Centralized Data Storage
**Driven by:** NFR-06 (Reliability) and the organisational constraint of limited time and resources for the academic project.

### Options Considered
1. A centralized Database Component for storing and retrieving system information.
2. Using separate storage locations or files for different parts of the system.

### Chosen Option and Reasons
We selected a centralized Database Component because CampusFIX needs to manage related information such as user accounts, maintenance requests, worker assignments and request history.
Keeping this information in one database makes it easier for the application components to access consistent records. It also simplifies data management and is more practical for the current size and scope of the project.

### Trade-off Accepted
The database becomes a central dependency. If it becomes unavailable, the system may not be able to save or retrieve information. The database will also need proper backup, security and recovery measures to reduce the risk of losing important records.

### Requirements It Supports
- NFR-06: Reliability.
- NFR-03: Security, through appropriate protection of stored information.
- FR-03 to FR-16: Maintenance request and workflow activities that depend on stored information.

---
## Conclusion
These decisions provide a foundation for the current CampusFIX design. The selected architecture keeps the system organized, centralizes access control and provides a common place for managing information.
Although each decision has disadvantages, we believe the selected approaches are suitable for the current academic project and can be improved as the system develops.
