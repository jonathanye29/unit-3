# Quiz 038

Create a program that creates the SalemanMap using your OOP code

```.py
import random
import matplotlib.pyplot as plt

class coordinates:
    def __init__(self, x: int, y: int):
        self.x = x
        self.y = y

    def __repr__(self)->str:
        return f"[Coordinate Object] x:{self.x}, y:{self.y}"

class city:
    def __init__(self, name:str, location:coordinates):
        self.name = name
        self.location = location

    def __repr__(self)->str:
        return f"[City Object] {self.name} is located at {self.location}"

    def distance(self, cityB):
        # if isinstance(cityB, city):
        xa, ya = self.location.x, self.location.y
        xb, yb = cityB.location.x, cityB.location.y
        # else:
        #     raise TypeError("Input should be an object of the class city")
        d = ((xa-xb)**2 + (ya-yb)**2)**(1/2)
        return round(d, 2)

class country:
    def __init__(self, name:str):
        self.name = name
        self.cities = []

    def add_city(self, new_city:city):
        self.cities.append(new_city)

    def plot_cities(self):
        x = []
        y = []
        for i in self.cities:
            x.append(i.location.x)
            y.append(i.location.y)
            plt.text(i.location.x + 2, i.location.y, i.name)
        plt.plot(x, y, 'ro')
        plt.show()

    def __repr__(self)->str:
        return f"[Country Object] Country {self.name} contains {len(self.cities)} cities."



point1 = coordinates(x=5, y=5)
print(point1)
tokyo = city(name="Tokyo", location=point1)
kyoto = city(name="Kyoto", location=coordinates(x=10, y=10))
print(tokyo)
Japan = country(name="Japan")

for name in ["Tokyo", "Kyoto", "Osaka", "Nara", "Okinawa", "Hiroshima", "Sapporo", "Niseko", "Fukuoka", "Kawasaki"]:
    rand_loc = coordinates(x = random.randint(1, 100), y = random.randint(1,100))
    ct = city(name=name, location=rand_loc)
    Japan.add_city(ct)

#distance from tokyo to any other
for city in Japan.cities:
    d = Japan.cities[0].distance(cityB=city)
    print(f"Distance between {Japan.cities[0].name} and {city.name} is {d}")


#get the total km of a route from tokyo visiting all cities
total = 0
for i in range(len(Japan.cities)):
    if i == len(Japan.cities)-1:
        total += Japan.cities[i].distance(cityB=Japan.cities[0])
    else:
        total += Japan.cities[i].distance(cityB=Japan.cities[i+1])
print(f"Total distance of the route is {total}km")

Japan.plot_cities()
```

<img width="1512" alt="Screen Shot 2023-02-05 at 4 22 14 PM" src="https://user-images.githubusercontent.com/111751273/216806871-92c137c1-4f81-461c-9031-9512d3e27582.png">

