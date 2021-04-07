# 관계형 데이터베이스

## 관계형 데이터베이스의 필요성

관계형 데이터베이스의 필요성에 대하여 말해보자 우선 보기 편하도록 Topic Table 을 보고 이야기 해보자

```
+----+------------+------------------+---------------------+--------+--------------------------+
|  1 | MySQL      | MySQL is...      | 2020-01-21 18:35:43 | me     | Developer                |
|  2 | Oracle     | Oracle is...     | 2020-01-21 19:12:54 | me     | Developer                |
|  3 | SQL Server | SQL Server is... | 2020-01-21 19:17:47 | Dura   | Database Administrator   |
|  4 | PostgreSQL | Postare SQL...   | 2020-01-21 19:20:12 | Teaho  | Data Scintist, Developer |
|  5 | MongoDB    | MongoDB is...    | 2020-01-21 19:21:33 | me     | Developer                |
+----+------------+------------------+---------------------+--------+--------------------------+

```

위과 같은 표가 있고 이 표에는 중복되는 것이 있다 바로 Author 와 Profile 을 보면 me, Developer 가 반복되고 있다.

반복된다는 것은 개선해야 한다는 뜻이다 위에 경우에는 데이터의 행이 5가지 밖에 없지만 데이터베이스는 억 단위의 데이터를 담을수 있는것을 생각하자.

그리고 그 중복된 것들이 쓸데없이 너무 많은 데이터를 차지한다 그리고 그 중복된 것들을 수정을 할때 굉장히 힘들다.


## 관계형 데이터베이스의 중복제거

우리는 이 중복을 조금 더 효율적으로 바꿔보자. 만약 Author, Profile 을 표현해주는 Id 값을 표로 따로 만들어 준다면 효율적일것이다 그 말은 Id Table, Topic Table 을 만들어보자.

### 테이블 나누기


```
+----+------------+------------------+---------------------+--------+--------------------------+
|  1 | MySQL      | MySQL is...      | 2020-01-21 18:35:43 | me     | Developer                |
|  2 | Oracle     | Oracle is...     | 2020-01-21 19:12:54 | me     | Developer                |
|  3 | SQL Server | SQL Server is... | 2020-01-21 19:17:47 | Dura   | Database Administrator   |
|  4 | PostgreSQL | Postare SQL...   | 2020-01-21 19:20:12 | Teaho  | Data Scintist, Developer |
|  5 | MongoDB    | MongoDB is...    | 2020-01-21 19:21:33 | me     | Developer                |
+----+------------+------------------+---------------------+--------+--------------------------+

```

위에서 말한것 같이 데이터 중 Author, Profile 을 떼어내어 Author Table, 남은 데이터들로 Topic 테이블을 만들면


topic(Posting category : 사용자가 입력한 데이터)
```
+----+-------------+-------------------+---------------------+-----------+
| id | title       | description       | created             | author_id |
+----+-------------+-------------------+---------------------+-----------+
|  1 | My SQL      | My SQl...         | 2020-01-28 21:22:06 |         1 |
|  2 | Oracle      | Oracle is...      | 2020-01-28 21:25:44 |         1 |
|  3 | SQL Server  | SQL Server is...  | 2020-01-28 21:26:21 |         2 |
|  4 | Postgre SQL | Postgre SQL is... | 2020-01-28 21:27:25 |         3 |
|  5 | MongoDB     | MongoDB is...     | 2020-01-28 21:29:48 |         1 |
+----+-------------+-------------------+---------------------+-----------+
```

author (personal info category : 사용자의 개인정보 데이터)
```
+----+-------+--------------------------+
| id | name  | profile                  |
+----+-------+--------------------------+
|  1 | Me    | Developer                |
|  2 | Dura  | Database Administrator   |
|  3 | Teaho | Data Scintist, Developer |
+----+-------+--------------------------+
```

이렇게 만들수 있다 topic Talbe 에 author_id 를 만들어 author 테이블과 유기적으로 '관계' 하며 효율적이게 만든다.


### join

이제 우리는 각각 독립되게 만든 이 Table 을 'join' 함으로 가독성이 떨어지던 단점을 보완해 보자, 이 부분이 관계형 데이터의 꽃이라고 볼수도 있다.

그럼 한번 해보자 우리는 MySQL에게 topic 에 있는 author_id 의 값과 author 의 id 값이 일치하면 topic 테이블에 author의 값을 붙혀라 라고 하고싶다.


```
select * from topic left join author on topic.author_id = author.id;
```
select * from topic / left join author / on topic.author_id = author.id;

위 코드를 하나하나 뜻어보자.

slect * from topic : topic Table 을 전부 불러오고 

join author : join 시켜라 author 를 (left는 아직 신경쓰지 말자)

on topic.author_id = author.id : topic 의 author_id 와 author 의 id 값이 동일한 author 의 데이터를 join

위와 같은 코드를 실행 시킨다면 아래와 같은 결과 값이 도출 될것이다.

```
+----+-------------+-------------------+---------------------+-----------+------+-------+--------------------------+
| id | title       | description       | created             | author_id | id   | name  | profile                  |
+----+-------------+-------------------+---------------------+-----------+------+-------+--------------------------+
|  1 | My SQL      | My SQl...         | 2020-01-28 21:22:06 |         1 |    1 | Me    | Developer                |
|  2 | Oracle      | Oracle is...      | 2020-01-28 21:25:44 |         1 |    1 | Me    | Developer                |
|  3 | SQL Server  | SQL Server is...  | 2020-01-28 21:26:21 |         2 |    2 | Dura  | Database Administrator   |
|  4 | Postgre SQL | Postgre SQL is... | 2020-01-28 21:27:25 |         3 |    3 | Teaho | Data Scintist, Developer |
|  5 | MongoDB     | MongoDB is...     | 2020-01-28 21:29:48 |         1 |    1 | Me    | Developer                |
+----+-------------+-------------------+---------------------+-----------+------+-------+--------------------------+
```

만약 위의 코드에서 author_id, author에 id 값을 보기 싫다면 우리가 알고 있는 select *를 이용하자

```
select id, title, description, created, name, profile from topic left join author on topic.author_id = author.id;
```

하지만 위와같은 코드를 실행하려하면 id 의 값이 불확실해 오류가 발생한다 그럴땐 우리가 직접 어떤 id 인지를 명령해주자 (topic.id)

```
select topic.id, title, description, created, name, profile from topic left join author on topic.author_id = author.id;
```

그리고 그 id 가 어떤 id 인지 표시해주고 싶다면 topic.id 뒤에 "as topic_id" 라고 적는다면 id 의 columnName 은 topic_id 로 바뀔것이다.

위 의 Join 은 매우매우 중요한 기술이다. 테이블을 나누어서 중복을 제거한다는 것은 그 테이블 간 관계와 개수가 증가하면 효율성은 매우매우 증가한다.


즉, 관계형 데이터베이스는 데이터가 많아짐에 따라 조금 더 효율적이게 운영하기 위해 테이블을 카테고리에 따라 나누고 MySQL 에서 join 과 같은 함수로 사용해 출력하는것을 말한다.

서로 다른 테이블들이 상호호환하는 데이터를 기준으로 하나의 데이터로 나타낼수 있는것이 "관계형 데이터"이다 (*상호호환하는 관계의 데이터가 있어야 한다.)  

## 키워드

데이터베이스의 장점 : 복수의 Table 을 마치 1개의 Table 처럼 연결하여 하여 스프레드 시트에서의 중복을 해결하고 그에 따라 가독성이 떨어지는 단점 해결할수 있다.  

join : 각각 독립된 두 Table 을 하나의 Table 처럼 접목시켜 중복을 제거함과 그에 따라 발생하는 단점인 낮아 가독성을 높이는것. 

select * from 00 : 선택된 테이블의 모든 데이터를 불러온다는 뜻이다. (선택한 데이터만 가지고 오고 싶으면 * 대신 columnName 을 넣는다.)

## 참고
[생활코딩](https://opentutorials.org/course/3161/19545)

