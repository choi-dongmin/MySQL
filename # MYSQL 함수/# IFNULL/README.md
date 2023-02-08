# IFNULL

- IFNULL

[참고](https://www.w3schools.com/sql/func_mysql_ifnull.asp)

만약 Column의 값이 NULL일때 다른 데이터로 치환하고 싶다면 `IFNULL()` 을 사용할 수 있다.
```
SELECT IFNULL(Column명, "Null일 경우 대체 값") FROM 테이블명; 
```

>프로그래머스 SELECT 문제 
>> 12세 이하의 환자목록 출력
>> [프로그래머스 SELECT 문제 12세 이하의 환자목록 출력](https://school.programmers.co.kr/learn/courses/30/lessons/132201)
```SQL
-- 코드를 입력하세요
SELECT 
    PT_NAME, PT_NO, GEND_CD, AGE, IFNULL(TLNO, "NONE") AS TLNO
FROM 
    PATIENT

WHERE AGE <= 12 && GEND_CD ='W'
ORDER BY AGE DESC, PT_NAME ASC
```

## ORACLE
- IFNULL 과 비슷한 함수로 `NVL` 함수가 있다. [참고](https://www.techonthenet.com/oracle/functions/nvl.php)