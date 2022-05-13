## 📅 2022/05/13

<br/>

### 🏹 주간 목표

- [ ] 이력서 지원
- [ ] stock 토이 프로젝트 데이터 파싱하기
- [ ] MySQL 스터디 이번주 분량 학습
- [x] 스프링 원리 학습 및 정리
- [x] queryDSL 학습


<br/>

### 일일 체크리스트(어제 정한 목표)

- [ ] 스프링 학습
- [ ] MySQL 격리레벨 테스트

<br/>

### 💯 오늘 한 일

- CS 공부 (운영체제)
- QueryDSL + Spring Data Mongo

<br/>

### 📈 내일 할 일

- 스프링 학습
- MySQL 격리레벨 테스트

<br/>

### 🧐 간단 회고

- 운영체제 역할
  - 입출력장치, 컴퓨터 자원 관리
  - 응용 프로그램 관리
    - 응용프로그램이 운영체제에게 기능요청을 위해서 운영체제의 시스템 콜이 존재함
    - 시스템 콜을 직접 사용하기 보단, 해당 시스템 콜을 사용해서 만든 각 언어별 라이브러리(API) 를 사용함
  - 사용자 인터페이스를 제공하기 위한 쉘 프로그램 제공
  

- QueryDSL + Spring Data Mongo
  - QueryDSL 의 RepositorySupport 를 사용할 수도 있고 (라이브러리 querydsl-apt)
  - Spring Data Mongo 의 MongoOperations(MongoTemplate 역할) 으로도 쿼리를 사용할 수 있다. (Spring Data JPA 에서는 QueryFactory)
  - RepositorySupport 는 조회를 간단하게 하기에 좋은 방식이고
  - cud 를 하기에는 MongoOperations 를 사용해야겠더라.
  
  
