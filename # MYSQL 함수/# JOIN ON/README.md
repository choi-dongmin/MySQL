# JOIN ON 

- RDBMS의 주요한 기능 중 하나로 서로 다른 테이블의 관계형 데이터를 통해 하나의 테이블처럼 활용 출력하는것.

- SELECT C1 FROM T1 JOIN T2 ON T1.C1 = T2.C1

> 프로그래머스 문제
>> [과일로 만든 아이스크림 고르기
](https://school.programmers.co.kr/learn/courses/30/lessons/133025)
```
SELECT
    FIRST_HALF.FLAVOR
FROM 
    FIRST_HALF 
JOIN  ICECREAM_INFO ON FIRST_HALF.FLAVOR = ICECREAM_INFO.FLAVOR
WHERE TOTAL_ORDER > 3000 && ICECREAM_INFO.INGREDIENT_TYPE = 'fruit_based'
ORDER BY TOTAL_ORDER DESC
```