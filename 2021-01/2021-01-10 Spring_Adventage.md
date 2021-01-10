# Spring의 장점

---

1. 경량화된 컨테이너
    - JAVA 각체를 담고 있음
    - 생성 ~ 소멸과 같은 라이프 사이클을 관리
    - Spring Container로 부터 필요한 객체를 가져와 사용
2. DI (Dependency Injection) 지원
    - 의존성이란?
        - 객체와 객체간의 의존을 의미
        - A라는 클래스에서 B라는 클래스의 메소드를 불러와 실행하게 될 때 그것을 의존한다고 한다
        - B클래스의 메소드 이름이 바뀌어 버리면 A클래스에서도 똑같이 변경해주어야 한다
        - 여러개의 의존 메소드가 바뀌면 변경이 힘들다
    - Spring에서 DI란?
        - 의존성을 제거
        - 별도로 3자가 만들어주는 의존 객체를 각 클래스에 뿌려주는 기능으로 변경의 유연성을 제공

        ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e83a6826-e738-40fb-86f0-0838818534c3/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e83a6826-e738-40fb-86f0-0838818534c3/Untitled.png)

3. AOP (Aspect Oriented Programming, 관점지향 프로그래밍) 지원
    - AOP란
        - 한 어플리케이션 내에서 다양한 모듈에서 공통적으로 이용되는 기능을 분리시켜 사용하는 것
        - 모듈의 핵심 기능 외의 기능을 해당 모듈에 응집되지 않도록 하기 위한 기술
        - Spring을 쓰는 이유중 제일 큰 이유
        - JAVA와는 다르게 특정 클래스들에 대한 수평적인 제어가 가능
4. POJO (Plain Old Java Object) 지원
    - java의 객체지향적인 특징을 살려 비즈니스 로직에 충실한 개발이 가능하도록 함
    - POJO를 사용하는 이유
        - 코드의 간결함 (low레벨의 종속적인 코드를 분리하므로 단순함)
        - 자동화 테스트에 유리
        - 객체지향적 설계의 자유로운 사용
    - POJO의 정리
        - 특정 규약에 종속되지 않는다
        - 특정 환경에 종속되지 않는다
        - 객체지향원리에 충실해야 한다
5. EJB보다 가볍고 배우기도 쉬우며 경량 컨테이너의 기능을 수행한다
    - EJB란
        - 분산 애플리케이션을 지원하는 컴포넌트 기반의 객체
        - Servlet이 Tomcat같은 Servlet Container에 올려서 서비스 되는것 같이 JBoss와 같은 EJB Container에 올려서 서비스 된다