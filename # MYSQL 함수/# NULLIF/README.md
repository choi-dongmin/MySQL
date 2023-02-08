# NULLIF

[참고](https://www.w3schools.com/sql/func_sqlserver_nullif.asp)

- `SELECT NULLIF(값1, 값2)`
- 값1,2를 비교하여 동일한 값인 경우 NULL 아닐 경우 값1을 출력하는 함수.


```SQL
SELECT NULLIF('Hello', 'Hello');	// NULL
SELECT NULLIF('Hello', 'World');	// Hello
```

