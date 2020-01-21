# MySQL의 CRUD

## CRUD란??

Create Read Update Delete 의 약자이다. 생성하고 읽고 수정하고 삭제하는것, 다시 말해 기본적인 DB 를 이용하는데 필요한 기술이다.

하지만 모든 DB에서 사용하는것은 앞에오는 CR 이고 UD는 어떤곳에선 필요하고 어떤곳에선 불필요 할수 있다.


## Insert (삽입하다)

Insert는 기존에 있던 Table에 Row 를 새로 추가하는것이다.

사용할 DB에 들어가서 원하는 Table에 Row를 삽입해보자.(show tables; 로 검색하면 현재 DB의 table을 보여준다.)

필자 같은경우엔 저번에 만들어 놓았던 Topic에 새로운 열(Row)을 넣겠다.(만약 table의 Column이 궁금하다면 desc tablename; 으로 볼수있다.)

```
insert into Topic (Title,Description,Created,Author,Profile)values('MySQL','MySQL is...',now(),'ME','Developer');
``` 

위의 로직을 보자 처음 "insert into Topic", 내가 가진 Table(Topic)에 열을 삽입한다 라는 명령이고 그 뒤 ()에 우리는 정보를 넣어야 한다.

(Column1, Column2, Column3 ...) Values (Column data 1, Column data 2, Column data 3...)

이런식으로 각각의 Column 과 Values() 에 그 각 Column 의 내용 써주어 삽입시킨다. 

(Id 같은 경우엔 지정을 하지 않는다면 1씩 늘어나도록 설정해 놓았고 Created Values 같은 경우엔 함수 now()를 써주었다.)


## Read (읽다)

이제 우리는 1줄의 Column과 1줄의 Row를 만들었다 어떻게 우리가 만든 Table을 볼수가 있을까?

1. Select

```
select * from Topic;
``` 

select * from Topic; 을 보자 알다 싶이 Topic; 은 Table의 이름이니 굳이 덧붙혀 설명을 안하겠다.

select * from 이 로직의 뜻을 보자 select(선택한다) *(all) from(~에) Topic;(Table)

내가 선택한 테이블에 선택한 정보를 가지고 오는것으로  select * 을 하면 그 Table의 정보를 모두 가져온다.

만약 우리가 모든 정보가 아닌 내가 선택한 정보만 가질려면 어떻게 해야할까? 답으 간단하다 바로 * 이 있는곳에 Column의 이름을 입력해 주면 된다.

```
select Id,Title,Created,Author from Topic;
``` 

이러면 원하는 정보만 뽑아 볼수 있다.


2. Where 

그럼 우리는 더 나아가 더 많은 문법을 접해보자 만약 우리가 Author의 값이 me인 것만 보고 싶다면?

```
select Id,Title,Created,Author from Topic where Author = 'me';
```

우리는 Topic 끝에 where Author = 'me'; 로 Author의 값이 me 인 것을 출력할수 있었다.

다시말해 Where (CoulumeName) = '(찾으려는 정보)' 를 입력하면 같은 내용을 선별할수 있다. 

```
* 그러나 반듯이 문법구조에 맞게 위치하여야 한다. where 가 From 보다 앞에 오면 오류가 발생할 것이다.
```


3. Order by desc

또 다른 문법으로 우리가 만약 Id 를 큰 숫자부터 내림차순 하고싶다면 어떨까?

```
select Id,Title,Created,Author from Topic where Author = 'me' order by Id desc;
```

order by Id desc; 은 where보다 뒤에 나오며 그 데이터값이 숫자일때 더 큰 숫자부터 내려오도록 하는것 이다.


4. Limit

스프레드시트와 다르게 DB는 굉장히 많은 데이터를 담을수 있음으로 억 단위의 데이터가 우리한테 있다고 가정 했을시 

만약 우리가 선행해서 본 select * from Topic; 을 해버린다면 컴퓨터는 과부하가 걸릴것이 분명하다 

그래서 우리는 Limit 를 통해 우리가 명령을 내렸을시 보여지게될 데이터의 최대값을 정해줄수 있다.

```
select Id,Title,Created,Author from Topic where Author = 'me' order by Id desc limit 2;
```

이러면 Table 상에 저 문법조건에 맞는 데이터들 중 2개가 나올것이다 (여기선 Author = me 중에 Id 값이 큰것부터 내림차순 한 5,2 가 나온다.)


사실 가장 중요한 부분이 바로이 Read 부분 (Select)이다. 데이터베이스를 잘 이용한다라고 할수있는 

많은 부분들이 있지만 이 Select 을 잘 이용하는것이 가장 DB를 잘 이용한다의 적합한 뜻이다.  

이말은 끝임없는 검색과 탐구로 인해 내가 필요한 것을 갖추어야 한다. 


## 키워드

CRUD : Create Read Update Delete 로 기본적인 DB를 사용하는데 필요한 기술.  

Row : 열을 뜻한다.

insert into (TableName) : Table 에 열을 추가함으로 정보를 기입할수 있게 하는 명령어 

select (*,Colunm) from (TableName) : 내가 선택한 Table 에 선택한 Colume의 포함된 Row 를 가지고 오는것

Where (CoulumeName) = '(찾으려는 정보)' : Colume에서 내가 찾으려는 정보가 일치하는 Row를 출력하는것. 

order by Id desc : Table에서 내가 선택한 Colume에 값이 숫자이면 내림차순 정렬로 정렬하는것. 

Limit : 표시해야할 데이터 개수중 최대값을 설정하는 문법.
