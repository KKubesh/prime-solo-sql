# prime-solo-sql

CREATE TABLE accounts (
    user_id serial PRIMARY KEY,
    username character varying(12),
    city character varying(128),
    transactions_completed integer,
    transactions_attempted integer,
    account_balance numeric(12,2)
);

INSERT INTO accounts (username, city, transactions_completed, transactions_attempted, account_balance) VALUES ('shawn', 'chicago', 5, 10, 355.80),
('cherise', 'minneapolis', 9, 9, 4000.00),
('larry', 'minneapolis', 3, 4, 77.01),
('dallas', 'new york', 6, 12, 0.99),
('anthony', 'chicago', 0, 0, 0.00),
('travis', 'miami', 1, 100, 500000.34),
('davey', 'chicago', 9, 99, 98.04),
('ora', 'phoenix', 88, 90, 3.33),
('grace', 'miami', 7, 9100, 34.78),
('hope', 'phoenix', 4, 10, 50.17);

-- 1. Get all the users
SELECT * FROM accounts WHERE "city" = 'chicago';

-- 2. Get all the users that contain the letter a
SELECT * FROM accounts WHERE "username" ILIKE '%a%';

-- 3. Get all the new users a new customer bonus of 10 dollars
UPDATE accounts SET "account_balance" = 10.00 WHERE "account_balance" = 0;

-- 4. Get all the users that have more than 9 transactions
SELECT * FROM accounts WHERE "transactions_attempted" > 9;

-- 5. username and account balance of the 3 users with the highest balances, sort highest to lowest balance. 
SELECT "username", "account_balance" FROM accounts 
ORDER BY "account_balance" DESC LIMIT 3;

-- 6. username and account balance of the 3 users with the lowest balances, sort lowest to highest balance. 
SELECT "username", "account_balance" FROM accounts 
ORDER BY "account_balance" ASC LIMIT 3;

-- 7. Get all the users with balance greater than 100 dollars
SELECT * FROM accounts WHERE "account_balance" > 100.00;

-- 8. Add a new record
INSERT INTO accounts ("username", "city", "account_balance") 
VALUES ('john', 'blaine', 129.00);

-- 9. Delete users that reside in miami OR phoenix and have completed fewer than 5 transactions
SELECT * FROM accounts WHERE ("city" = 'miami' OR "city" = 'phoenix') AND "transactions_completed" < 5;
/* Actually DELETE */
DELETE FROM accounts WHERE ("city" = 'miami' OR "city" = 'phoenix') AND "transactions_completed" < 5;
