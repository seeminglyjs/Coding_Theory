# JavaScript
- [DOM 트리](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#DOM_Tree)
- [let 과 const를 사용하는 이유](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#let_const)
- [async 와 await 알아보기 ](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#async/await)
- [$(document).ready() 와 $(window).load() 의 차이](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#document_ready/window_load)
- [CDN 이란?](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#CDN)
- [객체리터럴](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#객체리터럴)
- [null은 원시자료형인가?](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#null이란?)
- [같은 클래스에 서로다른 문자열 넣기](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#each활용법)
- [동일 객체를 복사하는 방법](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#동일한_객체_복사_하는_방법)
- [배열 메소드](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#배열_메소드)
- [블록 스코프](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#블록_스코프)
- [함수 스코프](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#함수_스코프)
- [스코프와 컨텍스트](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#스코프와_컨텍스트)
- [이벤트 핸들러(event handler)](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#event_handler)
- [Closure](https://github.com/seeminglyjs/Coding_Theory/edit/main/JavaScript/#Closure)
---
# DOM_Tree

###    - 정의
     
	DOM(Document Object Model)은 웹 페이지에 대한 인터페이스입니다. 
	기본적으로 여러 프로그램들이 페이지의 콘텐츠 및 구조, 
	그리고 스타일을 읽고 조작할 수 있도록 API를 제공합니다. 

---    

# let_const

###    - 정의
     
	let, const를 사용하면 var를 사용할때보다 상당히 이점이 많다.
	두개의 공통점은 var와 다르게 변수 재선언 불가능이다.

	let과 const의 차이점은 변수의 immutable여부이다.
	let은 변수에 재할당이 가능하지만,
	const는 변수 재선언, 재할당 모두 불가능하다.
	(const는 자바의 final과 비슷하다)


	// 가능
	let a;
	a = 10;

	//불가능
	const a;
	a = 10


	//가능 (const는 선언과 동시에 값을 넣어주어야 한다.)
	const a = 10;

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
 
# 객체리터럴

###   -정의 및 코드
      
	//빈객체를 생성하는 방법
	const car = new Object();
	const car = {}; //<- 객체 리터럴

	//객체 리터럴의 값 할당
	car.color = "red";
	console.log(car.color) // red 점표기법
	console.log(car.['color']) // red 대괄호표기법
	console.log(car.[변수명]) // red 대괄호표기법

	//점표기법은 두단어 이상으로 이루어져 있으면 사용할 수 없다.
            
 ---


# null이란?

###   -null 은 원시 자료형인가?
      
	null은 원시 자료형이지만 
	typeof를 사용하면 object로 나온다
	그 이유는 버그다..
            
 ---
      
# each활용법

###   -같은 클래스에 서로다른 텍스트 넣는법

	let texts =["abc1", "abc2", "abc3" ]


	$(".div").each(function(index)){
		$(this).eq(index).text(texts[index])

	}).
            
 ---
 
# 동일한_객체_복사_하는_방법

###   -코드

	const car = {
	color: 'red',
	};


	const secondcar = Object.assign({}, car);
	car.wheels =4;
	console.log(car)
	//{color : 'red', wheels : 4 }
	console.log(secondcar)
	//{color : 'red'}

	이렇게 하면 car의 내용을 변경해도 secondcar에는 영향을 주지 않는다.
            
 ---
 
# 배열_메소드

###   -코드

	const test1 = ['hi', 'hello', 'hello2']

	test1.push('hello3')
	//맨뒤 인덱스에 hello3를 추가한다.
	//['hi', 'hello', 'hello2','hello3']


	test1.unshift('hi0')
	//맨앞 인덱스에 'hi0'를 추가한다.
	//['hi0', 'hi', 'hello', 'hello2','hello3']

	test1.pop()
	//맨뒤 인덱스를 제거한다.
	//['hi0', 'hi', 'hello', 'hello2']
	

	test1.shift()
	//맨앞 인덱스 하나 제거
	//['hi', 'hello', 'hello2']
            
 ---
 
# 블록_스코프

###   -정의

	함수 스코프가 함수 생성시마다 새로운 스코프가 생성되는 것을 의미한다면, 
	블록 스코프는 말 그대로 블록 {}이 생성될 때마다 
	새로운 스코프가 형성되는 것을 의미한다. 
	원래 자바스크립트는 함수 스코프를 따르지만, 
	let과 const 키워드의 등장으로 블록 스코프를 형성하는 것도 가능해졌다.
            
 ---

# 함수_스코프

###   -정의

	function a() {
  	var secret = '12345'; 
	}
	secret; // ReferenceError
 

	함수를 만들고, 그 안에 변수를 저장하면, 
	이 경우 함수 생성과 동시에 함수에 대한 	새로운 실행 컨텍스트가 생성이 되고, 
	이 실행 컨텍스트 내부에 존재하는 
	변수 환경(variable environment)에 변수가 저장된다. 

	따라서 함수 외부에서 함수내부 변수에 접근하려고 할 경우 
	스코프가 다르기 때문에 해당 변수에 접근이 불가능하다.
	(함수 외부는 global scope이고, 
	함수 내부는 a 함수의 scope인데, 
	부모 스코프는 자식 스코프에게 
	간섭할 수가 없기 때문에 접근이 불가능한 것이다.)
            
 ---
 
# 스코프와 컨텍스트

###   -스코프(scope)

	함수가 실행될 때, 
	함수 내에서 변수에 대한 접근이 어떻게 되는지를 나타내는 용어이다.
	(함수의 실행 컨텍스트 내에서의 변수 환경이 무엇인지) 
	스코프는 함수를 기반으로 한 용어이다.

###   -컨텍스트(context) 

	this 키워드의 값이 무엇인지를 나타내는 용어이다. 
	현재 실행 컨텍스트 내에서 어떤 객체를 참조하고 있는지를 의미한다. 
	컨텍스트는 객체를 기반으로 한 용어이다.           
 ---
 
 # 스코프와 컨텍스트

###   -정의와 코드
	
	특정 요소에서 발생하는 이벤트를 처리하기 위해서는 
	이벤트 핸들러(event handler)라는 함수를 작성하여 연결해야만 합니다.

	이벤트 핸들러가 연결된 특정 요소에서 지정된 타입의 이벤트가 발생하면, 
	웹 브라우저는 연결된 이벤트 핸들러를 실행합니다.


	$(function() {

	    $("button").on({             // 모든 <button>요소에

		mouseenter: function() { // mouseenter 이벤트를 설정함.

		    $("#text").append("마우스가 버튼 위로 진입했어요!<br>");

		},

		click: function() {      // click 이벤트를 설정함.

		    $("#text").append("마우스가 버튼을 클릭했어요!<br>");

		},

		mouseleave: function() { // mouseleave 이벤트를 설정함.

		    $("#text").append("마우스가 버튼 위에서 빠져나갔어요!<br>");

		}

	    });

	});   
 ---
 
# Closure

###   -정의

	Closure(클로저)는 두 개의 함수로 만들어진 객체의 한 종류이며, 
	내부 함수가 익명 함수로 되어 외부 함수의 반환값으로 사용됩니다.

	이 클로저를 통해서 자바스크립트에는 없는 
	비공개(private) 속성/메소드, 
	공개 속성/메소드를 구현할 수 있는 방안을 마련할 수 있다.
	
###	-클로저 생성하기
		다음은 클로저가 생성되는 조건이다.

		내부 함수가 익명 함수로 되어 외부 함수의 반환값으로 사용된다.
		내부 함수는 외부 함수의 실행 환경(execution environment)에서 실행된다.
		내부 함수에서 사용되는 변수 x 는 외부 함수의 변수 스코프에 있다.


	function outer() {
	  var name = `closure`;
	  function inner() {
	    console.log(name);
	  }
	  inner();
	}
	outer();
	// console> closure

	outer함수를 실행시키는 context에는 name이라는 변수가 존재하지 않는다는 것을 확인할 수 있다. 비슷한 맥락에서 코드를 조금 변경해볼 수 있다.

	-----------------------------------------------------------
	var name = `Warning`;
	function outer() {
	  var name = `closure`;
	  return function inner() {
	    console.log(name);
	  };
	}

	var callFunc = outer();
	callFunc();
	// console> closure
	위 코드에서 callFunc를 클로저라고 한다. callFunc 호출에 의해 name이라는 값이 console 에 찍히는데, 
	찍히는 값은 Warning이 아니라 closure라는 값이다. 즉, outer 함수의 context 에 속해있는 변수를 참조하는 것이다. 
	여기서 outer함수의 지역변수로 존재하는 name변수를 free variable(자유변수)라고 한다.

	이처럼 외부 함수 호출이 종료되더라도 외부 함수의 지역 변수 및 변수 스코프 객체의 체인 관계를 유지할 수 있는 구조를 클로저라고 한다. 
	보다 정확히는 외부 함수에 의해 반환되는 내부 함수를 가리키는 말이다.

	Reference
	TOAST meetup - 자바스크립트의 스코프와 클로저


	-------------추가 예제-------------------------------------------------

	다음은 조금 더 흥미로운 예제인 makeAdder 함수이다:

	function makeAdder(x) {
	  var y = 1;
	  return function(z) {
	    y = 100;
	    return x + y + z;
	  };
	}

	var add5 = makeAdder(5);
	var add10 = makeAdder(10);
	//클로저에 x와 y의 환경이 저장됨

	console.log(add5(2));  // 107 (x:5 + y:100 + z:2)
	console.log(add10(2)); // 112 (x:10 + y:100 + z:2)
	//함수 실행 시 클로저에 저장된 x, y값에 접근하여 값을 계산

	이 예제에서 단일 인자 x를 받아서 새 함수를 반환하는 함수 makeAdder(x)를 정의했다. 반환되는 함수는 단일 인자 z를 받아서 x와 y와 z의 합을 반환한다.

	본질적으로 makeAdder는 함수를 만들어내는 공장이다. 
	이는 makeAdder함수가 특정한 값을 인자로 가질 수 있는 함수들을 리턴한다는 것을 의미한다. 
	위의 예제에서 add5, add10 두 개의 새로운 함수들을 만들기 위해 makeAdder함수 공장을 사용했다. 
	하나는 매개변수 x에 5를 더하고 다른 하나는 매개변수 x에 10을 더한다.

	add5와 add10은 둘 다 클로저이다. 이들은 같은 함수 본문 정의를 공유하지만 서로 다른 맥락(어휘)적 환경을 저장한다. 
	함수 실행 시 add5의 맥락적 환경에서 클로저 내부의 x는 5 이지만 add10의 맥락적 환경에서 x는 10이다. 
	또한 리턴되는 함수에서 초기값이 1로 할당된 y에 접근하여 y값을 100으로 변경한 것을 볼 수 있다. 
	(물론 x값도 동일하게 변경 가능하다.) 
	이는 클로저가 리턴된 후에도 외부함수의 변수들에 접근 가능하다는 것을 보여주는 포인트이며 
	클로저에 단순히 값 형태로 전달되는 것이 아니라는 것을 의미한다.


	-------------추가 예제-------------------------------------------------

	클로저를 이용해서 프라이빗 메소드 (private method) 흉내내기
	자바와 같은 몇몇 언어들은 메소드를 프라이빗으로 선언할 수 있는 기능을 제공한다. 
	이는 같은 클래스 내부의 다른 메소드에서만 그 메소드들을 호출할 수 있다는 의미이다.

	자바스크립트는 태생적으로는 이런 방법을 제공하지 않지만 클로저를 이용하여 프라이빗 메소드를 흉내내는 것이 가능하다. 
	프라이빗 메소드는 코드에 제한적인 접근만을 허용한다는 점 뿐만 아니라 전역 네임 스페이스를 관리하는 강력한 방법을 제공하여 
	불필요한 메소드가 공용 인터페이스를 혼란스럽게 만들지 않도록 한다.

	아래 코드는 프라이빗 함수와 변수에 접근하는 퍼블릭 함수를 정의하기 위해 클로저를 사용하는 방법을 보여준다. 
	이렇게 클로저를 사용하는 것을 모듈 패턴이라 한다.

	var counter = (function() {
	  var privateCounter = 0;
	  function changeBy(val) {
	    privateCounter += val;
	  }
	  return {
	    increment: function() {
	      changeBy(1);
	    },
	    decrement: function() {
	      changeBy(-1);
	    },
	    value: function() {
	      return privateCounter;
	    }
	  };
	})();

	console.log(counter.value()); // logs 0
	counter.increment();
	counter.increment();
	console.log(counter.value()); // logs 2
	counter.decrement();
	console.log(counter.value()); // logs 1
