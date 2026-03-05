# Task 2: E-Commerce Cart & Checkout System

## System Description
This project models the checkout flow of an online shopping platform. It includes several sequential control points to ensure a secure and logical transaction:
* **User Authentication:** A verification loop ensuring the user is successfully logged in before shopping.
* **Cart & Stock Management:** Allows users to add multiple products while checking real-time stock availability.
* **Discount Application:** Evaluates user input for a valid discount code and adjusts the total price accordingly.
* **Shipping Calculation:** Automatically adds a shipping fee if the cart total is below the free shipping threshold (500 TL).
* **Payment Processing:** Final confirmation step to complete the order.

## Personal Notes
Designing this system helped me understand how to link multiple independent control points sequentially. I learned how to manage cumulative variables (like `cart_total`) across different conditions. Furthermore, using `rankdir=TB` in Graphviz allowed me to create a top-to-bottom vertical flowchart, which makes reading complex e-commerce steps much more intuitive.
