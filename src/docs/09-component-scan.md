## 컴포넌트 스캔
지금까지는 스프링 빈 등록 시 @Bean / <bean> 을 사용했다.  
하지만 등록해야 할 빈이 많아질경우 이 과정은 번거롭다.  

그래서 스프링은 설정 정보 없이도 빈을 등록해주는 @ComponentScan이라는 기능과 의존관계도 자동으로 주입하는 @Autowired 기능을 제공한다.  

@ComponentScan을 사용하면 @Configuration 붙은 설정 정보도 자동으로 등록되기 때문에 예제에서는 제외해둔 상황

베이스 패키지를 지정해 스캔 위치를 지정해줄 수 있다. (여러개도 가능)  
지정하지 않으면 @ComponentScan이 있는 클래스의 파일 위치가 시작 위치가 된다.  
권장은 패키지 최상단에 두는 것.
```aiignore
@ComponentScan(
        basePackages = "hello.core.member",
        basePackageClasses = AutoAppConfig.class
) 
```

## 필터
- includeFilters : 컴포넌트 스캔 대상을 추가로 지정한다.
- excludeFilters : 스캔 대상을 제외시킨다.

```aiignore
@ComponentScan(
            includeFilters = @ComponentScan.Filter(type = FilterType.ANNOTATION, classes = MyIncludeComponent.class),
            excludeFilters = @ComponentScan.Filter(type = FilterType.ANNOTATION, classes = MyExcludeComponent.class)
    )
```

### 