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