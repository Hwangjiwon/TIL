MultiCampus Study!!
===================


**[ 인프라구축강의 1일차 ]**  

----------


기술의 발전
-------------

기술이 발전하는 이유는 ? **개발자 편의성** 때문.. (사용자 편의성 X)

## 1.  프로그램 기법
	- 	50’s 절차중심적 기법
	- 	6,70’s 정보공학 기법 - DBMS
	- 	80’s 객체지향적 기법 – Smalltalk
	- 	90’s 객체지향 기법 – JAVA
	- 	컴포넌트기반 기법 – CBD (Component Based Development)  
  > **컴포넌트 vs Framework**
  > - 컴포넌트 : 기능 관련. 독립적인 단위 모듈
  > - Framework:  구조적인 것 관련. 대신해주는 것

<hr>

##  2. 구조적 측면  
  - MainFrame 시대 - 중앙 집중적, 일체형  
  - Desktop 시대 - 독립적  
  - Network 시대 - 이전의 사이즈 문제 해결 위한 (CS 시대)  
  - Web Site 시대 - Protocol: http, ftp..., 정적인 처리만 가능    

> **왜 Http가 대세가 되었나**
>  - 개발이 편하다. txt기반
>  - 표준화된 웹서버, 표준화된 클라이언트
>  - Connection Reset State 요청 이후 응답 하면 바로 연결 끊음


  - 동적 처리를 위한 웹서버랑 독립되지 않은 연결된 CGI(Component Gateway Interface)  
    -- But, request가 여러개 들어와도 하나만 처리 가능. 요청마다 process생성하기 때문에 자원(메모리) 공유가 안됨.      
  - Process : 자원을 공유하지 않은 실행중인 프로그램
  - Thread : 자원(정보,code)을 공유하는 실행 흐름  ex) 네스케이프사의 NS API, MS사의 IS API Thread 기반 CGI
  - 플랫폼 종속성(Platform Dependent) ex) 네스케이프의 NS
  - 플랫폼 독립성 + Thread 기능의 장점이 합쳐진 SUN의 JAVA -> Servelt

<hr>

##  3. Architecture
   html,css,js / CGI / Window탐색기 / ...  
   Servelt = Server + Application : 요청분석 -> 비즈니스 수행(처리) -> 응답  // Thread로 동작하고, 플랫폼 독립성  
   Model : Business Component // Servelt의 비즈니스 수행(DB접근...)을 분리해서 처리  
  == == == == == == == == == == == == == == == == == == == ==  
   Java EE(Enterprise Edition) : ee.jar 컴파일  +  Web Container : 서포트해주는 인터페이스를 구현 한 코드 집합(ex. Tomcat, Resin, JRun...)  
   Java SE(Standard Edition) : JRE (JVM + RunTime.jar...)  
  == == == == == == == == == == == == == == == == == == == ==  
   Any Web Server (ex. Apache, Nginx, IIS, NS...) -> http Listener : http이해하는 프로그램. 따라서 요청을 이해할 수 있음    
   Any O/S  
   Any H/W  
   
   
   
   
 
 <hr>
  
 
   
**[ 인프라구축강의 2일차 ]**  

----------


Enterprise Web Architecure
-------------

Software Architecure는 소프트웨어 구성요소들 사이에서 관계표현. 설계와 업그레이드를 통제하는 지침과 원칙


## 1. Client - Server Pattern  
다수의 Client, 하나의 Server.

> **로드벨런싱**  
> 수평적인 확장이 가능하게끔 만들어주는 것.  
> 들어오는 요청을 서버 중 하나로 라우팅 처리해주며, 클라이언트로 응답.  
> 즉, 서버의 과부하를 막아주기 위해 요청을 분산시키는 일  



