## 빈이 2개 이상일때 해결 방법
1. @Autowired 에서 빈 이름, 파라미터 이름으로 매칭  
   - @Autowired는 타입 매칭을 먼저 수행하고, 그 다음에 이름 매칭을 수행한다.  
   - 따라서, 타입이 같은 빈이 2개 이상 존재하면 이름으로 매칭을 시도한다. 
   
2. @Qualifier("빈이름") : 빈 이름으로 매칭  
   - @Qualifier를 사용하면, 빈 이름을 명시적으로 지정할 수 있다.  
   - 예를 들어, @Qualifier("mainDiscountPolicy")를 사용하면, mainDiscountPolicy라는 이름의 빈을 찾아서 주입한다.
   - 명확하지 않은 방법이기 때문에 권장하지 않는다.

3. @Primary : 우선순위가 높은 빈을 매칭  (자주 사용)
   - @Primary를 사용하면, 동일한 타입의 빈이 여러 개 존재할 때, 우선순위가 높은 빈을 선택할 수 있다.  
   - 예를 들어, @Primary를 붙인 DiscountPolicy 빈이 있다면, @Autowired만 사용해도 해당 빈이 주입된다. 
   - 따라서, 동일한 타입의 빈이 여러 개 존재할 때는 @Primary를 사용하여 우선순위를 지정하는 것이 좋다.

## 어노테이션 생성
```aiignore
@Target({ElementType.FIELD, ElementType.METHOD, ElementType.PARAMETER, ElementType.TYPE, ElementType.ANNOTATION_TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Inherited
@Documented
@Qualifier("mainDiscountPolicy")
public @interface MainDiscountPolicy {   
}
```  
   