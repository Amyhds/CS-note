1. **원자성(Atomicity)**: 트랜잭션의 작업이 부분적으로 실행되거나 중단되지 않는 것을 보장하는 것을 말한다. 즉, All or Nothing의 개념으로서 작업 단위를 일부분만 실행하지 않는다는 것을 의미한다.
    
    ex. 트랜잭션이 A통장에서 돈을 출금하여 B통장에 입금하는 동작을 수행할 때, A통장에서만 돈을 출금하면 그 돈은 증발한다…(데이터 부정합 발생) 그렇기에 동작이 완전이 수행되지 않으면 롤백 시켜서 부분 실행을 막는다.
    
2. **일관성(Consistency)**: 트랜잭션이 성공적으로 완료되면 데이터베이스의 제약이나 규칙이 일관되어야 한다는 뜻이다. 여기서 말하는 일관성이란, 위의 송금 예제에서 금액의 데이터 타입이 정수형인데, 갑자기 문자열이 되지 않는 것을 말한다.
    
3. **격리성(Isolation)**: 트랜잭션 수행시 다른 트랜잭션의 작업이 끼어들지 못하도록 보장하는 것을 말한다. 격리 수준에 따라 ①READ UNCOMMITTED, ②READ COMMITTED, ③REPEATABLE READ, ④SERIALIZABLE이 있다.
    
4. **지속성(Durability)**: 성공적으로 수행된 트랜잭션은 영원히 반영이 되는 것을 말한다. commit을 하면 현재 상태는 영원히 보장된다. 이를 위해 commit이 성공하면 트랜잭션에 대한 로그를 남긴다. 그렇기에 DB에 오류가 발생해 종료되어도 로그 기록을 확인해 복구할 수 있다.