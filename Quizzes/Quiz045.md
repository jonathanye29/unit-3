# Quiz 045

<img width="1036" alt="Screen Shot 2023-02-22 at 11 58 01 PM" src="https://user-images.githubusercontent.com/111751273/220660609-615238cb-f8d0-4320-b197-a97b510324f4.png">

## SQL
```.sql
select account_id, sum(case when transaction_type = 'withdraw' then amount else 0 end) as withdraw, sum(case when transaction_type = 'deposit' then amount else 0 end) as deposit, sum(case when transaction_type = 'withdraw' then amount else 0 end) - sum(case when transaction_type = 'deposit' then amount else 0 end) as expected_balance from transactions group by account_id;

select accounts.account_id, accounts.balance, sum(case when transaction_type = 'withdraw' then amount else 0 end) as withdraw, sum(case when transactions.transaction_type = 'deposit' then amount else 0 end) as deposit, sum(case when transactions.transaction_type = 'deposit' then amount else 0 end) - sum(case when transactions.transaction_type = 'withdraw' then amount else 0 end) as expected_balance from transactions inner join accounts on transactions.account_id = accounts.account_id group by accounts.account_id;

SELECT
  CASE
    WHEN total_deposit - total_withdraw != balance THEN 'fraud'
    ELSE 'clear'
  END AS 'Status',
  total_deposit,
  total_withdraw,
  balance,
  account_id
FROM (
  SELECT
    SUM(amount) AS total_deposit,
    account_id AS account_deposit
  FROM transactions
  WHERE transaction_type = 'deposit'
  GROUP BY account_id
),
(
  SELECT
    SUM(amount) AS total_withdraw,
    account_id AS account_withdraw
  FROM transactions
  WHERE transaction_type = 'withdraw'
  GROUP BY account_id
),
accounts
WHERE account_deposit = account_withdraw
  AND account_deposit = accounts.account_id;

SELECT customers.first_name, customers.last_name, accounts.account_id
FROM customers
JOIN accounts
ON customers.customer_id = accounts.customer_id
WHERE accounts.account_id IN (12, 13, 15, 17, 19);
```

## Proof
<img width="1009" alt="Screen Shot 2023-02-23 at 12 18 53 AM" src="https://user-images.githubusercontent.com/111751273/220666973-bb160988-a130-4c82-9d5c-9cec5387f2d9.png">

