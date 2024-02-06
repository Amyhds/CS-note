- List 인터페이스 구현 클래스
- 배열을 이용하지만 크기가 가변적임
- 삽입과 삭제 시 데이터 이동이 필요하다
	- 5개의 데이터가 있고 맨 앞의 데이터를 삭제했을 때, 나머지 4개를 한칸씩 앞으로 이동
	- 지정된 위치에 요소를 넣을 수 있게 기존의 요소들이 한칸씩 뒤로 이동되면서 빈 공간을 만들어준다
- 배열 공간(capacity)가 꽉 차거나, 요소 중간에 삽입을 행하려 할때 기존의 배열을 복사해서 요소를 뒤로 한칸씩 일일히 이동해야 하는 작업이 필요하다.


출처:
https://inpa.tistory.com/entry/JAVA-%E2%98%95-ArrayList-%EA%B5%AC%EC%A1%B0-%EC%82%AC%EC%9A%A9%EB%B2%95
https://inpa.tistory.com/entry/JCF-%F0%9F%A7%B1-ArrayList-vs-LinkedList-%ED%8A%B9%EC%A7%95-%EC%84%B1%EB%8A%A5-%EB%B9%84%EA%B5%90#linkedlist_vs_arraylist_%ED%8A%B9%EC%A7%95_%EB%B9%84%EA%B5%90