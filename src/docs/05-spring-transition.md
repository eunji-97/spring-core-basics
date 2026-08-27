## 스프링으로 전환하기 

```
@Configuration //설정 정보 어노테이션
public class AppConfig {

    @Bean // 빈 등록
    public MemberService memberService() {
        return new MemberServiceImpl(memberRepository());
    }
```

### 실제 사용
```
//        AppConfig appConfig = new AppConfig();
//        MemberService memberService = appConfig.memberService();
//        OrderService orderService = appConfig.orderService();

    ApplicationContext applicationContext = new AnnotationConfigApplicationContext(AppConfig.class);
    MemberService memberService = applicationContext.getBean("memberService", MemberService.class);
    OrderService orderService = applicationContext.getBean("orderService", OrderService.class);
```
- ApplicationContext를 스프링 컨테이너라 한다.
- 스프링 컨테이너는 @Configuration 이 붙은 클래스를 설정 정보로 사용한다. @Bean이라 적힌 모든 메서드를 효출해 반환된 객체를 스프링 컨테이너에 등록한다.
- 빈의 이름은 메서드 이름