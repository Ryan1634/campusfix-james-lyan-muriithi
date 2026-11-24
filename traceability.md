# CampusFIX – Requirements Traceability

This table maps the use cases in the diagram to the functional requirements in the Week 3 SRS. The same mapping is shown in both directions so it is easier to check that no requirement has been left out.

## Part A: Use case to requirement

| Use case | Functional requirements satisfied |
|---|---|
| Log In | FR-01 |
| Log Out | FR-02 |
| Submit Maintenance Request | FR-03, FR-04, FR-05, FR-06 |
| View Submitted Requests | FR-07 |
| Check Request Status | FR-07, FR-12 |
| Search and Filter Requests | FR-14 |
| Set Request Priority | FR-08 |
| Assign Maintenance Worker | FR-09 |
| Update Request Status | FR-10, FR-12 |
| Record Resolution Notes | FR-11, FR-12 |
| Close Maintenance Request | FR-13, FR-12 |
| View Maintenance Dashboard | FR-15 |
| View Request History | FR-12 |

**Role-based access note:** FR-16 applies across the use cases rather than representing a separate user goal. CampusFIX must check a user's role before allowing restricted actions such as setting priority, assigning a worker, updating an assigned request or closing a request.

## Part B: Requirement to use case

| Requirement | What the Week 3 SRS requires | Use case(s) covering it |
|---|---|---|
| FR-01 | Registered users can log into CampusFIX using their credentials. | Log In |
| FR-02 | Authenticated users can log out of the system. | Log Out |
| FR-03 | Students and staff can submit a maintenance request. | Submit Maintenance Request |
| FR-04 | A request contains category, location, description, and date and time of reporting. | Submit Maintenance Request |
| FR-05 | The system generates a unique identification number for every request. | Submit Maintenance Request |
| FR-06 | Submitted requests are saved in the database. | Submit Maintenance Request |
| FR-07 | Authorised users can view maintenance requests according to their role. | View Submitted Requests; Check Request Status |
| FR-08 | An administrator/supervisor can set Low, Medium, High or Critical priority. | Set Request Priority |
| FR-09 | An administrator/supervisor can assign a request to a maintenance worker. | Assign Maintenance Worker |
| FR-10 | Maintenance staff can update the status of an assigned request. | Update Request Status |
| FR-11 | Maintenance staff can enter notes describing how a problem was handled. | Record Resolution Notes |
| FR-12 | The system keeps a history of important changes made to a request. | Check Request Status; Update Request Status; Record Resolution Notes; Close Maintenance Request; View Request History |
| FR-13 | Authorised users can close a request after the problem has been resolved. | Close Maintenance Request |
| FR-14 | Authorised users can filter requests by status, category or priority. | Search and Filter Requests |
| FR-15 | The system provides basic statistics showing the number of requests in different statuses. | View Maintenance Dashboard |
| FR-16 | The system restricts operations according to the user's role. | Applies across all use cases; particularly Set Request Priority, Assign Maintenance Worker, Update Request Status and Close Maintenance Request |

## Coverage check

All 16 functional requirements from the Week 3 SRS have been mapped. FR-16 is cross-cutting: it is enforced within the relevant use cases rather than being treated as a separate task that a user performs.
