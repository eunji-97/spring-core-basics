## 웹 어플리케이션과 싱글톤
웹 어플리케이션은 보통 여러 고객이 동시에 요청을 한다.  

클라 A > memberService 요청 > DI 컨테이너에서 memberService 만들어 반환  
클라 B > memberService 요청 > DI 컨테이너에서 memberService 만들어 반환  

스프링 없는 순수한 DI 컨테이너는 요청마다 객체를 만들어 준다 : 메모리 낭비

객체를 하나만 만들어 공유하도록 설계하자 > **싱글톤 패턴**

## 싱글톤 패턴
클래스의 인스턴스가 딱 1개만 생성되도록 보장하는 디자인 패턴.  
private 생성자를 이용한다.  

```java
    public class SingletonService {

    private static final SingletonService instance = new SingletonService();

    public static SingletonService getInstance() {
        return instance;
    }

    private SingletonService() {} //외부에서 생성하지 못하도록 함
}
```

***스프링 컨테이너는 객체를 싱글톤 패턴으로 관리한다. 그래서 위와 같이 일일이 코드 작성을 해주지 않아도 된다!***

## 싱글톤 컨테이너
스프링 컨테이너는 싱글톤 패턴을 적용하지 않아도, 객체 인스턴스를 싱글톤으로 관리한다.
스프링 컨테이너는 싱글톤 컨테이너 역할을 한다.

## 싱글톤 방식의 주의점
여러 클라이언트가 하나의 같은 객체를 공유하기 때문에 **무상태**로 설계해야 한다.  

- 특정 클라이언트에 의존적인 필드가 있으면 안됨.
- 값을 변경할 수 있는 필드가 있으면 안됨.
- 가급적 읽기만 가능해야 함
- 필드 대신 공유되지 않는 지역변수/파라미터/ThreadLocal 등을 사용해야 함.

```
    @Test
    void statefulServiceSingleton() {
        ApplicationContext ac = new AnnotationConfigApplicationContext(TestConfig.class);
        StatefulService statefulService1 = ac.getBean(StatefulService.class);
        StatefulService statefulService2 = ac.getBean(StatefulService.class);

        //ThreadA : A 사용자 10000원 주문
        statefulService1.order("userA", 10000);

        //ThreadB : B 사용자 20000원 주문
        statefulService2.order("userB", 20000);

        //ThreadA : A 사용자 주문 금액 조회
        int price = statefulService1.getPrice();
        System.out.println(price); //20000원으로 문제!

        assertThat(statefulService1.getPrice()).isEqualTo(20000);
    }
```

## @Configuration
```
    @Bean
    public MemberService memberService() {
        return new MemberServiceImpl(memberRepository());
    }

    @Bean
    public MemberRepository memberRepository() {
        return new MemoryMemberRepository();
    }

    @Bean
    public OrderService orderService() {
        return new OrderServiceImpl(memberRepository(), discountPolicy());
    }
    
    셋 다 memberRepository 를 호출하고 있는데, 싱글톤이 깨지지 않는걸까?
   
```
스프링은 어떠한 경우라도 싱글톤을 보장해준다!

스프링은 CGLIB 라는 라이브러리를 사용해 AppConfig을 상속받은 임의 클래스를 만들어 빈으로 등록한다.
이게 싱글톤을 보장해주는 것.

Configuration이 붙지 않은 @Bean은 CGLIB를 이용하지 않아 싱글톤이 보장되지 않는다.