START
Set logged_in = FALSE
Set total_credits = 0
Set MAX_CREDITS = 30
Set registration_active = TRUE

// 1. Login Phase
LOOP WHILE logged_in == FALSE
    PRINT "Enter Student ID and Password:"
    READ credentials
    
    IF credentials == valid THEN
        Set logged_in = TRUE
        PRINT "Login successful."
    ELSE
        PRINT "Invalid credentials. Try again."
    END IF
END LOOP

PRINT "Displaying available Course List..."

// 2. Course Selection & Validation Loop
LOOP WHILE registration_active == TRUE
    PRINT "Enter Course Code to register (or type 'DONE' to finish):"
    READ course_code
    
    IF course_code == "DONE" THEN
        Set registration_active = FALSE
    ELSE
        // Validation 1: Quota Check
        IF check_quota(course_code) > 0 THEN
            
            // Validation 2: Prerequisite Check
            IF check_prerequisites(course_code) == TRUE THEN
                
                // Validation 3: Schedule Conflict Check
                IF check_schedule_conflict(course_code) == FALSE THEN
                    
                    // Validation 4: Credit Limit Check
                    IF total_credits + credits(course_code) <= MAX_CREDITS THEN
                        
                        // Validation 5: Advisor Approval Check
                        IF get_advisor_approval(course_code) == TRUE THEN
                            
                            // Confirmation
                            PRINT "Confirmation: Course successfully added!"
                            Set total_credits = total_credits + credits(course_code)
                            Decrease quota of course_code by 1
                            
                        ELSE
                            PRINT "Error: Advisor approval denied."
                        END IF
                        
                    ELSE
                        PRINT "Error: Credit limit exceeded."
                    END IF
                    
                ELSE
                    PRINT "Error: Schedule conflict detected."
                END IF
                
            ELSE
                PRINT "Error: Prerequisite conditions not met."
            END IF
            
        ELSE
            PRINT "Error: Course quota is full."
        END IF
    END IF
END LOOP

PRINT "Registration finalized. Total credits taken: " + total_credits
END
