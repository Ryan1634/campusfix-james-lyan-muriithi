# CampusFIX – Architecture Traceability

## Introduction
This document shows how the components in the CampusFIX architecture relate to the functional requirements and use cases identified in the earlier weeks.
It provides two views of the system: the first shows what each component is responsible for, while the second shows which components handle each use case. This helps us check that all the planned system activities are covered by the architecture.

## Part A: Component to Requirements
The following table explains why each component exists and identifies the use cases and requirements it supports.

| Component | Use Cases Supported | Requirements Supported |
|---|---|---|
| User Interface | All use cases | FR-01 to FR-16, NFR-01, NFR-07 |
| Authentication Component | Log In, Log Out, and access checks across the system | FR-01, FR-02, FR-16, NFR-03, NFR-08 |
| Request Management Component | Submit Maintenance Request, View Submitted Requests | FR-03, FR-04, FR-05, FR-06, FR-07, NFR-04 |
| Request Assignment Component | Set Request Priority, Assign Maintenance Worker | FR-08, FR-09, FR-16, NFR-08 |
| Maintenance Workflow Component | Update Request Status, Record Resolution Notes, Close Maintenance Request | FR-10, FR-11, FR-13, FR-16, NFR-06 |
| Request History Component | Check Request Status, View Request History | FR-12, NFR-06 |
| Dashboard and Reporting Component | Search and Filter Requests, View Maintenance Dashboard | FR-14, FR-15, NFR-02 |
| Database Component | Stores and retrieves information required by all relevant use cases | FR-01 to FR-16, NFR-03, NFR-06 |

**Note:** NFR-05 (Maintainability) applies to the overall Three-Tier Layered Architecture because separating responsibilities into components makes the system easier to maintain and update.

## Part B: Use Case to Component

This table shows which components are responsible for handling each use case identified in the Week 4 use-case model.

| Use Case | Responsible Component(s) |
|---|---|
| Log In | User Interface, Authentication Component, Database Component |
| Log Out | User Interface, Authentication Component |
| Submit Maintenance Request | User Interface, Request Management Component, Database Component |
| View Submitted Requests | User Interface, Request Management Component, Database Component |
| Check Request Status | User Interface, Request History Component, Database Component |
| Search and Filter Requests | User Interface, Dashboard and Reporting Component, Database Component |
| Set Request Priority | User Interface, Request Assignment Component, Authentication Component, Database Component |
| Assign Maintenance Worker | User Interface, Request Assignment Component, Authentication Component, Database Component |
| Update Request Status | User Interface, Maintenance Workflow Component, Authentication Component, Request History Component, Database Component |
| Record Resolution Notes | User Interface, Maintenance Workflow Component, Request History Component, Database Component |
| Close Maintenance Request | User Interface, Maintenance Workflow Component, Authentication Component, Request History Component, Database Component |
| View Maintenance Dashboard | User Interface, Dashboard and Reporting Component, Database Component |
| View Request History | User Interface, Request History Component, Database Component |

## Coverage Check
After mapping the components and use cases, we can see that all 13 use cases from the Week 4 traceability document are supported by the proposed architecture.
All 16 functional requirements (FR-01 to FR-16) are represented. FR-16 is a shared requirement because role-based access control applies to different operations across the system rather than being handled by only one use case.
The eight components also have clear responsibilities, and each has a reason for being included in the design.

## Conclusion
The traceability review shows that the proposed CampusFIX architecture covers the activities identified during requirements analysis and use-case modelling.
It also provides a clear connection between the system requirements, use cases and architecture components. This will help guide implementation and make it easier to identify any missing functionality as the project develops.

