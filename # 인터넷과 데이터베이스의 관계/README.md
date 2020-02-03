# 인터넷과 데이터베이스의 관계

정보의 바다와 같은 인터넷과 SQL 융합적으로 동작하면 굉장한 효과를 얻을수 있다.

## Dtaabase Server 

우리는 Database Server 안에는 많은 Database 가 존재할 수 있고 그 Database 안에는 많은 Table이 존재할 수 있다는것을 알고 있다. 

그렇다면 이 가장 거시적인 Database Server 는 무엇인가? 우리가 주목해야 할 단어는 바로 'Server' 이다.

우리는 인터넷 이라는 것을 통해 단순히 컴퓨터 1대만으로 이룰수 없는 것들을 해내고 있다. 

예를 들자면 우리가 구글 웹을 주소창에 요청하면 우린 우리가 가진 컴퓨터에 있는 정보가 아닌 구글이 가진 서버에 요청을 하여 그 정보를 받는다.

(이 떄 우리가 요청을 함으로 'Client' 가 되는것 이고 서비스를 제공하는 곳이 바로 'Server' 가 된다.)

다시 DB로 돌아와서 우리가 MySQL 을 설치할때 2가지의 프로그램을 다운받는데 하나는 DB Client 또 하나는 바로 DB Server 이다.

DB Server 에는 실제로 데이터들이 저장되고 존재하며 DB Client 를 통해서 DB Server 에 접속 할 수있다.

(DB Server 는 DB Client 를 통해서만 들어갈수 있다. 우리가 처음 MySQL에 접속할때 ./mysql -uroot 를 통해 MySQL monitor 로 들어가게 된다.

이 MySQL monitor 는 MySQL DatabaseServer에 들어갈 수 있는 하나의 기본 Client 로 개발자들이 제공하는 것이다.)

이렇게 된다면 하나의 Database Server 에 수많은 사람들이 데이터를 저장을 하고 또 사용이 가능하게 된것이다.

다시 말하자면 전세계의 사람이 하나의 Data Server를 같고 서로 공유하는것이 가능한 것이다.


## Client

MySQL 에는 여러 Client 들이 있다 

1. MySQL monitor

MySQL monitor 의 장점은 MySQL을 설치하면 기본으로 설치된다는 점, 그렇기 떄문에 MySQL Server 가 있는곳에 MySQL monitor 가 있다 그 말은 어디서나 사용이 가능하며

명령어 기반의 프로그램이다(Not GUI : 마우스로 작동하는 것) 그렇기 떄문에 그 컴퓨터의 성능을 최대한으로 필요한 곳에서는 이 명령이 기반으로 작업을 한다.

단점 명령어 기반이기 때문에 그 명령어를 알아야 한다는 것이다.


2. MySQL Workbench

Workbench 는 GUI 기반이기 때문에 가시성이 좋고 인터페이스가 보다 편하다 하지만 명령어 기반이 아니기 때문에 monitor 와 정반대의 단점을 지니고 있다. 



## 키워드

Database Server : 데이터베이스 서버는 실질적으로 데이터들이 저장되는 곳으로써 오직 Client 를 통해서만 접속이 가능하며 이 곳에서 데이터를 저장 / 공유 한다.

Database Client : 데이터를 작성하고 데이터서버에 접근하기 위한 프로그램.

## 참고

[생활코](https://opentutorials.org/course/3161/19547)
