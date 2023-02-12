# GROUP BY / HAVING

- GROUP BY의 기능
> 집계 함수(Aggregate funtion)와 함께 사용을 위해 그룹화 한다.
> 집계 함수 사용시 중복된 데이터 값을 합친다.

> 프로그래머스 문제
>> [카테고리 별 상품 개수 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/131529)
```SQL
SELECT
    LEFT(PRODUCT_CODE, 2) AS CATEGORY, COUNT(PRODUCT_ID)
FROM
    PRODUCT 
GROUP BY CATEGORY
```

- HAVING
> 각 그룹에 대한 조건을 기술할 대 사용
> WHERE은 테이블 내의 전체에 대한 제약 조건
