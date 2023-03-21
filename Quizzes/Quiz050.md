# Quiz 50
<img width="960" alt="Screen Shot 2023-03-21 at 11 56 24 AM" src="https://user-images.githubusercontent.com/111751273/226514049-6ad38e53-7859-4a6f-84de-b128a0f0932a.png">

## Code
```.py
class flight():
    def __init__(self, flight_number:str, origin:str, destination:str, departure_time:str, duration:list[int]):
        self.flight_number = flight_number
        self.origin = origin
        self.destination = destination
        self.departure_time = departure_time
        self.duration = duration

    def get_duration(self):
        return f"{self.duration[0]} hours {self.duration[1]} minutes {self.duration[2]} seconds"


flight1 = flight("HX609", "NRT","HKG","12:00",[5,45,55])
flight2 = flight("AA321", "NRT", "DFW", "15:00", [12,30,25])

print(flight1.get_duration())
print(flight2.get_duration())
```

## Proof
<img width="1512" alt="Screen Shot 2023-03-21 at 11 59 03 AM" src="https://user-images.githubusercontent.com/111751273/226514314-89a84460-e99e-43cc-a8e2-391149052d4b.png">
