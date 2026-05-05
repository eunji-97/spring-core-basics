## 관심사의 분리
3번의 문제를 해결하려면 책임의 분리가 필요하다.

## AppConfig 등장
전체 동작 방식을 구성하기 위해 구현 객체를 생성 / 연결하는 책임을 가지는 별도의 클래스를 만들어보자

```
public class AppConfig {

    public MemberService memberService() {
        return new MemberServiceImpl(new MemoryMemberRepository());
    }
}
```  

이렇게 하면,
```
public class MemberServiceImpl implements MemberService{

    private MemberRepository memberRepository;

    public MemberServiceImpl(MemberRepository memberRepository) {
        this.memberRepository = memberRepository;
    }
```
**MemberServiceImpl**은 생성자를 통해서만 memberRepository를 받게 되고, 더 이상 의존하지 않게 된다.
오직 외부에서만 결정되도록 만든것!  

클라이언트인 MemberServiceImpl 입장에선 의존 관계를 마치 외부에서 주입해주는거 같다고 해서 **의존 관계 주입 / 의존성 주입 / DI** 라고 한다.

