# MAX, MIN, AVG, ROUND, COUNT, SUM

[참고](https://www.w3schools.com/sql/sql_min_max.asp)

- MAX 
> 해당 컬럼중 가장 높은 값을 출력.
> `SELECT MAX(column_name)`

- MIN
> 해당 컬럼중 가장 낮은 값을 출력.
> `SELECT MIN(column_name)`

- AVG
> 해당 컬럼 값들의 총 평균.
> `SELECT AVG(column_name)`

- ROUND
> 해당 컬럼의 값이 소수일때 반올림.
> `SELECT ROUND(AVG(column_name))`

- COUNT
> COUNT()함수는 지정된 기준과 일치하는 컬럼 수를 반환.
> NULL은 무시됩니다.
> `SELECT COUNT(column_name)`

- SUM
> 지정된 컬럼의 총 합계를 반환.
> NULL 값은 무시됩니다.
> `SELECT SUM(column_name)`

> 프로그래머스 문제
>> [가장 비싼 상품 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/131697)
```SQL
SELECT MAX(PRICE) AS MAX_PRICE
FROM PRODUCT 
```