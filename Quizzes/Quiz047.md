# Quiz 047

<img width="1036" alt="Screen Shot 2023-02-23 at 12 25 56 AM" src="https://user-images.githubusercontent.com/111751273/220669181-5808e9a7-84b2-41ad-818b-89382758d034.png">

## Python
```.py
import sqlite3
from kivymd.app import MDApp
from secure_password import encrypt_password

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


class quiz047(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.components = {"basic":0}

    def build(self):
        return

    def save(self):
        pass

    def update(self):
        base = self.root.ids.base.text
        hash = ""
        ids = ["inhabitant", "income_tax", "pension", "health"]

        if base != "":
            total = int(base)
            hash += f"base{total}"
            for each in ids:
                value = self.root.ids[each].text
                if value != "":
                    new_value = f"{int(value) * int(base) // 100} JPY"
                    total -= int(value) * int(base) / 100
                    hash += f"id_of_textField{value}"
                else:
                    new_value = " JPY"
                    hash += f"id_of_textField{0}"
                self.root.ids[f"{each}_label"].text = new_value
            hash += f"total{total}"
            self.root.ids.salary_label.text = f"{total} JPY"
            encrypted_hash = encrypt_password(hash)
            self.root.ids.hash.text = encrypted_hash[len(encrypted_hash)-50:len(encrypted_hash)]

    def save(self):
        base = self.root.ids.base.text
        hash = ""
        ids = ["inhabitant", "income_tax", "pension", "health"]

        if base != "":
            total = int(base)
            hash += f"base{total}"
            for each in ids:
                value = self.root.ids[each].text
                if value != "":
                    new_value = f"{int(value) * int(base) // 100} JPY"
                    total -= int(value) * int(base) / 100
                    hash += f"id_of_textField{value}"
                else:
                    new_value = " JPY"
                    hash += f"id_of_textField{0}"
                self.root.ids[f"{each}_label"].text = new_value
            hash += f"total{total}"
            self.root.ids.salary_label.text = f"{total} JPY"
            encrypted_hash = encrypt_password(hash)
            self.root.ids.hash.text = encrypted_hash[:50]

        inhabitant = int(self.root.ids.inhabitant_label.text.split(" JPY")[0])
        income_tax = int(self.root.ids.income_tax_label.text.split(" JPY")[0])
        pension = int(self.root.ids.pension_label.text.split(" JPY")[0])
        health = int(self.root.ids.health_label.text.split(" JPY")[0])
        total = int(self.root.ids.salary_label.text.split(" JPY")[0].split('.')[0])
        hash = self.root.ids.hash.text

        query = f"INSERT into payments(base, inhabitant, income_tax, pension, health, total, hash) values('{int(base)}', '{inhabitant}', '{income_tax}', '{pension}', '{health}', '{total}', '{hash}')"
        db = database_worker("payments.db")
        db.run_save(query)
        db.close()
        self.root.ids.hash.text = f"Payment saved"

    def clear(self):
        for label in ["base", "inhabitant","income_tax","pension","health"]:
            self.root.ids[label].text = ""
            self.root.ids[label+"_label"].text = " JPY"

        self.root.ids["salary_label"].text = " JPY"
        self.root.ids.hash.text = "----"

    def check_fraud(self):
        x = database_worker("payments.db")
        query = "SELECT * from payments"
        result = x.search(query)
        x.close()

        for each in result:
            base = each[1]
            inhabitant = each[2]
            income_tax = each[3]
            pension = each[4]
            health = each[5]
            total = each[6]
            hash = each[7]
            hash = hash[len(hash)-50:len(hash)]
            hash_to_check = f"base{base},inhabitant{int(inhabitant)//int(base) * 100},income_tax{int(income_tax)//int(base) * 100},pension{int(pension)//int(base)*100},health{int(health)//int(base)*100},total{int(total)//int(base)*100}"
            encrypted_hash = encrypt_password(hash_to_check)
            if encrypted_hash[len(encrypted_hash)-50:len(encrypted_hash)] == hash:
                print(f"Payment {each[0]} is not fraud")
            else:
                print(f"Payment {each[0]} is fraud")

test = quiz047()
create = """CREATE TABLE if not exists payments(
            id INTEGER PRIMARY KEY,
            base int,
            inhabitant int,
            income_tax int,
            pension int,
            health int
            total int,
            hash text
    )"""
test.check_fraud()
test.run()

```

## Proof
<img width="1512" alt="Screen Shot 2023-02-23 at 12 28 46 AM" src="https://user-images.githubusercontent.com/111751273/220670554-0a3e7c50-1424-43a1-98ae-1e84dbd1832e.png">

