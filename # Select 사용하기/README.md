# Select 사용하기

앞서 CRUD 를 설명하면서 다루었던 Select, from, where 외에 많은 문법을 알아보자. 

## Select 
```
select id, title, description, author_id from topic;


* 결과값
+----+-------------+-------------------+-----------+
| id | title       | description       | author_id |
+----+-------------+-------------------+-----------+
|  1 | My SQL      | My SQl...         |         1 |
|  2 | Oracle      | Oracle is...      |         1 |
|  3 | SQL Server  | SQL Server is...  |         2 |
|  4 | Postgre SQL | Postgre SQL is... |         3 |
|  5 | MongoDB     | MongoDB is...     |         1 |
+----+-------------+-------------------+-----------+

```

위와 같이 입력해주면 topic 의 5가지 column(id, title, description, author_id) 을 불러올수 있다.

selct ~ 은 스키마의 Column 중 원하는 것을 골라 표시할수 있도록 만들어 주는 역할을 한다 (* 을 사용시 전체선택.)


## From

From 은 항상 Select 과 함께 쓰인다 Select 혹은 From 을 개인적으로 하나만 쓴다면 MySQL은 이 쿼리에 예외가 발생한다.

From은 Select 을 실행할시 어느 Table 에서 그 Column 들을 가져올 것인가 에대한 이야기.

그렇기 때문에 Select ~ from ~ 과 같이 이루어져야 한다. 



## Where 

Where 은 마치 조건문과 같다.

```
select id, title, description, author_id from topic where author_id = 1;
``` 

이렇게 입력한다면 결과값에 author_id = 1 과 정확히 같은 조건을 충족시키는 결과만 출력된다.

```
+----+---------+---------------+-----------+
| id | title   | description   | author_id |
+----+---------+---------------+-----------+
|  1 | My SQL  | My SQl...     |         1 |
|  2 | Oracle  | Oracle is...  |         1 |
|  5 | MongoDB | MongoDB is... |         1 |
+----+---------+---------------+-----------+
```

## Like

Like 는 마치 Where 과 비슷하지만 다르다.
```
select id, title, description, author_id from topic where author_id like "1";
```
위와 같은 코드로 입력하면 정확하게 

```
+----+---------+---------------+-----------+
| id | title   | description   | author_id |
+----+---------+---------------+-----------+
|  1 | My SQL  | My SQl...     |         1 |
|  2 | Oracle  | Oracle is...  |         1 |
|  5 | MongoDB | MongoDB is... |         1 |
+----+---------+---------------+-----------+
```
위와 일치하는 Table이 출력된다 그럼 Where 과 무엇이 다른가?

바로 Like 그 데이터 안에 포함되어있는 String 을 구별해주는것이다.
```
+---------------+----------------------------------------------+
| Quarry        | Meaning                                      |
+---------------+----------------------------------------------+
| (문자열)%     | (문자열) 로 시작하는 모든 데이터              |
| %(문자열)%    | (문자열) 을 포함한 모든 데이터               |
| %(문자열)     | (문자열) 로 끝나는 모든 데이터                |
+---------------+----------------------------------------------+
```

```
 select id, title, description, author_id from topic where description = "%is...";
```
위와 같은 코드를 입력한다면.

```
+----+-------------+-------------------+-----------+
| id | title       | description       | author_id |
+----+-------------+-------------------+-----------+
|  2 | Oracle      | Oracle is...      |         1 |
|  3 | SQL Server  | SQL Server is...  |         2 |
|  4 | Postgre SQL | Postgre SQL is... |         3 |
|  5 | MongoDB     | MongoDB is...     |         1 |
+----+-------------+-------------------+-----------+
```
위 처럼 출력 될 것이다 왜냐하면 description중 "is..." 으로 끝나는 것들을 불러왔기 때문이다.


## And/Or/Not

위 세가지의 다 where ~ and/or/not 과 같은 방식으로 실행한다.

1. where ~ A and ~ B : and 는 A,B 를 모두 만족을 시킬때 출력한다.

2. where ~ A or ~ B : or 은 A 또는 B 일 때 출력한다.

3. where ~ not A : not 은 부정으로 A 가 아닐때  

(위에서 ~ 은 Column 이다.)

```
select id, title, description, author_id from topic where not author_id = "1" or author_id= "2";

* 결과값
+----+-------------+-------------------+-----------+
| id | title       | description       | author_id |
+----+-------------+-------------------+-----------+
|  3 | SQL Server  | SQL Server is...  |         2 |
|  4 | Postgre SQL | Postgre SQL is... |         3 |
+----+-------------+-------------------+-----------+
```

## In/Between

In/between 는 And 와 Or 를 좀 더 간단하게 나타낼수 있다.

1. between : where ~ between A and B 로 나타내는데 A 와 B 사이에 숫자를 출력해 준다. 

```
select id, title, description, author_id from topic where id between 1 and 4;

* 결과값
+----+-------------+-------------------+-----------+
| id | title       | description       | author_id |
+----+-------------+-------------------+-----------+
|  1 | My SQL      | My SQl...         |         1 |
|  2 | Oracle      | Oracle is...      |         1 |
|  3 | SQL Server  | SQL Server is...  |         2 |
|  4 | Postgre SQL | Postgre SQL is... |         3 |
+----+-------------+-------------------+-----------+
```

2. in : where ~ in (A, B) 로 나태낸다 (A,B) 둘중 하나라도 있는 것을 출력한다. 
```
select id, title, description, author_id from topic where author_id in(1,2);

*결과값
+----+------------+------------------+-----------+
| id | title      | description      | author_id |
+----+------------+------------------+-----------+
|  1 | My SQL     | My SQl...        |         1 |
|  2 | Oracle     | Oracle is...     |         1 |
|  3 | SQL Server | SQL Server is... |         2 |
|  5 | MongoDB    | MongoDB is...    |         1 |
+----+------------+------------------+-----------+
```

## Limit

Limit 은 항상 끝에 위치한다. 테이블에서 최대 몇개의 데이터를 표시할것인가 나타낸다.
```
select id, title, description, author_id from topic limit 3; 

* 결과값
+----+------------+------------------+-----------+
| id | title      | description      | author_id |
+----+------------+------------------+-----------+
|  1 | My SQL     | My SQl...        |         1 |
|  2 | Oracle     | Oracle is...     |         1 |
|  3 | SQL Server | SQL Server is... |         2 |
+----+------------+------------------+-----------+
```
표 위에서 부터 최대 3번째 까지 출력한다는 뜻이고 결과 또한 그렇게 나왔다

(만약 limit 3 뒤에 offset 2를 한다면 위에서 2개 그러니 id 1,2 를 제외한 3,4,5 가 출력된다.)

## Order By

Order By 는 차순을 결정한다. Desc, Asc  이 두가지로 원하는 차순으로 표시를 할 수 있다.

보통은 Limit 바로 앞(없을시 맨 뒤)에 위치한다.

1. Desc : where ~ order by ~ desc 로 실행하고 내림차순으로 정리를 한다는 뜻이다. 

```
select id, title, description, author_id from topic order by id desc limit 3;

* 결과값
+----+-------------+-------------------+-----------+
| id | title       | description       | author_id |
+----+-------------+-------------------+-----------+
|  5 | MongoDB     | MongoDB is...     |         1 |
|  4 | Postgre SQL | Postgre SQL is... |         3 |
|  3 | SQL Server  | SQL Server is...  |         2 |
+----+-------------+-------------------+-----------+

```
id가 내림차순부터 limit 3 으로 잘 출력되었다.

2. Asc : where ~ order by ~ asc 로 실행하고 오름차순으로 정리를 한다는 뜻이다.
```
select id, title, description, author_id from topic order by id asc limit 3;

* 결과값
+----+------------+------------------+-----------+
| id | title      | description      | author_id |
+----+------------+------------------+-----------+
|  1 | My SQL     | My SQl...        |         1 |
|  2 | Oracle     | Oracle is...     |         1 |
|  3 | SQL Server | SQL Server is... |         2 |
+----+------------+------------------+-----------+

```
위 또한 id 가 오름차순부터 limit 3 으로 잘 출력되었다.


## 키워드

select : 어떠한 table 원하는 Colume 을 불러오려 입력하는 문법이다.

from : select ~ from ~ 과 같이 써지며 어떠한 테이블을 불러올 것인지에 대한 문법이다.

where : select ~ from ~ where ~ 과 같이 쓰며 조건과 데이터가 정확히 일치하는것을 표시한다.

like :  select ~ from ~ where ~ like ~ 로 써지며 데이터중 그 문자열을 포함하는 것을 결과로 도출. 

and/or(not) : where 다음에 오며 각각 A, B 모두를 포함하는, 둘 중 하나를 포함하는 이라고 생각하면 되고 where ~ not 을 사용하면 부정문으로 바뀐다.

between : where ~ between A and B 이고 둘 사이에 값 모두를 출력한다.(And 를 좀 더 효율성 있게!)

in : where ~ in (A,B) : A,B 둘 중에 하나라도 포함된 것이 있다면 출력. (Or 을 좀 더 효율성 있게!)

Limit : 항상 끝에 위치하고 테이블에서 최대 몇개의 데이터를 표시할것인가 나타낸다.

order by desc/asc : 오름내림 차순을 설정하는 문법이.

## 참고
[Daikoku 블로그](https://blog.naver.com/jjys9047/221561557182)

