주어진 키를 해시 했을 때 충돌이 일어난다고 해서 그 옆의 다른 키가 가야할 자리로 가는 것이 아니라, 해시된 인덱스 안에서 또 다른 자료구조를 사용한다.
### 버킷
- 배열 요소 하나가 다시 여러 개로 이루어지게 한다. 즉 2차원 배열이 된다.
- 키가 일치하는 레코드를 여러 번 찾아야 하는 시간적 부담
### 별도 체인
배열 요소를 연결 리스트를 가리키는 헤드로 만든 것