# Quiz 037

An Accounting firm needs a software package to calculate compound interest.

```.py
class CompoundInterest:
    def __init__(self,principal:int, rate:float, year:int):
        self.principal = principal
        self.rate = rate
        self.year = year


class AccountingProgram:
    def __init__(self):
        self.compound = CompoundInterest(0,0,0)
    def set_principal(self,principal):
        if principal <= 0:
            raise ValueError("Principal should be greater than zero")
        self.compound.principal = principal
        return f"Principal set to {self.compound.principal}"

    def set_rate(self,rate):
        if rate <= 0:
            raise ValueError("Interest rate should be greater than zero")
        self.compound.rate = rate
        return f"Rate set to {self.compound.rate}"

    def set_years(self, year):
        if year <= 0:
            raise ValueError("Years should be greater than zero")
        self.compound.year = year
        return f"Year set to {self.compound.year}"

    def calculate_interest(self):
        temp = self.compound.principal*(1+self.compound.rate)**self.compound.year
        format_float = "{:.2f}".format(temp)
        return float(format_float)
```

<img width="1512" alt="Screen Shot 2023-02-05 at 4 06 47 PM" src="https://user-images.githubusercontent.com/111751273/216806335-f70317c2-0776-460a-bd99-83e78c750c0d.png">


## UML Diagram
![Quizzes-27](https://user-images.githubusercontent.com/111751273/216806659-84ddb719-9245-49f2-b613-d6629345e500.jpg)

