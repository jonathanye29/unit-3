# Quiz 046

<img width="1037" alt="Screen Shot 2023-02-23 at 12 20 14 AM" src="https://user-images.githubusercontent.com/111751273/220667334-74958113-a618-405f-abe4-a4a0a0553223.png">

## Python
```.py
import sqlite3

haiku = """Code flows like a stream
Algorithms guide its way
In silence, it solves"""

connection = sqlite3.connect("quiz046.db")
cursor = connection.cursor()
query = f"""CREATE Table if not exists Words(
       id INTEGER PRIMARY KEY,
       word text NOT NULL unique
   )
   """
cursor.execute(query)
connection.commit()

# query the average of all the lengths
connection = sqlite3.connect("quiz046.db")
cursor = connection.cursor()
query = f"""SELECT AVG(LENGTH(word)) FROM Words"""
result = cursor.execute(query).fetchall()

# close database
connection.close()
print(f"average word length is {result}")

# get avg len of words using python
avg_len = sum([len(word) for word in haiku.split()])/len(haiku.split())
```

## Proof
<img width="1512" alt="Screen Shot 2023-02-23 at 12 24 21 AM" src="https://user-images.githubusercontent.com/111751273/220668694-e3372d6f-a9ed-408f-a3fe-828e7944d514.png">

