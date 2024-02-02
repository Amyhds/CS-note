- Data Manipulation Language로 데이터 조작어를 뜻한다
- 테이블에 새 데이터를 삽입하거나 저장된 데이터를 수정, 삭제, 검색하는 기능을 제공한다

1. SELECT: 검색
2. INSERT: 삽입
3. UPDATE: 수정
4. DELETE: 삭제
	데이터는 지워지지만 테이블 용량은 줄지 않습니다. 원하는 데이터만 지울 수 있으며, 삭제 후 commit 이전에 rollback을 통해 잘못 삭제한 것을 되돌릴 수 있습니다.