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
| 1 | 회원 도메인 실행과 테스트 | [1. 회원 도메인 실행과 테스트](src/docs/1.%ED%9A%8C%EC%9B%90_%EB%8F%82%EB%A9%94%EC%9D%B8_%EC%8B%A4%ED%96%89%EA%B3%BC_%20%ED%85%8C%EC%8A%A4%ED%8A%B8.md) |
| 2 | 주문과 할인 도메인 실행과 테스트 | [2. 주문과 할인 도메인 실행과 테스트](src/docs/2.%EC%A3%BC%EB%AC%B8%EA%B3%BC_%ED%95%A0%EC%9D%B8_%EB%8F%82%EB%A9%94%EC%9D%B8_%EC%8B%A4%ED%96%89%EA%B3%BC_%20%ED%85%8C%EC%8A%A4%ED%8A%B8.md) |
| 3 | 새로운 할인 정책 적용과 문제점 | [3. 새로운 할인 정책 적용과 문제점](src/docs/3.%20%EC%83%88%EB%A1%9C%EC%9A%B4_%ED%95%A0%EC%9D%B8_%EC%A0%95%EC%B1%85_%EC%A0%81%EC%9A%A9%EA%B3%BC_%EB%AC%B8%EC%A0%9C%EC%A0%90.md) |
| 4 | 관심사의 분리 | [4. 관심사의 분리](src/docs/4.%EA%B4%80%EC%8B%AC%EC%82%AC%EC%9D%98_%EB%B6%84%EB%A6%AC.md) |
| 5 | 스프링으로 전환하기 | [5. 스프링으로 전환하기](src/docs/5.%EC%8A%A4%ED%94%84%EB%A7%81%EC%9C%BC%EB%A1%9C_%EC%A0%84%ED%99%98%ED%95%98%EA%B8%B0.md) |
| 6 | BeanFactory와 ApplicationContext | [6. BeanFactory와 ApplicationContext](src/docs/6.BeanFactory%EC%99%80_ApplicationContext.md) |
| 7 | BeanDefinition | [7. BeanDefinition](src/docs/7.BeanDefinition.md) |
| 8 | 웹 애플리케이션과 싱글톤 | [8. 웹 애플리케이션과 싱글톤](src/docs/8.%EC%9B%B9_%EC%96%B4%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98%EA%B3%BC_%EC%8B%B1%EA%B8%80%ED%86%A4.md) |
| 9 | 컴포넌트 스캔 | [9. 컴포넌트 스캔](src/docs/9.%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8_%EC%8A%A4%EC%BA%94.md) |
| 10 | 의존관계 주입 방법 | [10. 의존관계 주입 방법](src/docs/10.%20%EC%9D%98%EC%A1%B4%EA%B4%80%EA%B3%84%20%EC%A3%BC%EC%9E%85%20%EB%B0%A9%EB%B2%95.md) |
| 11 | 빈 2개 등록 시 해결 | [11. 빈 2개 등록 시 해결](src/docs/11.%20%EB%B9%88%202%EA%B0%9C%20%EB%93%B1%EB%A1%9D%20%EC%8B%9C%20%ED%95%B4%EA%B2%B0.md) |
| 12 | 빈 생명주기 콜백 | [12. 빈 생명주기 콜백](src/docs/12.%20%EB%B9%88%20%EC%83%9D%EB%AA%85%EC%A3%BC%EA%B8%B0%20%EC%BD%9C%EB%B0%B1.md) |
| 13 | 빈 스코프 | [13. 빈 스코프](src/docs/13.%20%EB%B9%88%20%EC%8A%A4%EC%BD%94%ED%94%84.md) |

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

