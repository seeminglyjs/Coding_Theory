# JavaScript
- [X forword for](https://github.com/seeminglyjs/Coding_Theory/edit/main/Network/#X_forword_for)

# X_forword_for

---
### X forword for 정의
    X-Forwarded-For (XFF) 헤더는 HTTP 프록시나 로드 밸런서를 통해 웹 서버에 접속하는 클라이언트의 원 IP 주소를 식별하는 사실상의 표준 헤더다. 
    클라이언트와 서버 중간에서 트래픽이 프록시나 로드 밸런서를 거치면, 
    서버 접근 로그에는 프록시나 로드 밸런서의 IP 주소만을 담고 있다. 
    클라이언트의 원 IP 주소를 보기위해 X-Forwarded-For 요청 헤더가 사용된다.
    이 헤더는 디버깅, 통계, 그리고 위치 종속적인 컨텐츠를 위해 사용되고, 
    클라이언트의 IP 주소 등과 같은 민감한 개인정보를 노출시킨다. 
    그러므로 이 헤더를 사용할 때에는 사용자의 프라이버시를 주의해야 한다.
    이 헤더의 표준화된 버전은 HTTP Forwarded 헤더다.
    
### X forword for 지시자
    <client>
    클라이언트 IP 주소
    <proxy1>, <proxy2>
    하나의 요청이 여러 프록시들을 거치면, 각 프록시의 IP 주소들이 차례로 열거된다. 
    즉, 가장 오른쪽 IP 주소는 가장 마지막에 거친 프록시의 IP 주소이고, 가장 왼쪽의 IP 주소는 최초 클라이언트의 IP 주소다.
    ex) X-Forwarded-For: client, proxy1, proxy2
      
### X forword for 참고 예제
     https://sg-choi.tistory.com/540
     https://linked2ev.github.io/java/2019/05/22/JAVA-1.-java-get-clientIP/
---
