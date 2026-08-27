## 새로운 할인 정책 적용 시 보이는 문제
```
private final DiscountPolicy discountPolicy = new FixDiscountPolicy();

변경 시 

private final DiscountPolicy discountPolicy = new RateDiscountPolicy();
```
위와 같이 새로운 정책을 적용하려 구체 클래스를 변경하는 순간 OrderServiceImpl 코드에서 수정을 해야 한다는 문제점이 발견된다.  
서비스가 **DiscountPolicy** 라는 인터페이스에도, **FixDiscountPolicy/RateDiscountPolicy** 구현체에도 의존하고 있는 형태이다.

이는 **OCP / DIP 위반**이다.


## 해결방법
인터페이스에만 의존하도록 코드를 변경하자

```
private DiscountPolicy discountPolicy;
```
하지만 이대로는 구현체를 만들어 주지 않아 NPE가 발생한다. 그래서 누군가 OrderServiceImpl 에 구현 객체를 대신 생성하고 주입해주어야 한다.

