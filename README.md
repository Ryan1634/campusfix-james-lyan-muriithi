CampusFIX – Architecture and Design Rationale

###System Overview
CampusFIX is a web-based maintenance management system designed to help students and university staff report facility-related problems within the university. It allows administrators and supervisors to review reported issues, set priorities and assign maintenance workers. Maintenance staff can update the progress of assigned tasks, record resolution notes and close completed requests. The system also keeps a record of maintenance activities and provides basic statistics to help monitor the state of reported problems. Students, staff, maintenance workers and administrators interact with CampusFIX, while these actors remain outside the system boundary.

###Constraints
The design of CampusFIX is influenced by the following constraints:

1. Technical constraint: The system is designed as a web application, so its components must communicate through a clear interface and support access through a web browser.
2. Organisational constraint: This is an individual semester project with limited development time and resources. Therefore, a simple architecture is more practical than a complex distributed system.
3. Budget constraint: The project has limited financial resources, so the design should favour affordable development tools and technologies rather than expensive commercial platforms.
4. Legal constraint: CampusFIX may handle personal information belonging to students and university employees. The design must therefore consider the Kenya Data Protection Act, 2019, particularly the protection of personal information and controlled access to user data.
5. Maintenance constraint: The system should be organised into separate components so that future changes can be made without unnecessarily affecting the entire application.

###Architecture Diagram
Architecture pattern: Three-Tier Layered Architecture
The architecture diagram will show how the presentation, application and data layers work together to support CampusFIX.

###Pattern Choice
Three-Tier Layered Architecture
Field| Description
Pattern| Three-Tier Layered Architecture
How it appears in my design| CampusFIX is divided into the presentation layer, application layer and data layer. Each layer has its own responsibility and communicates with the next layer.
Why it fits my requirements and constraints| The system handles different activities, including user authentication, maintenance reporting, request assignment and status updates. Separating these activities makes the system easier to organise and develop.
Advantages I am relying on| Easier maintenance, separation of responsibilities, better organisation of code and the ability to modify one layer without redesigning the entire system.
Disadvantages I am accepting| Communication between layers can introduce additional processing, and a problem in one important layer may affect the whole application.
One alternative I considered and why I rejected it| A monolithic architecture was considered because it can be simpler to build initially. However, it combines responsibilities more closely, making future maintenance and modification harder as CampusFIX grows.
###Components

CampusFIX is divided into several components, with each component handling a specific responsibility. This separation helps keep the system organised and makes it easier to maintain and improve in the future.

| Component | Its one job | Use cases it supports | Requirements supported |
|---|---|---|---|
| User Interface | Provides screens through which users interact with CampusFIX. | All use cases | FR-01 to FR-16 |
| Authentication Component | Handles user login, logout and access verification. | Log In, Log Out | FR-01, FR-02, FR-16 |
| Request Management Component | Handles the creation, validation and storage of maintenance requests. | Submit Maintenance Request, View Submitted Requests | FR-03, FR-04, FR-05, FR-06, FR-07 |
| Request Assignment Component | Handles request prioritisation and assignment to maintenance workers. | Set Request Priority, Assign Maintenance Worker | FR-08, FR-09, FR-16 |
| Maintenance Workflow Component | Handles request progress, status updates, resolution notes and closure. | Update Request Status, Record Resolution Notes, Close Maintenance Request | FR-10, FR-11, FR-13, FR-16 |
| Request History Component | Maintains records of important changes made to maintenance requests. | Check Request Status, View Request History | FR-12 |
| Dashboard and Reporting Component | Displays maintenance statistics and helps users filter and monitor requests. | Search and Filter Requests, View Maintenance Dashboard | FR-14, FR-15 |
| Database Component | Stores and retrieves user accounts, maintenance requests, assignments and activity records. | Supports all use cases requiring stored information | FR-01 to FR-16 |

**Component interaction:** The User Interface receives requests from users and forwards them to the appropriate application component. Application components process the requests and communicate with the Database Component whenever information needs to be stored or retrieved. The results are then returned to the user through the interface.
