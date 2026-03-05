START
Set correct_PIN = "1234"
Set balance = 5000
Set daily_limit = 2000
Set attempts = 0
Set authenticated = FALSE

// PIN Verification Loop (Max 3 attempts)
LOOP WHILE attempts < 3 AND authenticated == FALSE
    PRINT "Please enter your PIN:"
    READ input_PIN
    
    IF input_PIN == correct_PIN THEN
        Set authenticated = TRUE
        PRINT "PIN accepted. Welcome!"
    ELSE
        Set attempts = attempts + 1
        PRINT "Incorrect PIN. Attempts remaining: " + (3 - attempts)
    END IF
END LOOP

// Main Transaction Flow
IF authenticated == TRUE THEN
    Set continue_transaction = "YES"

    LOOP WHILE continue_transaction == "YES"
        PRINT "Enter withdrawal amount (Multiples of 20TL):"
        READ amount

        IF amount % 20 != 0 THEN
            PRINT "Error: Amount must be a multiple of 20TL."
        ELSE
            IF amount > daily_limit THEN
                PRINT "Error: Amount exceeds your daily withdrawal limit."
            ELSE
                IF amount > balance THEN
                    PRINT "Error: Insufficient balance."
                ELSE
                    // Process Withdrawal
                    Set balance = balance - amount
                    Set daily_limit = daily_limit - amount
                    PRINT "Please take your cash: " + amount + "TL"
                    PRINT "Your new balance is: " + balance + "TL"
                END IF
            END IF
        END IF

        PRINT "Do you want to perform another transaction? (YES/NO):"
        READ continue_transaction
    END LOOP
    
    PRINT "Thank you for using our ATM. Please take your card."
ELSE
    PRINT "Too many incorrect attempts. Your card has been retained."
END IF
END
