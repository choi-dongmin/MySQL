# CASE WHEN

[참고](https://www.w3schools.com/sql/sql_case.asp) 
- `CASE WHEN A > B THEN C ELSE D END AS ABCD`
- Case 에 대하여 만약 when 조건이 참이라면 THEN 아니라면 ELSE 를 출력.

```SQL
CASE WHEN 2 > 1 THEN 'T' ELSE 'F' END AS TF // T

CASE 10 WHEN 1 THEN 'one' WHEN 2 THEN 'Two' ELSE 'IDK' END AS ONETOWIDK // IDK
```

