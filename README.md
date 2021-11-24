# internHomework
      Обязательные задания по SQL.

Решение задания №1
```SQL
SELECT name, COUNT(*) as count
FROM Passenger
JOIN Pass_in_trip on 
Passenger.id = Pass_in_trip.passenger
JOIN Trip on Trip.id = Pass_in_trip.trip and Trip.time_out <= now()
GROUP BY Passenger.id, Passenger.name
HAVING COUNT(*) >= 1
ORDER BY 
count DESC,
name ASC  
```
Решение задания №2
```SQL
SELECT DISTINCT TIMEDIFF(
    (SELECT end_pair FROM Timepair WHERE id=4),
    (SELECT start_pair FROM Timepair WHERE id=2)
    ) AS time 
FROM Timepair; 
```
Решение задания №3
```SQL
SELECT DISTINCT Rooms.*
FROM Rooms
JOIN Reservations
ON Rooms.id=Reservations.room_id
WHERE WEEK(start_date, 1) = 12 AND YEAR(start_date)=2020 
```
Решение задания №4
```SQL
SELECT classroom
FROM Schedule
GROUP BY classroom
HAVING COUNT(classroom) = 
(SELECT COUNT(classroom)
FROM Schedule
GROUP BY classroom
ORDER BY count(classroom) DESC
LIMIT 1)
```
Решение задания №5



Решение задания №6
```SQL
WITH 
t1 AS
(SELECT ROW_NUMBER() OVER (ORDER BY DATE) num1, 
name,
date,
NTILE(2) OVER (ORDER BY DATE) group1
FROM Battles t1),
t2 AS 
(SELECT *, ROW_NUMBER() OVER (PARTITION BY group1 ORDER BY DATE) num2
FROM t1)
SELECT 
    max(iif(group1 = 1, num1, null)),
    max(iif(group1 = 1, name, null)),
    max(iif(group1 = 1, date, null)),
    max(iif(group1 = 2, num1, null)),
    max(iif(group1 = 2, name, null)),
    max(iif(group1 = 2, date, null))
FROM t2
GROUP BY num2
```

              ДОПОЛНИТЕЛЬНЫЕ ЗАДАНИЯ

    МАТЕМАТИКА (Решение описано в прикрепленных фотографиях)
    
Задание №1

Ответ: 1/448

Задание №2

Ответ: Доверительный интервал - 8% +- 3%

Задание №3

Ответ: Теснота связи - умеренная (~-0.5)

      ОСНОВЫ ПРОГРАММИРОВАНИЯ
      
Задание №1
```Python
N = 7
A = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print('Массив = ', A)
NX = -1
NY = -1
for i in range(10):
    for j in range(10):
        if A[i]+A[j] == N:
            NX = i
            NY = j
    if NX+NY != -2:
        print("[",NX,"] + [", NY, "]")
        NX = -1
        NY = -1
 ```       
Вывод:
Массив =  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[ 0 ] + [ 5 ]
[ 1 ] + [ 4 ]
[ 2 ] + [ 3 ]
[ 3 ] + [ 2 ]
[ 4 ] + [ 1 ]
[ 5 ] + [ 0 ]

Process finished with exit code 0
