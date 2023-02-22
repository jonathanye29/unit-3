# Quiz 048

Check that there is no fraud in the database by checking the hash signature of each transaction

```.py
from secure_password import check_password
import sqlite3
end_code = "\033[00m"
red = "\033[0;31m"
green = "\033[0;32m"
class database_worker:
    def __init__(self, name):
        self.connection = sqlite3.connect(name)
        self.cursor = self.connection.cursor()

    def search(self, query):
        result = self.cursor.execute(query).fetchall()
        return result

    def run_save(self, query):
        self.cursor.execute(query)
        self.connection.commit()

    def close(self):
        self.connection.close()

x = database_worker("bitcoin_exchange.db")
query = "SELECT * from ledger"
result = x.search(query)
# print(result)
x.close()

for row in result:
    # print(row)
    hash = row[4]
    string_hash = f"id {row[0]},sender_id {row[1]},receiver_id {row[2]},amount {row[3]}"
    equal = check_password(hashed_password=hash, user_password=string_hash)

    if equal == True:
        print(f"{green}Tx(id={row[0]})Signature matches{end_code}")
    else:
        print(f"{red}[1;31m Tx(id={row[0]})Error signature {end_code}")
```

## Proof
<img width="1512" alt="Screen Shot 2023-02-23 at 12 34 38 AM" src="https://user-images.githubusercontent.com/111751273/220672584-ea9936c2-f315-498b-bfc7-313b32bb351c.png">
