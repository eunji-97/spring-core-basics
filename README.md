# 스프링 핵심 원리 기본편 정리

'스프링 핵심 원리 - 기본편' 강의를 듣고 배운 내용을 정리하고, 실습 코드를 함께 기록한 저장소입니다.

## 📚 학습 범위

이 프로젝트는 스프링의 핵심 개념을 직접 실습하며 이해하는 데 초점을 두고 있습니다.

- 객체 지향 설계와 의존관계 관리
- 스프링 컨테이너와 빈 관리
- 싱글톤과 프로토타입 스코프
- 컴포넌트 스캔과 자동/수동 빈 등록
- 의존관계 주입(DI)
- 빈 생명주기와 콜백
- 스프링의 핵심 원리 이해

## 🗂️ 개념 정리 문서

| 번호 | 주제 | 문서 |
|---|---|---|
| 1 | 회원 도메인 실행과 테스트 | [1. 회원 도메인 실행과 테스트](src/docs/01-member-domain-test.md) |
| 2 | 주문과 할인 도메인 실행과 테스트 | [2. 주문과 할인 도메인 실행과 테스트](src/docs/02-order-discount-domain-test.md) |
| 3 | 새로운 할인 정책 적용과 문제점 | [3. 새로운 할인 정책 적용과 문제점](src/docs/03-discount-policy-problem.md) |
| 4 | 관심사의 분리 | [4. 관심사의 분리](src/docs/04-separation-of-concerns.md) |
| 5 | 스프링으로 전환하기 | [5. 스프링으로 전환하기](src/docs/05-spring-transition.md) |
| 6 | BeanFactory와 ApplicationContext | [6. BeanFactory와 ApplicationContext](src/docs/06-beanfactory-applicationcontext.md) |
| 7 | BeanDefinition | [7. BeanDefinition](src/docs/07-bean-definition.md) |
| 8 | 웹 애플리케이션과 싱글톤 | [8. 웹 애플리케이션과 싱글톤](src/docs/08-webapp-singleton.md) |
| 9 | 컴포넌트 스캔 | [9. 컴포넌트 스캔](src/docs/09-component-scan.md) |
| 10 | 의존관계 주입 방법 | [10. 의존관계 주입 방법](src/docs/10-di-methods.md) |
| 11 | 빈 2개 등록 시 해결 | [11. 빈 2개 등록 시 해결](src/docs/11-duplicate-bean-solution.md) |
| 12 | 빈 생명주기 콜백 | [12. 빈 생명주기 콜백](src/docs/12-bean-lifecycle-callback.md) |
| 13 | 빈 스코프 | [13. 빈 스코프](src/docs/13-bean-scope.md) |

## 🧪 프로젝트 구조

```text
spring-core-basics/
├── src/
│   ├── main/java/hello/core/      # 실습 코드
│   ├── test/java/hello/core/      # 테스트 코드
│   └── docs/                      # 강의 정리 문서
├── build.gradle                  # Gradle 설정
├── settings.gradle               # 프로젝트 설정
├── gradlew                       # Gradle wrapper
├── README.md                     # 프로젝트 소개
└── .gitignore
```

## ▶️ 실행 방법

```bash
./gradlew test
```

테스트를 실행해 실습 코드가 정상 동작하는지 확인할 수 있습니다.

## 🔍 참고

이 저장소는 스프링의 핵심 개념을 이해하는 데 초점을 두며, 각 문서는 실습 코드와 함께 정리되어 있습니다.

