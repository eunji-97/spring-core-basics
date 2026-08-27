## BeanDefinition
스프링 빈 설정 메타 정보  
@Bean(자바), <bean>(xml) 당 각각 하나씩 메타 정보가 생성된다.
스프링 컨테이너는 이 정보를 기반으로 스프링 빈을 생성한다.  

스프링 컨테이너 -> BeanDefinition <- AppConfig.class / appConfig.xml / appConfig.xxx