# TRUNCATE

- 데이터 값으로 수가 있을때 버릴 자릿수를 지정하여 그 하위 값은 버린다.
> `SELECT COLUMM(12345, 1)  // 1의자리수  : 12340`
> `SELECT COLUMM(12345, -2)  // 10의자리수  : 12300`
> `SELECT COLUMM(12345, -3)  // 100의자리수  : 12000`
> `SELECT COLUMM(12345, -4)  // 1000의자리수  : 10000`

```SQL
SELECT TRUNCATE(123, -2) // 12
```