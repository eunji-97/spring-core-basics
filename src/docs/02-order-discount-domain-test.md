## 단일 책임 원칙

``` 
    public class OrderServiceImpl implements OrderService{

    private final MemberRepository memberRepository = new MemoryMemberRepository();
    private final DiscountPolicy discountPolicy = new FixDiscountPolicy(); 

    @Override
    public Order createOrder(Long memberId, String itemName, int itemPrice) {
        Member member = memberRepository.findById(memberId);
        int discountPrice = discountPolicy.discount(member, itemPrice);

        return new Order(memberId, itemName, itemPrice, discountPrice);
    }
}
```
나중에 할인 정책이 바뀌더라도 서비스 코드 전체를 변경하는 것이 아닌 **DiscountPolicy**에서만 변경하면 된다.
이는 단일 책임 원칙(SRP)이 잘 지켜진 사례로 볼 수 있다.

***SRP 단일 책임 원칙***  
하나의 클래스는 하나의 책임(기능)만을 가져야 한다.

