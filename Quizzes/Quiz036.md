# Quiz 036

Create test cases for the classes below ② UML diagram. ③ Add another class Classroom which can store in a list student　objects, a method to add, remove students and method to calculate the average score.

```.py

class Person:
    def __init__(self, name:str, age:int):
        self.name = name
        self.age = age

    def get_name(self)->str:
        return self.name

    def get_age(self):
        return self.age

class Student(Person):
    def __init__(self, name:str, age:int, grade:int):
        super().__init__(name, age)
        self.name = name
        self. age = age
        self.grade = grade

    def get_grade(self):
        return self.grade

class Classroom:
    def __init__(self):
        self.students = []

    def add_student(self, student:Student):
        self.students.append(student)

    def remove_student(self, student:Student):
        if student not in self.students:
            raise ValueError("Class is empty")
        self.students.remove(student)

    def get_average_score(self):
        if len(self.students) == 0:
            raise ValueError("Classroom is empty")
        total = 0
        for student in self.students:
            total += student.get_grade()
        return total / len(self.students)
```

<img width="1512" alt="Screen Shot 2023-02-05 at 4 05 29 PM" src="https://user-images.githubusercontent.com/111751273/216806290-bb35c894-a167-4235-987d-74c0cdde3366.png">


