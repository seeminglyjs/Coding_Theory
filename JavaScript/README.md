# JavaScript
- [async 와 await 알아보기 ](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#async/await)
- [$(document).ready() 와 $(window).load() 의 차이](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#document_ready/window_load)
- [CDN 이란?](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#CDN)
---
# async/await
###    - 정의
     
      일반적으로 자바스크립트의 코드는 콜백 함수를 사용해서 실행순서를 보장받는 형식이다.
      비동기 함수로 만들려면 함수 앞에 async 키워드를 붙여야 한다.
      await는 async가 붙은 비동기 함수에서만 동작한다.
      await는 프로미스가 결고라르 반환할 때 까지 기다리도록 자바스크립트에 지시한다.
    
###    - 기본문법
      
      async function 함수명() {
      await 비동기_처리_메서드_명();
      }
    
###    - 특징 
      
      async를 사용하면 Promise를 반환한다.
      예외처리시 asyncFuc().catch(console.log) 와 같은 형식으로 처리할 수 있다.

---

# document_ready/window_load

###   -$(document).ready()
      
      외부 리소스. 이미지와는 상관 없이 브라우저가 
      DOM (document object model) 트리를 생성한 직후 실행

	window.load() 보다 더 빠르게 실행되고 
	중복 사용하여 실행해도 선언한 순서대로 실행됨

###   -$(window).load()
      
      DOM의 standard 이벤트

	html의 로딩이 끝난 후에 시작

	화면에 필요한 모든 요소(css, js, image, iframe etc..)들이 
	웹 브라우저 메모리에 모두 올려진 다음에 실행됨

	화면이 모두 그려진 다음의 메세징이나 
	이미지가 관련 요소가 모두 올려진 다음의 애니메이션에 적합함

	전체 페이지의 모든 외부 리소스와 이미지가 
	브러우저에 불려운 이후 작동하게 되어 
	이미지가 안뜨거가 딜레이가 생길 때에는 그만큼의 시간을 기다려야 함

	외부 링크나 파일 인크루트시 그 안에 window.load 스크립트가 있으면 둘 중 하나만 적용됨
      
 ---
      
# CDN

###   -정의
      
      웹 사이트의 접속자가 서버에서 콘텐츠를 다운받아야 할 때, 
	자동으로 가장 가까운 서버에서 다운받도록 하는 기술입니다.

	이 기술을 이용하면 특정 서버에 트래픽이 집중되지 않고, 
	콘텐츠 전송 시간이 매우 빨라지는 장점이 있습니다.

	이러한 CDN을 이용하면 제이쿼리 파일을 서버에 따로 저장하지 않아도 
	제이쿼리를 사용할 수 있습니다.
            
 ---
      
      
