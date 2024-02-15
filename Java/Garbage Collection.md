- JVM(자바 가상 머신)의 **Heap 영역**에서 **동적으로 할당했던 메모리** 중 **필요 없게 된 메모리 객체(garbage)를 모아 주기적으로 제거**하는 프로세스
- C/C++에서는 프로그래머가 메모리 할당과 해제를 직접 해야 하지만, Java에서는 가비지 컬렉터가 이를 대신해주어 **메모리 관리를 효율적**으로 할 수 있고, 개발자는 메모리 관리에 신경 쓰지 않고 **개발에 집중**할 수 있다.
- 객체에 레퍼런스가 있다면 **Reachable**로 구분되고, 객체에 유효한 레퍼런스가 없다면 **Unreachable**로 구분해버리고 수거해버린다. 
### Mark and Sweep
- 의도적으로 GC를 실행해야 하며 application 실행과 병행된다는 특징이 있다
- Mark->Sweep(Delete)->Compact
	1. **Mark 과정** : 먼저 Root Space로부터 그래프 순회를 통해 연결된 객체들을 찾아내어 각각 어떤 객체를 참조하고 있는지 찾아서 마킹한다.
	2. **Sweep 과정** : 참조하고 있지 않은 객체 즉 Unreachable 객체들을 Heap에서 제거한다.
	3. **Compact 과정** : Sweep 후에 분산된 객체들을 Heap의 시작 주소로 모아 메모리가 할당된 부분과 그렇지 않은 부분으로 압축한다. (가비지 컬렉터 종류에 따라 하지 않는 경우도 있음)
### Heap 영역
![[Pasted image 20240214153535.png]]
![[Pasted image 20240214153700.png]]
- Weak Generational Hypothesis를 기반으로 설계되었다
	1. 대부분의 객체는 금방 접근 불가능한 상태(Unreachable)가 된다.
	2. 오래된 객체에서 새로운 객체로의 참조는 아주 적게 존재한다.
- 신규로 생성되는 객체는 [[Young 영역]]에, 오랫동안 살아남은 객체는 [[Old 영역]]에 보관한다
- 더 효율적인 GC를 위해 Young 영역을 Eden, Survivor 0, Survivor 1로 나눈다
### **STW**(Stop The World)
- GC를 수행하기 위해 JVM이 프로그램 실행을 멈추는 현상을 의미
- Major GC의 경우 시간이 오래 걸려서 STW가 발생하게 된다
### Parallel GC
- Java 8의 디폴트 GC
- Minor GC를 멀티 스레드로 실행
- 싱글 스레드로 처리하는 Serial GC에 비해 STW 시간 감소

출처: 
[https://inpa.tistory.com/entry/JAVA-☕-가비지-컬렉션GC-동작-원리-알고리즘-💯-총정리](https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EA%B0%80%EB%B9%84%EC%A7%80-%EC%BB%AC%EB%A0%89%EC%85%98GC-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%F0%9F%92%AF-%EC%B4%9D%EC%A0%95%EB%A6%AC) [Inpa Dev 👨‍💻:티스토리]
https://gyoogle.dev/blog/computer-language/Java/Garbage%20Collection.html