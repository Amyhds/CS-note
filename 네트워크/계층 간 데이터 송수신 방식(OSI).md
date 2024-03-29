OSI 7계층을 통해 데이터를 보낼 때에는 전송 계층에서 데이터를 작은 단위로 분할하고, 하위 계층을 따라 내려가며 각각의 분할된 데이터마다 네트워크 전송을 위한 부가정보를 추가하는 작업이 일어납니다. 
이 과정을 **인캡슐레이션**이라고 합니다. 전송 정보를 추가하는 작업은 계층마다 ‘헤더’라는 영역을 한 겹씩 추가하고, 그 안에 계층별로 필요한 정보를 집어넣는 방식으로 이루어집니다.

- 전송 계층에서는 목적지의 포트 주소가 추가됩니다.
	3 way handshake 등에 사용하는 ACK, SYN 등의 정보 또한 여기서 추가됩니다.
        흐름 제어를 위해 사용되는 윈도우 크기도 추가됩니다.
- 네트워크 계층에서는 IP 주소 정보가 추가됩니다.
- 데이터 링크 계층에서는 MAC 주소 정보가 추가됩니다.
	그리고 끝단에 ‘트레일러’영역을 추가하여 오류를 검출하는 비트를 추가합니다.
- 물리 계층은 완성된 결과물을 전기 신호로 변환합니다.

이렇게 전송된 전기 신호가 목적지 컴퓨터에 도착하고 난 뒤, OSI 7계층을 역순으로 거슬러 올라가며 부착했던 부가정보들을 한 겹씩 확인하고 폐기하는 과정을 거칩니다. 이를 **디캡슐레이션**이라고 합니다.

- 데이터 링크 계층, 네트워크 계층은 헤더에 기록된 목적지 주소가 현재 컴퓨터가 맞는지 확인합니다.
- 전송 계층에서는 데이터가 순서대로 빠짐없이 도착했는지 확인합니다.