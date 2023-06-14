# FUNCTION FOR CALCULATING MAXIMUM WEIGHT DIFFERENCE
## CREATE FUNCTION CalculateMaxWeightDifference(N INT, K INT, weights VARCHAR(255))
## return INT
## BEGIN
##    DECLARE chef_weight INT DEFAULT 0;
##    DECLARE son_weight INT DEFAULT 0;
##    DECLARE i INT DEFAULT 1;
##    DECLARE weight INT;

## -- here we are Parsing the weights  into a temporary table
## CREATE TEMPORARY TABLE temp_weights (weight INT);

##    WHILE i <= LENGTH(weights) DO
##        INSERT INTO temp_weights (weight) VALUES (weight);
##        SET i = i + 1;
##    END WHILE;

## -- here we are sorting the weight in the ascending order
##    SELECT weight INTO weight
##    FROM temp_weights
##    ORDER BY weight;
    
## -- From the below query we are Calculating the weights carried by Chef and his son
##    SET i = 1;
##    WHILE i <= N DO
##        IF i <= K THEN
##            SELECT weight INTO son_weight
##            FROM temp_weights
##            LIMIT 1;
##        ELSE
##            SELECT weight INTO chef_weight
##            FROM temp_weights
##            WHERE weight > son_weight
##            ORDER BY weight
##            LIMIT 1;
##            SET chef_weight = chef_weight + weight;
##        END IF;
##       SET i = i + 1;
##    END WHILE;
    
##    -- Calculate and return the maximum possible weight difference
##    RETURN chef_weight - son_weight;
## END;



## --------------------------------------------------------------------------------------------------------------
# After we execute the above function we have to call the function 
# Test Case 1 :- 
## SELECT CalculateMaxWeightDifference(5, 2, '8 4 5 2 10') AS max_difference;
# Test Case 2 :- 
## SELECT CalculateMaxWeightDifference(8, 3, '1 1 1 1 1 1 1 1') AS max_difference_1;

