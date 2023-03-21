# Quiz 49

<img width="962" alt="Screen Shot 2023-03-21 at 11 54 08 AM" src="https://user-images.githubusercontent.com/111751273/226513837-8208422b-5a0b-490d-a47a-4812ab140715.png">

## Code
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

total = 0
for row in result:
    # print(row)
    hash = row[4]
    string_hash = f"id {row[0]},sender_id {row[1]},receiver_id {row[2]},amount {row[3]}"
    equal = check_password(hashed_password=hash, user_password=string_hash)

    if equal == True:
        total += int(row[3])
        print(f"{green}Tx(id={row[0]})Signature matches{end_code}")
    else:
        print(f"{red}[1;31m Tx(id={row[0]})Error signature {end_code}")

print(f"Total bitcoins transferred: {total} BTC")
```

## Proof
<img width="1512" alt="Screen Shot 2023-03-21 at 11 55 17 AM" src="https://user-images.githubusercontent.com/111751273/226513952-b2b3bd11-50e1-442b-9eb2-8737e8709ca0.png">
