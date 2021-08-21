# JavaScript
- [async 와 await 알아보기 ](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#async/await)
---
# ● async/await
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
   
