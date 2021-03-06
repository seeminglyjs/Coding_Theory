# Linux
- [iptables](https://github.com/seeminglyjs/Coding_Theory/edit/main/Linux/#iptables)
- [IO Redirection](https://github.com/seeminglyjs/Coding_Theory/edit/main/Linux/#IO_Redirection)
- [SHELL](https://github.com/seeminglyjs/Coding_Theory/edit/main/Linux/#SHELL)
- [SHELL Script](https://github.com/seeminglyjs/Coding_Theory/edit/main/Linux/#SHELL_Script)
- [Package manager](https://github.com/seeminglyjs/Coding_Theory/edit/main/Linux/#Package_manager)
- [file download](https://github.com/seeminglyjs/Coding_Theory/edit/main/Linux/#file_download)
- [find사용법](https://github.com/seeminglyjs/Coding_Theory/edit/main/Linux/#find)
- [ps와 grep](https://github.com/seeminglyjs/Coding_Theory/edit/main/Linux/#ps_grep)
- [background](https://github.com/seeminglyjs/Coding_Theory/edit/main/Linux/#background)
---
# iptables

###    - 정의
     
  iptables란 넷필터 프로젝트에서 개발했으며 광범위한 프로토콜 상태 추적, 패킷 애플리케이션 계층검사, 속도 제한, 
  필터링 정책을 명시하기 위한 강력한 매커니즘을 제공한다.


###   -iptables 용어


#### 테이블(tables)
  우선 iptables에는 테이블이라는 광범위한 범주가 있는데, 이 테이블은 filter, nat, mangle, raw 같은 4개의 테이블로 구성되며, 
  이중에서 우리에게 필요한 것은 필터링 규칙을 세우는 filter 테이블이다.

#### 체인(chain)
  iptables에는 filter 테이블에 미리 정의된 세가지의 체인이 존재하는데 이는 INPUT, OUTPUT, FORWARD 이다. 
  이 체인들은 어떠한 네트워크 트래픽(IP 패킷)에 대하여 정해진 규칙들을 수행한다.
  가령 들어오는 패킷(INPUT)에 대하여 허용(ACCEPT)할 것인지, 거부(REJECT)할 것인지, 버릴(DROP)것인지를 결정한다.

  * INPUT : 호스트 컴퓨터를 향한 모든 패킷
  * OUTPUT : 호스트 컴퓨터에서 발생하는 모든 패킷
  * FORWARD : 호스트 컴퓨터가 목적지가 아닌 모든 패킷, 즉 라우터로 사용되는 호스트 컴퓨터를 통과하는 패킷
  
####  매치(match)
  iptables에서 패킷을 처리할때 만족해야 하는 조건을 가리킨다. 즉, 이 조건을 만족시키는 패킷들만 규칙을 적용한다.

   * --source (-s) : 출발지 IP주소나 네트워크와의 매칭
   * --destination (-d) : 목적지 ip주소나 네트워크와의 매칭
   * --protocol (-p) : 특정 프로토콜과의 매칭
   * --in-interface (-i) : 입력 인테페이스
   * --out-interface (-o) : 출력 인터페이스
   * --state : 연결 상태와의 매칭
   * --string : 애플리케이션 계층 데이터 바이트 순서와의 매칭
   * --comment : 커널 메모리 내의 규칙과 연계되는 최대 256바이트 주석
   * --syn (-y) : SYN 패킷을 허용하지 않는다.
   * --fragment (-f) : 두 번째 이후의 조각에 대해서 규칙을 명시한다.
   * --table (-t) : 처리될 테이블
   * --jump (-j) : 규칙에 맞는 패킷을 어떻게 처리할 것인가를 명시한다.
   * --match (-m) : 특정 모듈과의 매치
  
####  타겟(target)
  iptables는 패킷이 규칙과 일치할 때 동작을 취하는 타겟을 지원한다.

   * ACCEPT : 패킷을 받아들인다.
   * DROP : 패킷을 버린다(패킷이 전송된 적이 없던 것처럼).
   * REJECT : 패킷을 버리고 이와 동시에 적절한 응답 패킷을 전송한다.
   * LOG : 패킷을 syslog에 기록한다.
   * RETURN : 호출 체인 내에서 패킷 처리를 계속한다.
  
   * REJECT는 서비스에 접속하려는 사용자의 액세스를 거부하고 connection refused라는 오류 메시지를 보여주는 반면 
     DROP은 말 그대로 telnet 사용자에게 어떠한 경고 메시지도 보여주지 않은 채 패킷을 드롭한다. 
     관리자의 재량껏 이러한 규칙을 사용할 수 있지만 사용자가 혼란스러워하며 계속해서 접속을 시도하는 것을 방지하려면 REJECT를 사용하는 것이 좋다.

#### 연결 추적(Connection Tracking)
  iptables는 연결 추적(connection tracking)이라는 방법을 사용하여 내부 네트워크 상 서비스 연결 상태에 따라서 그 연결을 감시하고 제한할 수 있게 해준다. 
  연결 추적 방식은 연결 상태를 표에 저장하기 때문에, 다음과 같은 연결 상태에 따라서 시스템 관리자가 연결을 허용하거나 거부할 수 있다.

   * NEW : 새로운 연결을 요청하는 패킷, 예, HTTP 요청
   * ESTABLISHED : 기존 연결의 일부인 패킷
   * RELATED : 기존 연결에 속하지만 새로운 연결을 요청하는 패킷, 예를 들면 접속 포트가 20인 수동 FTP의 경우 전송 포트는 사용되지 않은 1024 이상의 어느 포트라도 사용 가능하다.
   * INVALID : 연결 추적표에서 어디 연결에도 속하지 않은 패킷
  상태에 기반(stateful)한 iptables 연결 추적 기능은 어느 네트워크 프로토콜에서나 사용 가능하다. UDP와 같이 상태를 저장하지 않는 (stateless) 프로토콜에서도 사용할 수 있다.

#### 명령어(commond)
   * -A (--append) : 새로운 규칙을 추가한다.
   * -D (--delete) : 규칙을 삭제한다.
   * -C (--check) : 패킷을 테스트한다.
   * -R (--replace) : 새로운 규칙으로 교체한다.
   * -I (--insert) : 새로운 규칙을 삽입한다.
   * -L (--list) : 규칙을 출력한다.
   * -F (--flush) : chain으로부터 규칙을 모두 삭제한다.
   * -Z (--zero) : 모든 chain의 패킷과 바이트 카운터 값을 0으로 만든다.
   * -N (--new) : 새로운 chain을 만든다.
   * -X (--delete-chain) : chain을 삭제한다.
   * -P (--policy) : 기본정책을 변경한다.
  
#### 기본 동작
  패킷에 대한 동작은 위에서 부터 차례로 각 규칙에 대해 검사하고, 그 규칙과 일치하는 패킷에 대하여 타겟에 지정한 ACCEPT, DROP등을 수행한다.
  규칙이 일치하고 작업이 수행되면, 그 패킷은 해당 규칙의 결과에 따리 처리하고 체인에서 추가 규칙을 무시한다.
  패킷이 체인의 모든 규칙과 매치하지 않아 규칙의 바닥에 도달하면 정해진 기본정책(policy)이 수행된다.
  기본 정책은 policy ACCEPT , policy DROP 으로 설정할 수 있다.
  일반적으로 기본정책은 모든 패킷에 대해 DROP을 설정하고 특별히 지정된 포트와 IP주소등에 대해 ACCEPT를 수행하게 만든다.

---

#### iptables 출력
  Iptables의 룰셋을 확인할때 아래와 같이 하면 보기 더 편리하다.
  출처: https://webdir.tistory.com/170 [WEBDIR]

```
BASH
iptables -nL

  Chain INPUT (policy DROP)
  target     prot opt source               destination
  ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
  ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
  ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22
  ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53
  ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53
  ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80
  ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:443
  ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:3306

  Chain FORWARD (policy DROP)
  target     prot opt source               destination

  Chain OUTPUT (policy ACCEPT)
  target     prot opt source               destination
```

아래와 같이 각 룰셋의 적용순서까지 확인 가능한 방법도 있다.

```
BASH
iptables -nL --line-numbers

  Chain INPUT (policy DROP)
  num  target     prot opt source               destination
  1    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
  2    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
  3    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22
  4    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53
  5    ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53
  6    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80
  7    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:443
  8    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:3306

  Chain FORWARD (policy DROP)
  num  target     prot opt source               destination

  Chain OUTPUT (policy ACCEPT)
  num  target     prot opt source               destination
```

```
BASH
iptables -L -v

  Chain INPUT (policy DROP 1626 packets, 214K bytes)
   pkts bytes target     prot opt in     out     source               destination
      0     0 ACCEPT     all  --  lo     any     anywhere             anywhere
    944  194K ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED
      0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh
      0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:domain
      4   245 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:domain
      6   304 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:http
      0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:https
      2    88 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:mysql

  Chain FORWARD (policy DROP 0 packets, 0 bytes)
   pkts bytes target     prot opt in     out     source               destination

  Chain OUTPUT (policy ACCEPT 179 packets, 22190 bytes)
   pkts bytes target     prot opt in     out     source               destination
```



---    

# find

###    - 정의
          find 명령만 입력하면 현재 디렉토리(.)에 있는 파일을 찾는다.(하위 디렉토리. 숨겨진 파일도 표시)
          ex) find /etc -name "ssh*" -> etc에 있는 파일중 ssh로 시작하는 모든 파일을 찾는다.

###    - name 옵션
          찾는 파일의 이름을 지정할때 사용한다.

###    - type 옵션
         파일의 형식을 지정해서 찾을 수 있다.
         ex) find /etc -name "test" -type d -> etc 폴더에 test라는 파일인데 그중 디렉토리인 것만 찾아라

###    - size 옵션
          파일의 사이즈를 지정해서 검색을 할 수 있다.
          ex) find /etc -size +10M -> 사이즈가 10M 이상인 파일들을 찾아라

###    - empty 옵션         
          빈파일을 찾을 때 사용한다.
          ex) find . -empty
         
###    - maxdepth 옵션    
          maxdepth 옵션으로 서브 디렉토리 검색 깊이를 지정한다.
          ex) find /etc -maxdepth 2 -name 'x*' -> 최대 깊이가 2인 파일중 이름이 x로 시작하는 모든 파일을 찾아라
          
###    - newer 옵션 
          newer 옵션 뒤에 적힌 파일보다 최근에 변경된 파일을 검색한다.
          ex) find . -newer game.py -> 최근에 변경된  game.py파일을 찾는다.
          
###    - exec 옵션 
          exec 옵션 뒤에 명령어를 입력하여 검색한 파일로 부가적인 작업을 수행할 수 있다.
          (검색된 파일이 {} 위치에 입력되어 처리된다.)
           ex)find . -empty -exec ls -l {} \; -> 빈파일들을 찾아 나열한다.
           ex)find . -empty -exec rm {} \;   -> 빈파일들을 찾아 삭제한다.
           
###    - 2>/dev/null 옵션 
          'Permission denied'와 같은 오류를 무시하기 위해 리다이렉션을 사용할 수 있다.
          (sudo 명령을 사용할 수 없는 경우에 효과적이다.)
          ex)find / -name "test*" 2>/dev/null -> 권한 오류를 무시하고 test라고 시작하는 이름의 파일을 찾는다.
          출처 https://withcoding.com/97
          
          
 ---    

# Package_manager

###    - apt
          apt-get update; -> apt패키지 매니저를 최신상태로 다운로드한다.
          apt-cache search htop -> htop 패키지들을 캐시에서 찾는다.
          apt-get install htop ->  -> htop 패키지를 설치한다.

          (htop 은 윈도우의 작업관리자 같은 소프트웨어이다.)

          apt-get upgrade htop -> htop 프로그램을 최신화한다.
          apt-get upgrade -> apt로 설치한 모든 패키지를 최신화한다.
          apt -get remove htop -> htop 를 삭제한다.

 ---

# file_download

###    - wget
          wget [url정보] -> url에 있는 파일을 다운로드한다.
          mv dowload hello.jpeg -> 파일이름을 hello.jpeg 로 변경한다.

          wget -O hello.jpeg url정보] -> 파일이름을 hello.jpeg 로 저장한다.
          
 ---

# ps_grep

###    - 예제
          grep [찾고싶은내용] [찾고싶은내용을가지고있는파일]
          ls --help | grep [찾고싶은내용] ->ls --help에 파이프(|) 로 연결해서 [찾고싶은내용] 을 가져온다.
          ls --help | grep [찾고싶은내용] | grep [찾고싶은내용] -> 파이프는 계속 연결해서 사용해서 사용할 수 있다.
          ps aux | grep apache -> 실행되고 있는 프로세스중 아파치라는 이름이 포함된 프로세스만 가져온다.
          
 ---

# IO_Redirection

###    - OutPut
          ls -l > result.txt -> ls -l 의 내용을 result.txt에 저장한다.
          > 기호는 아웃풋 리다렉이션을 의미하는 기호이다.
          
          rm rename2.txt > result.txt -> 파일이 없다는 전제하에 실행하면 
          result.txt에 에러메시지가 저장되지않고 콘솔에 나타난다. 즉 리타이렉션 되지 않는다.
          이는 > standard output만 리다이렉션하기 때문이다. 
          [ 1> == standard ] 를 의미한다. 에러메시지를 저장하고 싶으면 
          [ rm rename2.txt 2> result.txt ]  와 같은 형식으로 > 리다이렉션 기호앞에 2를 붙여주면 된다.

          rm test.txt 1> result.txt 2> error.log -> 스탠다드 아웃풋 과 스탠다드 에러 리다이렉션을 붙여서 사용할 수도 있다.
          
          ls -al >> result.xt -> append되어서 기존의 데이터에 추가된다.
          >> 리다이렉션을 하는데 리다이렉션하는 내용을 append한다

          ls -al > /dev/null	->  /dev/null 은 유닉스계열에서 쓰레기통과 같은 역할을 한다.

###    - InPut
          cat < hello.txt -> hello.txt에 저장되어 있는 내용을 입력으로 받는다.
          cat hello.txt -> 위와 결과는 동일하나 동작은 다르다.
          
          
---

# SHELL

###    - 기초이론
          hardware > kernel > shell > application

          echo "hello" -> echo는 뒤에들어오는 문자를 화면에 출력하는 명령어이다.
          echo $0	->  사용하는 쉘의 종료를 확인하는 명령어	ex) -bash , -zsh 등등으로 나올 것이다.

          -bash 와 -zsh는 부모가 같아 동작하는 기능이 비슷하다. 다만 zsh는 bash의 확장판 정도라고 생각하며 되며,
          추가적인 기능을 사용할 수 있다.
          
---

# SHELL_Script 

###    - 정의
          명령어들을 한번에 실행할 수 있는 하나의 각본이라고 볼 수 있다.

###    - 예제
          
```
          #!/bin/bash	-> 현재 쉘스크립트를 실행시켰을때 보는 첫줄(무조건 적는 약속) bin 밑에 있는 bash라는 프로그램으로 실행된다는 의미

          if ! [ -d bak ]; then		-> 현재 디렉토리에 bak 디렉토리가 존재안하는지 여부 체크
	     mkdir bak	-> 없으면 bak디렉토리를 만든다.
          fi			-> 조건문의 종료 fi

          cp *.log bak		-> 현재 디렉토리에 log 파일들을 bak 디렉토리에 저장한다.


          ./backup		-> 현재 디렉토리에 backup이라는 파일을 실행시킨다.	./ -> 현재 디렉토리라는 의미
```
---

# background 

###    - 정의
	 리눅스 내에서 하나의 프로그램이 아닌 여러 프로그램을 실행하기 위해서 필요하다.

###    - jobs
	 현재 백그라운드 내에서 실행중인 프로그램들을 보여준다. 명령어 사용시 아래와 같이 나타난다.
	 [1]	Stopped		test1
	 [2]-	Stopped		test2
	 [3]+	Stopped		test3
	 
	 + 는 fg 명령어를 옵션없이 사용시 나타나는 다음 프로그램이다. 
	 
	 
###    - ctrl + z
	 현재 실행중인 프로그램을 백그라운드로 보낸다.
	 
###    - fg %1
	 백그라운드에 있는 프로그램을 다시 그라운드로 올린다.
	 %뒤에 숫자는 stopped 앞에 붙은 숫자이며 해당 숫자 프로그램이 그라운드로 올라온다.
	 
###    - kill %1
	 현재 실행중인 백그라운드 프로그램을 종료시킬 때 사용하게 되는 명령어이다.
	 % 기호로 명시적으로 종료하고 싶은 프로그램을 나타내는 것이 꼭 필요하다.
	 
---
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	 
	
