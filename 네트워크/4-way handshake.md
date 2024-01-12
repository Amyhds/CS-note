TCP 연결을 종료하기 위한 과정
![[Pasted image 20240112135837.png]]
1. 연결 종료 요청(FIN)
	- 클라이언트가 서버에게 FIN 플래그를 보낸다
2. 연결 종료 응답(ACK)
	- 서버는 확인했다는 ACK를 클라이언트에게 보낸다
	- 모든 데이터를 보내기 위해 CLOSE_WAIT 상태가 된다
3. 상대방 연결 종료 요청(FIN)
	- 데이터를 모두 보냈다면 연결 종료 준비가 되었다는 FIN 플래그를 클라이언트에게 보낸다
4. 상대방 연결 종료 응답(ACK)
	- 클라이언트는 FIN을 받고 확인했다는 ACK를 서버에 보낸다
	- 서버는 CLOSED 된다
	- 서버로부터 받지 못한 데이터가 있을 수 있으므로 TIME_WAIT를 통해 기다린다
	- 클라이언트도 CLOSED 된다

출처:
https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Network/TCP%203%20way%20handshake%20%26%204%20way%20handshake.md
https://amyislearning.notion.site/3-way-hand-shake-4-way-hand-shake-5f4af0abe34644c0b9d7e632dc9f46b4?pvs=4
면접을 위한 CS 전공지식 노트