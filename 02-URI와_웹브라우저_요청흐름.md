

## URI와 웹 브라우저 요청 흐름

### URI (Uniform Resource Identifier)
리소스를 식별하는 통합된 방법   
URI(Resource Identifier) = URL(Resource Lodator) + URN(Resource Name)

- Uniform: 리소스 식별하는 통일된 방식
- Resource: 자원, URI로 식별할 수 있는 모든 것(제한 없음)
- Identifier: 다른 항목과 구분하는데 필요한 정보   
- URL - Locator: 리소스가 있는 위치 지정
- URN - Name: 리소스에 이름을 부여
- 위치는 변할 수 있지만, 이름은 변하지 않는다.
- URN 이름만으로 실제 리소스를 찾을 수 있는 방법이 보편화 되지 않음

### URL 전체 문법
- scheme://[userinfo@]host:[:port][/port][?query][#fragment]   
   https://www.google.com:443/search?q=hello&hi=ko

scheme
- 주로 프로토콜 사용
- 프로토콜: 어떤 방식으로 자원에 접근할 것인가 하는 약속 규칙 예) http, https, ftp 등등
- http는 80 포트, https는 443 포트를 주로 사용, 포트는 생략 가능
- https는 hhp에 보안 추가 (HTTP Secure)
  
userinfo
- URL에 사용자정보를 포함해서 인증
- 거의 사용하지 않음

host
- 호스트명
- 도메인명 또는 IP 주소를 직접 사용가능

PORT
- 포트(PORT)
- 접속포트
- 일반적으로 생략, 생략시 htp는 80, https는 443

path
- 리소스 경로(path), 계층적 구조
- 예) /home/file1.jpg , /members , /members/100, /items/iphone12

query
- key=value의 형태
- ?로 시작, &로 추가 가능 ?keyA = valueA & keyB = valueB
- query parameter, query string 등으로 불림, 웹서버에 제공하는 파라미터. 문자 형태

fragment
- html 내부 북마크 등에 사용
- 서버에 전송하는 정보 아님

### 웹 브라우저 요청 흐름
```
# HTTP 요청 메세지 
GET /search?q=hello&hi=ko HTTP/1.1 Host:www.google.com

# HTTP 응답 메세지 
HTTP/1.1 200 OK
Content-Type:text/html;charset=UTF-8
Content-Length: 3423

<html>
    <body>..</body>
</html>
```
### HTTP 메세지 전송
1. 웹 브라우저가 HTTP 메세지 생성
2. SOCKET 라이브러리를 통해 전달 
 - A: TCP/IP 연결(IP,PORT)
 - B: 데이터 전달
3. TCP/IP 패킷 생성, HTTP 메시지 포함
4. 웹 브라우저 HTML 렌더링