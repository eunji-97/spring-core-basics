## 의존관계 주입 방법
1. 생성자 주입  
생성자 호출 시점에 딱 한번만 호출 / 불변, 필수 의존관계 사용

```aiignore
private final MemberRepository memberRepository;
private final DiscountPolicy discountPolicy;

@Autowired
    public OrderServiceImpl(MemberRepository memberRepository, DiscountPolicy discountPolicy) {
        this.memberRepository = memberRepository;
        this.discountPolicy = discountPolicy;
}
```  

생성자가 하나만 있다면 @Autowired 생략 가능

2. setter 주입  
수정자 메서드를 통해 주입 / 선택, 변경 가능점이 있는 의존관계에 사용

```aiignore
private MemberRepository memberRepository;
private DiscountPolicy discountPolicy;

@Autowired
public void setMemberRepository(MemberRepository memberRepository) {
    this.memberRepository = memberRepository
}

@Autowired
public void setDiscountPolicy(DiscountPolicy discountPolicy) {
    this.discountPolicy = discountPolicy
}
```  

3. 필드 주입  
필드 자체에 값을 그대로 넣어버리는 방법 / 순수 테스트 코드를 작성하는게 어려움 (결국은 setter로 지정해야 되기 때문) / 권장하지 않음  

```aiignore
@Autowired private MemberRepository memberRepository;
@Autowired private DiscountPolicy discountPolicy;
```  

4. 일반 메서드 주입  
일반 메서드에 주입 (아무 메서드에) / 사실상 setter 주입이랑 다를게 없음 / 잘 사용하지 않음

```aiignore
@Autowired
public void init(DiscountPolicy discountPolicy) {
    this.discountPolicy = discountPolicy
}
```  

## 옵션 처리
주입할 빈이 없어도 동작해야 할 경우가 있음  

@Autowired required 기본값은 true이지만 주입할 빈이 없을 때 실행해야 하는 경우 false로 처리할 수 있다.

1. @Autowired(require=false) : 수정자 메서드 자체가 호출 안됨
2. @Nullable : 없을 경우 null을 넣음
3. Optional<> : 없을 경우 Optional.empty


## 생성자 주입을 선택해야 하는 이유
1. 불변
2. 누락 방지 (컴파일러 선에서 방지 가능)
3. final 키워드
4. @RequiredArgsConstructor 롬복과 함께 사용 가능