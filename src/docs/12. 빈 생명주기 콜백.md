## 빈 생명주기 콜백 시작
데이터베이스 커넥션 풀, 네트워크 소켓처럼 앱 시작 시점에 필요한 연결을 미리 해두고, 종료 시점에 연결을 모두 종료하는 작업을 진행하려면 객체의 초기화와 종료 작업이 필요하다.  

### 스프링 빈 라이프사이클
객체 생성 -> 의존관계 주입  

### 스프링 빈의 이벤트 라이프사이클  
스프링 컨테이너 생성 -> 스프링 빈 생성 -> 의존관계 주입 -> 초기화 콜백 -> 사용 -> 소멸 전 콜백 -> 스프링 컨테이너 종료  

초기화 콜백 : 빈이 생성되고 의존관계 주입이 완료된 후 호출되는 콜백
소멸 콜백 : 빈이 소멸되기 직전에 호출되는 콜백 

<b>참고 : 객체의 생성과 초기화를 분리하자. 생성자 인젝션은 의존관계 주입을 위해 사용하고, 초기화는 초기화 콜백에서 진행하자.</b>

1. 인터페이스 InitializingBean, DisposableBean 사용
```aiignore
**public class NetworkClient implements InitializingBean, DisposableBean **

...

@Override
    public void afterPropertiesSet() throws Exception {
        connect();
        call("초기화 연결 메시지");
    }

    @Override
    public void destroy() throws Exception {
        disconnect();
    }
```
  
단점 : 스프링 전용 인터페이스를 사용해야 하므로, 코드가 스프링에 의존하게 된다. / 외부 라이브러리에 적용할 수 없다. -> 거의 사용하지 않는다. 

