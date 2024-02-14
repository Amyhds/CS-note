- JVM(자바 가상 머신)의 **Heap 영역**에서 **동적으로 할당했던 메모리** 중 **필요 없게 된 메모리 객체(garbage)를 모아 주기적으로 제거**하는 프로세스
- C/C++에서는 프로그래머가 메모리 할당과 해제를 직접 해야 하지만, Java에서는 가비지 컬렉터가 이를 대신해주어 메모리 관리를 효율적으로 할 수 있고, 개발자는 메모리 관리에 신경 쓰지 않고 개발에 집중할 수 있다.
- 객체에 레퍼런스가 있다면 Reachable로 구분되고, 객체에 유효한 레퍼런스가 없다면 Unreachable로 구분해버리고 수거해버린다. 
### **STW**(Stop The World)
GC를 수행하기 위해 JVM이 프로그램 실행을 멈추는 현상을 의미.  
GC가 작동하는 동안 GC 관련 Thread를 제외한 모든 Thread는 멈추게 되어 서비스 이용에 차질이 생길 수 있다.  
따라서 이 시간을 최소화 시키는 것이 쟁점이다.



출처: 
[https://inpa.tistory.com/entry/JAVA-☕-가비지-컬렉션GC-동작-원리-알고리즘-💯-총정리](https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EA%B0%80%EB%B9%84%EC%A7%80-%EC%BB%AC%EB%A0%89%EC%85%98GC-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%F0%9F%92%AF-%EC%B4%9D%EC%A0%95%EB%A6%AC) [Inpa Dev 👨‍💻:티스토리]