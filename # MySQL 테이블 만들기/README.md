# MySQL 테이블 만들기

이제 우리는 표에서 Column(Table 상의 열) 을 만들어 볼것이다.

```
create table topic(

Id int(11) not null auto_increment,

(;없이 엔터를 치면 명령어가 실행되는게 아니라 줄을 내린다.)
```

위 예제는 topic 테이블의 1번쨰 Id Column을 만드는 예제이다 내용을 보면.

create table TableName 이 create table 이라는 명령과 만들고자 하는 "테이블 이름" 을 기입하고

column의 이름을 기입한다(이 경우엔 Id) 그리고 데이터 타입을 기입한 후 () 안에 테이블에 나타나는 

데이터를 얼마까지 노출시킬 것인가를 적어준다(에를 들어 11이라는 것은 하나의 셀 당 1234567891011 까지 나타낸다).

"not null" 이라는 명령어는 이 Column 의 값이 없음을 허용하지 않는다는 뜻이며

Auto_increment 이란 이 추가되었을시 이 Column 의 값에 1을 더한다는 뜻이다.  


이젠 Id 옆에 다른 행을 넣어 표를 Column을 완성시켜 보자.

1. 2번째는 "Title" 이라는 Column으로 데이터 타입은 문자이고 데이터표시는 100까지 표시한다.

2. 3번째는 "Description" 은 데이터타입은 문자이고 이것은 본문이다.

3. 4번쨰는 "Created" 이고 데이터타입은 날짜이다.

4. 5번째는 "Author" 이고 데이터타입은 문자이며 데이터표시는 30자 까지 표시한다.

5. 6번쨰는 "profile" 이고 문자의 형태이고 익명이 있을수 있 데이터를 100까지 담을수 있다.


위 조건을 만족시키는 Column의 로직을 보면 이러할 것이다.

```
create table Topic( 

Id int(11) not null auto_increment,

Title varchar(100) not null,

Description text null,

Created datetime not null,

Author varchar(100) null,

Profile varchar(30) null,

primary key(Id));

```

그리고 예문외의 것을보은 primary key(id) 이다. primary key(id) 뜻은 이 Table에 Column중 가장 

메인 이 되는 것은 (id) 이다라고 밝히는 것이다.

이 primary key 는 성능적인 면과 중복을 제거하는 면의 기능을 가질수 있는데 지금 우리가 알아야 할것은 

중복을 제거하는 면이다 만약 primary key 에서 같은 문자,숫자를 가진 데이터가 복수적으로 존재하지 못하도록 

방지 하는것이다.




SQL과 엑셀의 차이점 중 하나는 엑셀은 Table안의 데이터를 숫자,문자 등 데이터타입의 영향을 받지 않지만

SQL은 그 Column 에 들어갈 데이터타입 및 표시될 데이터의 양을 강제해야하고 할수있다.  



## 키워드

Column : Table 상의 행을 뜻한다.

not null : 해당 Column 에는 값이 무조건 있어야 한다는 명령이다.(공백이 없어야 한다 null은 가)

int : 정수를 표현하는 데이터 타입이다.

varchar : varchar 는 문자 데이터타입으로 약 255개 문자를 담을수 있다. 

text : 약 65000개의 문자를 담을수 있는 데이터타입이다.

datatime : 1000-01-01 00:00:00 부터 9999-12-31 23:59:59 까지 표현하는 날짜와 시간 데이터타입.

primary key() : 생성하고자하는 table 에 가장 중요한 Colume 을 ()안에 지정해준다.

## 참고

[생활코딩](https://opentutorials.org/course/3161/19542)
