# Task 1: ATM Cash Withdrawal System

## System Description
This project contains the algorithm and flowchart designs for a basic ATM cash withdrawal system. The system includes the following core functionalities:
* **Authentication:** A 3-attempt limit for PIN verification.
* **Amount Validation:** Ensuring the requested withdrawal amount is a multiple of 20 TL.
* **Limit & Balance Checks:** Verifying that the amount does not exceed the daily withdrawal limit (2000 TL) and the current account balance.
* **Continuous Flow:** Allowing the user to perform multiple transactions without needing to re-enter the PIN, using a loop structure.

## Personal Notes
In this task, I learned how to effectively use nested `IF-THEN-ELSE` statements for complex decision-making and 
`WHILE` loops for repetitive tasks like PIN attempts and repeated transactions. Converting the pseudocode 
into visual flowcharts using both Graphviz (DOT) and Mermaid helped me understand the logical flow of a program much better.
