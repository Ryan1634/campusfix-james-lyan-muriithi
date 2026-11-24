CampusFIX – Architecture and Design Rationale

1. System Overview
CampusFIX is a web-based maintenance management system designed to help students and university staff report facility-related problems within the university. It allows administrators and supervisors to review reported issues, set priorities and assign maintenance workers. Maintenance staff can update the progress of assigned tasks, record resolution notes and close completed requests. The system also keeps a record of maintenance activities and provides basic statistics to help monitor the state of reported problems. Students, staff, maintenance workers and administrators interact with CampusFIX, while these actors remain outside the system boundary.

2. Constraints
The design of CampusFIX is influenced by the following constraints:

1. Technical constraint: The system is designed as a web application, so its components must communicate through a clear interface and support access through a web browser.
2. Organisational constraint: This is an individual semester project with limited development time and resources. Therefore, a simple architecture is more practical than a complex distributed system.
3. Budget constraint: The project has limited financial resources, so the design should favour affordable development tools and technologies rather than expensive commercial platforms.
4. Legal constraint: CampusFIX may handle personal information belonging to students and university employees. The design must therefore consider the Kenya Data Protection Act, 2019, particularly the protection of personal information and controlled access to user data.
5. Maintenance constraint: The system should be organised into separate components so that future changes can be made without unnecessarily affecting the entire application.

3. Architecture Diagram
Architecture pattern: Three-Tier Layered Architecture
The architecture diagram will show how the presentation, application and data layers work together to support CampusFIX.

4. Pattern Choice
Three-Tier Layered Architecture
Field| Description
Pattern| Three-Tier Layered Architecture
How it appears in my design| CampusFIX is divided into the presentation layer, application layer and data layer. Each layer has its own responsibility and communicates with the next layer.
Why it fits my requirements and constraints| The system handles different activities, including user authentication, maintenance reporting, request assignment and status updates. Separating these activities makes the system easier to organise and develop.
Advantages I am relying on| Easier maintenance, separation of responsibilities, better organisation of code and the ability to modify one layer without redesigning the entire system.
Disadvantages I am accepting| Communication between layers can introduce additional processing, and a problem in one important layer may affect the whole application.
One alternative I considered and why I rejected it| A monolithic architecture was considered because it can be simpler to build initially. However, it combines responsibilities more closely, making future maintenance and modification harder as CampusFIX grows.
