# Quiz 033

Write the function mystery and pass the tests contained in the file test_quiz_33.py

```.py

def mystery(list1, list2:list):
    output = []
    for i in range(len(list1)):
        for j in range(len(list2)):
            if list1[i] == list2[j]:
                output.append(list1[i])
    return output
```

<img width="1512" alt="Screen Shot 2023-02-05 at 3 24 11 PM" src="https://user-images.githubusercontent.com/111751273/216805021-f5e91c82-36dd-4d15-8c46-506a0082e4a5.png">

