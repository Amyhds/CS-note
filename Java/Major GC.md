![[Pasted image 20240214155124.png]]
1. 객체의 age가 임계값(여기선 8로 설정)에 도달하게 되면,
2. 이 객체들은 Old Generation 으로 이동된다. 이를 promotion 이라 부른다.
3. 위의 과정이 반복되어 Old Generation 영역의 공간(메모리)가 부족하게 되면 Major GC가 발생되게 된다.