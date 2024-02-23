- 의존성 주입(Dependency Injection)
- 클래스 A 내에서 B가 생성됨
```java
public class A {
    private B b = new B();
}
```
- 의존 대상을 직접 생성하는 것이 아니라 외부로부터 주입받음
```java
public class A {
    private B b;
    
    public A(B b) {
        this.b = b;
    }
}
```
- 위의 생성자 주입 외에도 Setter 주입, 인터페이스 주입이 있다.
- 변경에 덜 취약해진다
- 단위 테스트가 쉬워진다
- 가독성이 높아지고 재사용성이 높아진다
- Spring의 경우 @Autowired를 통해 스프링 컨테이너에서 관리하는 객체인 [[Bean]]을 주입받는다
![[Pasted image 20240223160237.png]]
-  다시 말하지만, 빈 들에 한해서 IoC 컨테이너는 의존성 주입을 아주 쉽게 할 수 있도록 해줄 뿐  의존성 주입은 개발자도 할 수 있습니다.

출처:
[https://kghworks.tistory.com/115](https://kghworks.tistory.com/115) [kghworks:티스토리]
https://velog.io/@9sanha/%EC%8A%A4%ED%94%84%EB%A7%81-Bean-IOC-DI