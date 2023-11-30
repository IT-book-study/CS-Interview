# www.github.com을 브라우저에 입력하고 엔터를 쳤을 때, 네트워크 상 어떤 일이 일어나는지 최대한 자세하게 설명해 주세요.

## 키워드

- DNS
- TCP
- HTTP
- Web Server / WAS

## 1. DNS 검색

먼저 브라우저는 www.github.com의 ip주소를 찾습니다.

1. 브라우저는 캐시안에서 www.github.com에 매핑되는 ip를 찾습니다.
2. 없다면, hosts 파일에서 IP주소를 찾습니다.
3. 없다면, DNS에게 도메인주소에 대응하는 IP주소를 UDP로 요청합니다.

## 2. TCP 연결

브라우저가 www.github.com의 ip주소를 알게되면, 해당 ip 주소로 TCP 연결을 합니다.

- 포트번호는 HTTP면 80으로 설정하고, HTTPS면 443으로 설정합니다.
- TCP연결을 할때는 3-way-handshake를 통해서 연결을 합니다.

## 3. HTTP 요청

TCP 연결이 잘 이루어지면, 브라우저는 HTTP 요청을 보내서 html 문서를 받아야 합니다.

- 이때는, GET 메서드가 사용됩니다.

## 4. Web Server vs WAS

HTTP 요청은 웹 서버가 받게 되는데, HTML이나 CSS, javascript와 같은 정적인 문서는 이 단계에서 처리가 가능합니다.

- 다만, 요청에 따라 DB를 사용해야 하거나, 백엔드 상에서 로직 처리가 필요한 경우에는 WAS서버가 요청을 처리합니다.
- WAS서버는 요청마다 스레드를 할당해 처리하는 것으로 알고 있습니다.
- Python 서버 환경에서는 WAS 서버보다 WSGI(Web Server Gateway Interface)서버나 ASGI(Aysnc ...)서버를 주로 사용합니다.
- WSGI: 요청마다 콜백 함수 실행(동기)
- ASGI: WSGI와 호환되는 비동기 인터페이스

## 5. HTTP 응답

HTTP 응답 메시지를 TCP를 통해 브라우저(클라이언트)에게 전송합니다.

- 이때, html문서는 응답 메시지 body에 들어갑니다.
- 만약 URL이 변경되는 등의 이유로 리다이렉트하는 경우도 있는데, `Location` 헤더에 새 주소를 명시합니다.
  - 이때는 다시 브라우저가 새 주소로 HTTP 요청을 보내면 됩니다.

## 참고

https://github.com/SantonyChoi/what-happens-when-KR
