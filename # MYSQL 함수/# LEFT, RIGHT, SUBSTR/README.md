# LEFT, RIGHT, SUBSTR

## LEFT
- 문자열 또는 컬럼의 왼쪽에서부터 N번째까지 잘라주는 것

```SQL
SELECT LEFT("20221212", 2) // 20
```

## RIGHT
- 문자열 또는 컬럼의 오른쪽에서부터 N번째까지 잘라주는 것

```SQL
SELECT RIGHT("20221212", 2) // 12
```

## SUBSTR
- 문자열 또는 컬럼의 시작과 끝을 지정해 문자열을 자른다.
```SQL
SELECT SUBSTR("20221212", 2, 5) // 02212
```