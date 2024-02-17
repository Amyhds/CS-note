![[Pasted image 20240214154740.png]]
![[Pasted image 20240214154803.png]]
![[Pasted image 20240214154820.png]]
1. 어떠한 새로운 객체가 들어오면 Eden Space에 할당
2. Eden space가 가득차게 되면, minor garbage collection 시작
3. 참조되는 객체들은 survivor 0로 이동, 비 참조 객체는 Eden space가 clear 될 때 반환
4. 살아남은 객체들은 age가 1씩 증가
5. 또다시 Eden 영역에 신규 객체들로 가득 차게 되면 다시한번 minor GC 발생하고 mark
6. marking 한 객체들을 비어있는 Survival 1으로 이동하고 sweep
7. 살아남은 객체들은 age가 1씩 증가하고 위 과정을 반복, s0과 s1을 왔다갔다 함
8. age가 임계값에 다다르면 Old 영역으로 이동
