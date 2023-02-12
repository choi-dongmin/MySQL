# IS NULL / IS NOT NULL

## IS NULL
- 컬럼의 NULL 값을 가진 데이터를 반환
> `WHERE NAME IS NULL`
>> NAME 컬럼에서 NULL 값인 데이터를 추출

> 프로그래머스 문제
>>[나이 정보가 없는 회원 수 구하기
](https://school.programmers.co.kr/learn/courses/30/lessons/131528)
```
SELECT
    COUNT(USER_ID) AS USERS
FROM 
    USER_INFO 
WHERE
    AGE IS NULL
```

## IS NOT NULL
- 컬럼의 NULL 값을 가진 데이터를 반환 하지않 은
> `WHERE NAME IS NOT NULL`
>> NAME 컬럼에서 NULL 데이터를 출력하지 않음