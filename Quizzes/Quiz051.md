# Quiz 51
<img width="941" alt="Screen Shot 2023-03-21 at 12 13 56 PM" src="https://user-images.githubusercontent.com/111751273/226515753-e06720ba-9aa6-4770-af51-b755e6d50e27.png">


## Code
```.py
class Wheel:
    def __init__(self, size: int):
        self.size = size
    def get_size(self):
        print(f"Wheel size: {self.size}")
    def get_perimeter(self):
        perimeter=round(self.size*3.1415*2.54,2)
        return perimeter
    def get_km_per_rotation(self):
        km= round(1000*100/self.get_perimeter(),2)
        return f"The wheel has {km} rotations per km"
class Bycicle:
    def __init__(self, material: str, wheelsize):
        self.material = material
        self.wheel = Wheel(wheelsize)
    def ride(self):
        print(f"Wheel size:{self.wheel.size}, frame material:{self.material}")

Bike=Bycicle(wheelsize=26, material="Aluminum")
print(Bike.wheel.get_km_per_rotation())
```

## Proof
<img width="1512" alt="Screen Shot 2023-03-21 at 12 14 12 PM" src="https://user-images.githubusercontent.com/111751273/226515780-9a24b330-fff7-40d3-b25d-846e0b6247fd.png">

