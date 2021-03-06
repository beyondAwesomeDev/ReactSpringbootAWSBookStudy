









# 인텔리제이로 Spring Initializr 사용하기

![image](https://user-images.githubusercontent.com/85017704/177480488-c7a7b528-081e-44d3-bb3b-e73a9de197b6.png)

책에서 spring initializr 웹사이트를 통해 생성하는데

인텔리제이 안에서도 생성할 수 있다.



![image](https://user-images.githubusercontent.com/85017704/177480749-95cefc7b-cf10-4356-9000-9c91fa50ce06.png)

이렇게 dependncy 추가도 가능하다







# @Component

@Component는 스프링에게 이 클래스를 자바 빈으로 등록시키라고 알려주는 어노테이션.





# 백엔드 서비스 아키텍처

### 레이어드 아키텍처 패턴

![image](https://user-images.githubusercontent.com/85017704/177486047-89752b4d-22f1-4d94-b049-1dbc38bd0b6c.png)

- 스프링 프로젝트 내부에서 어떻게 코드를 적절히 분리하고 관리할 것이냐에 대한 것.
- 코드를 적절히 분리하고 관리하는 것은 코드 베이스가 커질수록 중요.
- 애플리케이션을 구성하는 요소들을 수평으로 나눠 관리하는 것.
- 레이러로 나눈다? 메서드를 클래스 또는 인터페이스로 쪼개는 것
- 레이어 사이에 계층이 있음.
  - 기본적인 레이어드 아키텍처에서는 상위레이어는 자신의 바로 하위 레이어만 사용한다.

### REST 아키텍처 스타일

- 클라이언트가 서비스를 이용하려면 어떤 형식으로 요청을 보내고 응답을 받는지에 대한 것.
- RESTful 서비스 : REST 아키텍처 스타일을 따라 설계 및 구현 된 서비스

# 모델과 엔티티

이 프로젝트에서는 모델과 엔티티를 한 클래스에 구현했다고 함.

따라서 모델은 비즈니스 데이터를 담는 역할과 데이터베이스의 테이블과 스키마를 표현하는 두 역할을 함.

큰 애플리케이션의 경우 모델과 엔티티를 따로 구현하지만 이 프로젝트는 규모가 작어서 합쳐서 구현했다고 함.

> 모델과 엔티티를 따로 구현하는 방식이 궁금하다..  어떻게 활용되는지 감이 안잡힘



# REST API

REST(Representatioinal State Transfer)

아키텍처 스타일(반복되는 아키텍처 디자인)

REST 제약조건

- 클라이언트-서버
- 상태가 없는
- 캐시되는 데이터
- 일관적인 인터페이스
- 레이어 시스템
- 코드-온-디맨드(선택사항)



1. 클라이언트-서버

   리소스(REST API가 리턴할 수 있는 모든것을 의미 ex) HTML, JSON,이미지 등)를 관리하는 서버가 존재하고

   다수의 클라이언트가 리소스를 소비하려고 네트워크를 통해 서버에 접근하는 구조 (ex) 웹애플리케이션 )

2. 상태가 없음

   stateless : 클라이언트가 서버에 요청을 보낼 때 이전 요청의 영향을 받지 않음

3. 캐시되는 데이터

   서버에서 리소스를 리턴할 때 캐시가 가능한지 아닌지 명시할 수 있어야함.

   HTTP에서는 cache-control이라는 헤더에 리소스의 캐시 여부를 명시할 수 있음.

4. 일관적인 인터페이스

   시스템 또는 애플리케이션의 리소스에 접근할 때 인터페이스가 일관적이야함.

   리소스에 접근하는 방식, 요청 형식, 응답 형식 -> 즉 URI, 요청의 형태와 응답의 형태가 애플리케이션 전반에 걸쳐 일관적이어야함.

   ex) 일관적이지 않은 인터페이스 

   - URI 일관성

     - Todo 아이템 가져오기 : http://fsofwareengineer.com/todo

     - Todo 아이템 업데이트: http://fsoftwareengineer2.com/todo

   - 리턴 타입 일관성

     - http://fsofwareengineer.com/todo : JSON 리턴
     - : http://fsofwareengineer.com/account : HTML 리턴

5. 레이어 시스템

   클라이언트가 서버에 요청을 할 때 여러개의 레이어로 된 서버를 거칠 수 있음. 이 사이의 레이어들은 요청과 응답에 어떤 영향을 미치지 않으며 클라이언트는 서버의 레이어 존재 유무를 알지 못함.

6. 코드-온-디맨드(선택사항)

   클라이언트는 서버에 코드를 요청할 수 있고 서버가 리턴한 코들르 실행할 수 있음



REST와 HTTP는 다르다. REST는 HTTP를 이용해 구현하기 쉽고 대부분 그렇게 구현하지만 

엄밀히 말하면 REST는 아키텍처이고 HTTP는 REST아키텍처를 구현할 때 사용하면 쉬운 프로토콜임.





# 직렬화(serialization)

직렬화: 오브젝트를 저자하거나 네트워크를 통해 전달할 수 있도록 변환하는 것

반대의 작업을 역직렬화라고함(deserialization)







---

백엔드로 스프링부트 프론트엔드로 리액트를 활용해 결합하는 과정을 해보고싶어 이책을 선택했는데

저번에 배웠던책이랑 조금씩 차이가 있네.. 어떤 방법을 실무에서 더 많이 쓸까...

여기서는 @AutoWired로 빈생성하는데 

전책에서는 @ RequiredArgsConstructor로 빈생성했음...

@AutoWired 쓰니깐 인텔리제이에서 추천하지않는다고 하이라이트가떴음..

*Field injection is not recommended*

생성자 주입을 사용해야하는 이유 : https://yaboong.github.io/spring/2019/08/29/why-field-injection-is-bad/

이거말고도 저번책에서도 생성자 주입을 추천해줬다.

이 책의 프로젝트를 생성자 주입으로 바꿔서 해봐야겠다.

@RequiredArgsConstructor을 사용해 final 선언된 필드에 생성자 생성





# JPA

JPA는 스펙(Specification): JPA의 구현을 위해서 이런이런 기능을 작성해라고 말해주는 그야말로 지침이 되는 문서

이 스펙이 명시한 대로 동작한다면 그 내부의 구현 세부사항은 구현자의 마음.

JPA란 자바에서 데이터베이스 접근, 저장, 관리에 필요한 스펙

이 스펙을 구현하는 구현자를 JPA Provider라고 부르는데 그 중 대표적인 JPA Provider가 Hibernate임.



그렇다면 스프링 데이터 JPA는 무엇이고 JPA와 어떤 관계인가?

스프링 데이터 JPA는 JPA에 +a라고 생각하면 됨.

JPA를 더 사용하기 쉽게 도와주는 스프링의 프로젝트임 기술적으로는 이를 추상화했다고 함.

추상화했다는 것은 사용하기 쉬운 인터페이스를 제공한다는 것임.

이 프로젝트에서는 그런 인터페이스 중 하나인 JpaRepository를 사용함



# In-Memory 데이터베이스 H2

h2를 디펜던시로 설정하면 @SpringBootApplication 어노테이션의 일부로 스프링이 알아서 H2데이터베이스에 연결해줌





# 로그 어노테이션

@Slf4j 



# Dto의 toEntity 메서드

DTO는 HTTP 응답을 반환할 때 비즈니스 로직을 캡슐화하거나 추가적인 정보를 함께 반환하려고 사용함.

따라서 컨트롤러는 사용자에게서 TodoDTO를 요청 바디로 넘겨받고 이를 TodoEntity로 변환해 저장해야함.

또 TodoService의 create()가 리턴하는 TodoEntity를 TodoDTO로 변환해 리턴해야함.

(레이어 계층)



> 저번해 했던 스프링부트 책에서 toEntity의 용도를 제대로 이해하지 못했는데 이부분을 보고 깨달음!!



