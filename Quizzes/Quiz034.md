# Quiz 034

Create a new Python function called to_roman(num) that takes a single integer as input. It returns a string representing the Roman numeral equivalent of the input number. 

```.py
def to_roman(num:int)->str:
    if num > 100:
        raise ValueError("Input must me less than or equal to 100")
    roman = ""
    if num == 100:
        roman = "C"
        num = 0
    if num >= 90:
        roman += "XC"
        num -= 90
    if num >= 50:
        roman += "L"
        num -= 50
    if num >= 40:
        roman += "XL"
        num -= 40
    if num >= 10:
        roman += "X" * (num // 10)
        num %= 10
    if num >= 9:
        roman += "IX"
        num -= 9
    if num >= 5:
        roman += "V"
        num -= 5
    if num >= 4:
        roman += "IV"
        num -= 4
    if num >= 1:
        roman += "I" * num
    return roman
```

<img width="1512" alt="Screen Shot 2023-02-05 at 3 35 12 PM" src="https://user-images.githubusercontent.com/111751273/216805311-fb188023-3ef2-42a7-908d-b0b992d44477.png">

    
