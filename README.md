# borntobeheesoKN

### 개발 필수요건

### 회원관리

- [x] 회원정보,가입/탈퇴,로그인

### 검색관리

- [x] 외부가격비교 : 외부 서비스에 대한 가격정보 서비스
- [x] 내부가격비교 : 내부 서비스에 대한 가격정보 서비스

### 주문관리

- [x] 등록한 상품으로 주문을 받을 수 있어야 한다.
- [x] 주문한건당 여러개의 상품을 받을 수 있다.(1:N)
- [x] 주문은 부분취소가 가능하다.
- [x] 주문 내 일부 상품만 취소할 수 있다.
- [x] 주문상태 예시 : 주문접수/배송완료/주문취소

### 주문 및 취소 시 알림

- [x] 콘솔에 로그 출력을 알림발송으로 인정합니다.

### 개발 추가요건(선택)

- [ ] 인증/인가
- [x] 토큰 기반
- [x] 로그인사용자 관리
- [x] 예외처리
- [ ] 단위테스트
- [x] 활용가능한 기술 추가적용 가능

• 결제서비스
• 배송서비스
• 반품/교환 서비스
• 이력서비스
• 저장
• 조회
• 관리
• 분석서비스 : 구매분석(연령대, 성별, 지역, 시간, 결재액...) 판매분석(판매자, 품목, 수량), 프로모션
분석(규모, 기간), 매출분석 (매출, 이익율)
• 학습서비스 : 구매 이력, 패턴, 금액, segment별 학습, 개별 학습,
• 전처리
• 데이터 이동, 보관

# Tech Stacks

- ### springboot Framework

- ### Postgresql

  - Postgresql은 자체적으로 구축해서 사용중인 홈 서버에 Docker로 올려서 사용했습니다.

- ### Redis(Bull Message Queue)

  - Redis도 Postgresql과 마찬가지로 홈 서버에 Docker를 이용해 사용했습니다.
  - 
### Components

- auth
  - 인증/인가와 관련된 컴포넌트
  - `ex) jwt, google, github, ...etc`
- common
  - 전역으로 공통적으로 사용될 파일들로 구성
  - `ex) Dto, Decorator, enum, interface, utils`
- config
  - database, orm 설정 등 추가적으로 특정 패키지의 설정이 들어갈 때 해당 디렉토리에서 모듈화하도록 구성
- exceptions
  - 커스텀하게 특정 예외나 에러를 처리하기 위한 클래스들이 위치할 디렉토리
  - `ex) HttpExceptionFilter`
- interceptors
  - AOP를 위한 특정 역할을 위한 커스텀한 Interceptor 클래스들이 위치할 디렉토리
  - `ex) Logging Interceptor, Transform Interceptor`
- orders
  - 주문 관련 도메인의 파일로 구성
- products
  - 상품 관련 도메인의 파일로 구성
- users
  - 유저 관련 도메인의 파일로 구성
- validations
  - 각종 유효성 검사를 위한 파일로 구성
  - `ex) 환경변수 및 데이터베이스 설정 Validation`

# API

## Order

- 주문 조회 `(GET /orders)`
- 주문 상세 조회 `(GET /orders/{id})`
- 주문 접수 요청 `(POST /orders)`
- 주문 완료 요청 `(POST /orders/complete/{id})`
- 주문 취소 요청 `(POST /orders/cancel/{id})`
- 주문 상품 부분 취소 요청 `(POST /orders/partial-cancel)`
- 주문 수정 `(PUT /orders)`
- 주문 삭제 `(DELETE /orders)`

## Product

- 상품 조회 `(GET /products)`
- 상품 상세 조회 `(GET /products/{id})`
- 상품 등록 `(POST /products)`
- 상품 수정 `(PUT /products/{id})`
- 상품 삭제 `(DELETE /products/{id})`

## User

- 회원 전체 조회 `(GET /users)`
- 회원가입 `(POST /users/register)`
- 로그인 `(POST /users/login)`
