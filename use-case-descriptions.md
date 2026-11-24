# CampusFIX – Use Case Descriptions

The following use cases describe the main tasks people will carry out in CampusFIX. They follow the process in the SRS: **Report → Triage → Assignment → In Progress → Resolved → Closed**.

## UC1: Submit Maintenance Request

**Actor(s):** Student/Staff.

**Goal:** Report a facilities problem and make sure the details are recorded so that it can be followed up.

**Precondition:** The student or staff member has a valid CampusFIX account and is logged in.

**Main flow:**
1. The student/staff member chooses the option to report a maintenance problem.
2. CampusFIX opens the maintenance request form.
3. The user selects the problem category, enters the location and describes the problem.
4. CampusFIX checks that the required information has been entered.
5. The user submits the request.
6. CampusFIX records the date and time, generates a unique request ID and saves the request.
7. CampusFIX confirms that the request has been submitted and displays its reference ID.

**Alternative flows:**
- **Step 3 – Missing details:** If the category, location or description is missing, CampusFIX points out what needs to be completed. The user adds the missing information and continues.
- **Step 4 – Invalid information:** If the information does not pass validation, CampusFIX explains that the request cannot yet be saved and asks the user to correct it.
- **Step 6 – Saving problem:** If the request cannot be saved, CampusFIX displays an error instead of showing a successful submission. The user can try again later.

**Postcondition:** If successful, the request is stored with its category, location, description, date and time, and unique ID. If saving fails, the system does not present the request as successfully submitted.

## UC2: Review, Prioritise and Assign Maintenance Request

**Actor(s):** Administrator/Supervisor (starts and manages the process); Maintenance Staff (receives the assignment).

**Goal:** Make sure a reported problem is reviewed, given an appropriate priority and assigned to a maintenance worker.

**Precondition:** A maintenance request has been submitted and saved. The administrator/supervisor is logged in and has permission to manage requests.

**Main flow:**
1. The administrator/supervisor opens the list of maintenance requests.
2. CampusFIX displays requests that the administrator/supervisor is allowed to view.
3. The administrator/supervisor selects a request.
4. CampusFIX displays its category, location, description, reporting date and current status.
5. The administrator/supervisor chooses a priority: Low, Medium, High or Critical.
6. CampusFIX saves the selected priority.
7. The administrator/supervisor selects a maintenance worker for the request.
8. CampusFIX checks that the administrator/supervisor is authorised to make the assignment and records the selected worker.
9. CampusFIX updates the request status to **Assigned** and makes the assignment visible to the maintenance worker.

**Alternative flows:**
- **Step 2 – No matching requests:** If no requests are available, CampusFIX displays an appropriate message and the use case ends without making a change.
- **Step 5 – Priority not selected:** If the administrator/supervisor has not selected a priority, CampusFIX asks them to choose one before continuing.
- **Step 7 – No worker available:** If no suitable maintenance worker is available, the administrator/supervisor can leave the request unassigned and return to it later. The request remains saved.
- **Step 8 – Unauthorised assignment:** If a user without the required permission attempts to assign a worker, CampusFIX refuses the action and leaves the assignment unchanged.

**Postcondition:** The request remains stored with its selected priority. If assignment succeeds, the assigned worker and **Assigned** status are recorded. If assignment is refused or no worker is available, the request remains saved without an incorrect assignment.

## UC3: Update and Resolve Maintenance Request

**Actor(s):** Maintenance Staff (updates the work); Administrator/Supervisor (may review and close the request).

**Goal:** Keep the request's progress up to date and record what was done to resolve the problem.

**Precondition:** The request has been assigned to the maintenance worker, who is logged in.

**Main flow:**
1. The maintenance worker opens the list of requests assigned to them.
2. CampusFIX displays the worker's assigned requests.
3. The worker selects the request they are handling.
4. CampusFIX displays the request details and current status.
5. The worker starts the repair and changes the status to **In Progress**.
6. CampusFIX saves the status change in the request record and history.
7. When the repair is complete, the worker enters notes describing the work performed and how the problem was handled.
8. CampusFIX saves the resolution notes and the worker updates the status to **Resolved**.
9. The administrator/supervisor reviews the completed request and closes it when satisfied that the problem has been resolved.
10. CampusFIX records the closure and changes the status to **Closed**.

**Alternative flows:**
- **Step 3 – Request not assigned to this worker:** CampusFIX refuses the update because maintenance workers should only update requests assigned to them. The request remains unchanged.
- **Step 5 – Work is still ongoing:** The worker updates the progress but leaves the request as **In Progress**. They can return to it when the work continues.
- **Step 7 – Resolution notes missing:** CampusFIX asks the worker to enter resolution information. The request cannot be treated as resolved until the required notes are provided.
- **Step 9 – Problem not fully resolved:** If the administrator/supervisor is not satisfied with the result, the request is not closed. It is returned for further attention and remains available for follow-up.

**Postcondition:** The request history contains the recorded status changes. When the work is completed, resolution notes are stored and the request can be closed. If the problem remains unresolved, the request stays open for further work.
