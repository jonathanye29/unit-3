# Quiz 044
<img width="1035" alt="Screen Shot 2023-02-22 at 11 49 28 PM" src="https://user-images.githubusercontent.com/111751273/220658319-45a672ba-d7bd-422a-85d8-04c8db07149f.png">

## SQL
```.sql
select * from INHABITANT where gender = 'Male';
select * from INHABITANT where gender = 'Male' and state = 'Friendly';
SELECT AVG(gold) from INHABITANT group by villageid;
select * from ITEM where item like 'A%';
select job from INHABITANT group by job;
select item from ITEM where owner is 4 or owner is 18;
```

## Proof
![quiz044](https://user-images.githubusercontent.com/111751273/220660406-046278fd-eb63-4508-97fa-39053c8ed3dd.gif)
