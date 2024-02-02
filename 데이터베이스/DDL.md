DDL이란 Data Definition Language의 약자로, DBMS의 모든 오브젝트를 생성 또는 변경하는 명령어입니다. 주로 스토어드 프로시저, 테이블, 데이터베이스, 함수를 생성/변경합니다.

1. CREATE : 생성
2. ALTER : 변경
3. DROP : 삭제
	테이블 전체를 삭제하며, 공간, 객체를 삭제합니다. 자동 commit이 되므로 삭제 후 rollback이 불가합니다.
4. TRUCATE : 테이블 초기화
	테이블 용량이 줄어 들고 인덱스 등도 모두 삭제됩니다. 최초 생성 시의 storage만 남기고, 데이터를 모두 삭제합니다. 자동 commit이 되므로 삭제 후 rollback이 불가합니다.
![[Pasted image 20240201122717 1.png]]
![[Pasted image 20240131161545.png]]