## BeanFactory
스프링 컨테이너의 최상위 인터페이스.
스프링 빈을 관리하고 조회하는 역할이다.

## ApplicationContext
BeanFactory 기능을 모두 상속받아 제공한다.  
둘의 차이는 무엇인가? >> 부가기능의 차이

### ApplicationContext 부가 기능
**MessageSource** : 메시지 소스를 활용한 국제화 기능 (한국에서 들어가면 한국어로 나오는 기능)
**EnvironmentCapable** : 환경 변수, 로컬/개발/운영등을 구분해 처리
**ApplicationEventPublisher** : 애플리케이션 이벤트. 이벤트를 발행하고 구독하는 모델을 편리하게 지원
**ResourceLoader** : 편리한 리소스 조회. 파일/클래스 패스/외부 등에서 리소스를 편리하게 조회