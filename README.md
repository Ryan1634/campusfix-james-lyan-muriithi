CampusFIX – Architecture and Design Rationale

## 1. System Overview
CampusFIX is a web-based maintenance management system designed to help students and university staff report facility-related problems within the university. It allows administrators and supervisors to review reported issues, set priorities and assign maintenance workers. Maintenance staff can update the progress of assigned tasks, record resolution notes and close completed requests. The system also keeps a record of maintenance activities and provides basic statistics to help monitor the state of reported problems. Students, staff, maintenance workers and administrators interact with CampusFIX, while these actors remain outside the system boundary.

## 2. Constraints
The design of CampusFIX is influenced by the following constraints:

1. Technical constraint: The system is designed as a web application, so its components must communicate through a clear interface and support access through a web browser.
2. Organisational constraint: This is an individual semester project with limited development time and resources. Therefore, a simple architecture is more practical than a complex distributed system.
3. Budget constraint: The project has limited financial resources, so the design should favour affordable development tools and technologies rather than expensive commercial platforms.
4. Legal constraint: CampusFIX may handle personal information belonging to students and university employees. The design must therefore consider the Kenya Data Protection Act, 2019, particularly the protection of personal information and controlled access to user data.
5. Maintenance constraint: The system should be organised into separate components so that future changes can be made without unnecessarily affecting the entire application.

## 3. Architecture Diagram
Architecture pattern: Three-Tier Layered Architecture
The architecture diagram will show how the presentation, application and data layers work together to support CampusFIX.

## 4. pattern Choice
Three-Tier Layered Architecture
Field| Description
Pattern| Three-Tier Layered Architecture
How it appears in my design| CampusFIX is divided into the presentation layer, application layer and data layer. Each layer has its own responsibility and communicates with the next layer.
Why it fits my requirements and constraints| The system handles different activities, including user authentication, maintenance reporting, request assignment and status updates. Separating these activities makes the system easier to organise and develop.
Advantages I am relying on| Easier maintenance, separation of responsibilities, better organisation of code and the ability to modify one layer without redesigning the entire system.
Disadvantages I am accepting| Communication between layers can introduce additional processing, and a problem in one important layer may affect the whole application.
One alternative I considered and why I rejected it| A monolithic architecture was considered because it can be simpler to build initially. However, it combines responsibilities more closely, making future maintenance and modification harder as CampusFIX grows.
## 5. Components

CampusFIX is divided into several components, with each component handling a specific responsibility. This separation helps keep the system organised and makes it easier to maintain and improve in the future.

| Component | Its one job | Use cases it supports | Requirements supported |
|---|---|---|---|
| User Interface | Provides screens through which users interact with CampusFIX. | All use cases | FR-01 to FR-16,NFR-01,NFR-07 |
| Authentication Component | Handles user login, logout and access verification. | Log In, Log Out | FR-01, FR-02, FR-16,NFR-03,NFR-08 |
| Request Management Component | Handles the creation, validation and storage of maintenance requests. | Submit Maintenance Request, View Submitted Requests | FR-03, FR-04, FR-05, FR-06, FR-07,NFR-04 |
| Request Assignment Component | Handles request prioritisation and assignment to maintenance workers. | Set Request Priority, Assign Maintenance Worker | FR-08, FR-09, FR-16,NFR-08 |
| Maintenance Workflow Component | Handles request progress, status updates, resolution notes and closure. | Update Request Status, Record Resolution Notes, Close Maintenance Request | FR-10, FR-11, FR-13, FR-16,NFR-06 |
| Request History Component | Maintains records of important changes made to maintenance requests. | Check Request Status, View Request History | FR-12,NFR-06 |
| Dashboard and Reporting Component | Displays maintenance statistics and helps users filter and monitor requests. | Search and Filter Requests, View Maintenance Dashboard | FR-14, FR-15,NFR-02 |
| Database Component | Stores and retrieves user accounts, maintenance requests, assignments and activity records. | Supports all use cases requiring stored information | FR-01 to FR-16,NFR-03,NFR-06 |

**Component interaction:** The User Interface receives requests from users and forwards them to the appropriate application component. Application components process the requests and communicate with the Database Component whenever information needs to be stored or retrieved. The results are then returned to the user through the interface.


## 6. Non-Functional Requirements to Architectural Decisions

The architecture of CampusFIX is designed to support the quality requirements identified in the Week 3 SRS. Each requirement is addressed through the following architectural decisions.

| NFR | Requirement | Architectural Decision and How It Is Supported |
|---|---|---|
| NFR-01 | Usability | The Presentation Layer provides a simple and organized user interface, making it easier for students, staff and administrators to use the system. |
| NFR-02 | Performance | The three-tier structure separates user interaction, application processing and data storage. This helps organize operations and supports reasonable response times in the prototype. |
| NFR-03 | Security | The Authentication Component handles login and works with the Database Component to manage user credentials. Passwords must be securely hashed rather than stored as plain text. |
| NFR-04 | Validation | The Request Management Component checks submitted information before it is saved, helping prevent incomplete or invalid maintenance requests. |
| NFR-05 | Maintainability | The layered architecture separates responsibilities into understandable components, making future updates easier without unnecessarily affecting the whole system. |
| NFR-06 | Reliability | The Database Component stores maintenance requests and their history. However, backup and recovery mechanisms have not yet been included in the current design. |
| NFR-07 | Compatibility | The Presentation Layer is designed as a web interface that can be accessed through commonly used modern web browsers. |
| NFR-08 | Authorization | The Authentication and Authorization functions check user roles and restrict operations according to the permissions assigned to students, maintenance staff and administrators. |

Although the architecture provides a foundation for these requirements, some still depend on proper implementation and testing. In particular, performance must be tested, password security must be implemented correctly, and database backup and recovery need further attention.

## 7. Risks and Limits

Although the Three-Tier Layered Architecture provides a clear structure for CampusFIX, it has some limitations:

1. **Single point of failure:** The system currently depends on a central database. If the database becomes unavailable, users may be unable to submit or retrieve maintenance requests.

2. **Performance limitations:** As the number of users and maintenance requests increases, the application may experience slower response times, especially if database operations are not optimized.

3. **Limited security and recovery features:** The current design identifies authentication and role-based access control, but advanced security measures, database backups and recovery mechanisms still need to be implemented.

These limitations are acceptable for the current academic prototype, but they should be considered if CampusFIX is developed into a larger university system.


## 8. If Things Change

The CampusFIX architecture can be extended if the system's requirements change in the future.

### Scenario 1: Increase in the Number of Users

If CampusFIX begins serving many more students, staff and maintenance workers, the Application Layer and Database Component may need improvements to handle the increased workload.

The database could be optimized, and additional application resources could be introduced to improve performance. The Presentation Layer and the main responsibilities of the existing components would remain largely unchanged.

### Scenario 2: Introduction of a Mobile Application

If the university decides to introduce a mobile application, a new mobile interface could be added to the Presentation Layer.

The existing Application Layer would continue handling authentication, maintenance requests, assignments and status updates. The Database Component would also remain responsible for storing information. This would allow mobile users to access the same services without redesigning the entire system.
