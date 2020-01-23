# SQL의 CRUD (Update, Delete)

## Update

만약 우리가 만들어낸 DB안에 Colume 의 내용 중 고치고 싶은 것이 있다면 Updata 를 통하여 내용을 바꿀수 있다.
```
+----+------------+------------------+---------------------+--------+--------------------------+
| Id | Title      | Description      | Created             | Author | Profile                  |
+----+------------+------------------+---------------------+--------+--------------------------+
|  1 | MySQL      | MySQL is...      | 2020-01-21 18:35:43 | ME     | Developer                |
|  2 | Oracle     | Oracle is...     | 2020-01-21 19:12:54 | me     | Developer                |
|  3 | SQL Server | SQL Server is... | 2020-01-21 19:17:47 | Dura   | Database Administrator   |
|  4 | PostgreSQL | PostgreSQL       | 2020-01-21 19:20:12 | Teaho  | Data Scintist, Developer |
|  5 | MongoDB    | MongoDB is...    | 2020-01-21 19:21:33 | me     | Developer                |
+----+------------+------------------+---------------------+--------+--------------------------+
```

위의 내용은 우리가 저번에 만들어 보았던 Topic Table 이다 저곳에서 고쳐야할 부분을 찾아보자, Id 1에 Author을 보면 ME를 me로 고쳐주고 싶다.

그렇다면 우리는 "update TableName set ColumnName='새로 넣고싶은 문장' where primary key=00" 으로 바꾸줄수 있다.

* (Where 뒤에 오는 문장을 작성하지 않으면 해당 Cloumn 들이 모두 바뀐다.)

그것을 위의 예제에 적용 시켜 문법을 작성해 보면

```
update Topic set Author='me' where Id=1;
```

위의 문법으로 Id 1번의 Author의 Me를 me로 고칠수 있다. 

다시한번 더 바꾸어 보도록 하자 이번엔 Id 4번째의 Description 의 PostgreSQL 을 Postgre SQL... 으로 바꿔보자.


```
update Topic set Description='Postgre SQL...' where Id=4;
```

위와 같은 내용을 SQL에 입력한다면 4번째의 Description 의 PostgreSQL 을 Postgre SQL... 으로의 바꿀수가 있다.


## Delete

이번엔는 수정이 아닌 삭제를 배워보자 CRUD중 가장 마지막인 'Delete' 이다.
```
+----+------------+------------------+---------------------+--------+--------------------------+
| Id | Title      | Description      | Created             | Author | Profile                  |
+----+------------+------------------+---------------------+--------+--------------------------+
|  1 | MySQL      | MySQL is...      | 2020-01-21 18:35:43 | me     | Developer                |
|  2 | Oracle     | Oracle is...     | 2020-01-21 19:12:54 | me     | Developer                |
|  3 | SQL Server | SQL Server is... | 2020-01-21 19:17:47 | Dura   | Database Administrator   |
|  4 | PostgreSQL | Postare SQL...   | 2020-01-21 19:20:12 | Teaho  | Data Scintist, Developer |
|  5 | MongoDB    | MongoDB is...    | 2020-01-21 19:21:33 | me     | Developer                |
+----+------------+------------------+---------------------+--------+--------------------------+
```
이전에서 수정까지 마친 Topic DB 이다. 여기서 우리는 Id 5번째 MongoDB를 삭제해볼 것이다.

삭제 하는 문법은 "Delete From TableName where Primary key = 00;" 으로 삭제할수 있다 그럼  Topic Table 에서 적용해보자.

* 이곳 또한 Where 뒤에 구문을 쓰지 않을시 해당 테이블이 통째로 사라지는 상황을 만들어 낸다. 

```
delete from Topic where Id=5;
``` 

이렇게 Delete 값을 적용하고 난 후의 Topic 테이블을 보면 (Select * from Topic)

```
+----+------------+------------------+---------------------+--------+--------------------------+
| Id | Title      | Description      | Created             | Author | Profile                  |
+----+------------+------------------+---------------------+--------+--------------------------+
|  1 | MySQL      | MySQL is...      | 2020-01-21 18:35:43 | me     | Developer                |
|  2 | Oracle     | Oracle is...     | 2020-01-21 19:12:54 | me     | Developer                |
|  3 | SQL Server | SQL Server is... | 2020-01-21 19:17:47 | Dura   | Database Administrator   |
|  4 | PostgreSQL | Postare SQL...   | 2020-01-21 19:20:12 | Teaho  | Data Scintist, Developer |
+----+------------+------------------+---------------------+--------+--------------------------+
```
이런식으로 5번쨰 Id가 사라진것을 볼수가 있다.


## 키워드

CRUD : Create, Read, Update, Delete



Updata : 기존에 있던 Column 을 선택하여 내가 원하는 새로운 정보로 대체하여 수정하는것. 문법적으로는 

"update TableName set ColumnName='새로 넣고싶은 문장' where primary key=00" 으로 사용된다.

단, where 구문을 작성하지 않으면 모든 해당 Column의 내용이 수정이 되니 항상 조심해야 한다.



Delete : 기존에 있던 DB 혹은 Column 을 선택해 그것을 완전히 삭제시키는 명령이다 

"Delete From TableName where Primary key = 00;" 으로 실행한다

단, Where 구문을 작성하지 않으면 해당 Table 이 통쨰로 사라지기 때문에 각별히 주의해야한다.



Select * From (TableName) : (TableName) 그안에 작성한 Table을 선택하여 모든Column(*)
을 출력하도록 하는 명령

단, 모든 Column 이 아닌 보고 싶은 부분이 있다면 * 대신 해당 ColumnName을 입력한다.(복수가능)

## 참고

[생활코딩](https://opentutorials.org/course/3161/19542)



