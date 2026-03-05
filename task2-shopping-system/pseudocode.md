START
Set logged_in = FALSE
Set cart_total = 0
Set shopping_complete = FALSE

// Control Point 1: User Login
LOOP WHILE logged_in == FALSE
    PRINT "Please log in to your account:"
    READ credentials
    
    IF credentials == valid THEN
        Set logged_in = TRUE
        PRINT "Login successful."
    ELSE
        PRINT "Invalid login. Try again."
    END IF
END LOOP

// Control Point 2 & 3: Adding Products and Stock Check
LOOP WHILE shopping_complete == FALSE
    PRINT "Enter product ID to add to cart (or type 'DONE' to checkout):"
    READ product_input
    
    IF product_input == "DONE" THEN
        Set shopping_complete = TRUE
    ELSE
        // Control Point 3: Stock Checking
        IF stock_of(product_input) > 0 THEN
            Set cart_total = cart_total + price_of(product_input)
            Decrease stock_of(product_input) by 1
            PRINT "Product added. Current total: " + cart_total
        ELSE
            PRINT "Error: Product is currently out of stock."
        END IF
    END IF
END LOOP

// Control Point 4: Applying Discount Code
PRINT "Do you have a discount code? (YES/NO)"
READ has_discount

IF has_discount == "YES" THEN
    PRINT "Enter your discount code:"
    READ code
    IF code == valid_code THEN
        Set cart_total = cart_total - discount_amount
        PRINT "Discount applied successfully."
    ELSE
        PRINT "Invalid discount code."
    END IF
END IF

// Control Point 5: Shipping Fee Calculation
// Free shipping threshold is assumed to be 500
IF cart_total < 500 THEN
    Set cart_total = cart_total + 50
    PRINT "A shipping fee of 50 has been added to your order."
ELSE
    PRINT "Congratulations! You get free shipping."
END IF

// Control Point 6: Payment Processing
PRINT "Your total amount is: " + cart_total
PRINT "Do you want to process the payment? (YES/NO)"
READ process_payment

IF process_payment == "YES" THEN
    PRINT "Payment successful. Thank you for your order!"
ELSE
    PRINT "Payment cancelled. Cart saved for later."
END IF

END
