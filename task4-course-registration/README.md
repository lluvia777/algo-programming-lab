# Task 4: University Course Registration System

## System Description
This project models the general flow of a university course registration system, including user login, course list display, course selection, strict validation checks, and final confirmation. 

During the registration process, the system performs five essential validation checks sequentially:
1. **Quota:** Checks if the course has available seats.
2. **Prerequisites:** Verifies if the student has passed required prior courses.
3. **Schedule Conflicts:** Ensures the new course does not overlap with existing schedules.
4. **Credit Limit:** Confirms the student does not exceed the maximum allowed credits (30 credits).
5. **Advisor Approval:** Checks if the academic advisor has approved the selection.

## Personal Notes
In this task, I learned how to implement strict validation mechanisms using deeply nested `IF-THEN` structures. Visualizing these nested conditions required representing every single control point as a decision diamond in Graphviz (DOT) and Mermaid formats, which helped me understand the step-by-step filtering logic of complex systems.
