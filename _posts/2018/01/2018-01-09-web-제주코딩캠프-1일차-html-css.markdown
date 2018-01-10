---
layout: "post"
title: "[Web] 제주코딩캠프 1일차 - HTML / CSS"
date: "2018-01-09 08:43"
category: Web
tags: HTML CSS Python CodingCamp Django Javascript
---

## Background
1월 8일 월요일부터 시작하여 1월 13일까지 제주도에서 진행되는 장고 웹개발 캠프에 참가할 수 있는 기회를 잡아 오랜만에 집에서 가족들 얼굴도 보고 웹 개발 공부의 기초부터 다시한번 복습하고 또한 모르는 부분들은 다시 알아나가는 시간을 갖게 되었습니다.

캠프는 제주도 제주시에서 진행되어쏙 약 13~16명의 인원으로 구성되어 이호준 바울랩아이씨티 연구소 대표님과 '오후코드'로 유명하신 김대현 개발자님, 페이스북에서 '1분코딩'을 진행하시는 유준모 개발자님을 강사로 진행합니다.

일주일 간의 강의 커리큘럼은 HTML, CSS, JS 를 시작으로 개발자도구, 홈페이지 기획과정 그리고 파이썬과 장고 프레임워크를 단시간 내에 배우고 나서 마지막 일정으로 반나절간 해커톤을 진행하는 방식으로 구성되어 있습니다.

캠프의 참석하는 사람들은 각각 다양한 배경과 이유를 가지고 이 캠프에 참석을 하였습니다. 각자 배우는 목적과 깊이는 다를 수 있겠지만, 그 다름을 통해서 다른사람들의 생각을 들어보고 공감하거나 새로운 관점으로 살펴 볼 수 있는 시간이 될 것 같습니다.

강의 내용은 간단히 개발노트에 짤막하게 기억해야 될 만한 것들을 정리한 필기를 복습차원을 위해 남기겠습니다.

---

## Study

### 오전
- `www.naver.com`과 통신하기 위한 정보
  - 이름 : URL, 도메인
  - 주소 : IP
  - 문 : 포트
- 웹 애플리케이션은 `Client`<->`Internet`<->`DNS`<->`Internet`<->`Server`의 기본 구조로 통신을 한다
- 홈페이지 기획을 할 때 유용한 툴
  - [Oven](http://ovenapp.io) : 마우스, 드래그를 이용한 간단한 프로토타이핑
  - HTML의 구조를 보기위한 Dummy Text 만들기
    - [한글 입숨](http://hangul.thefron.me/)
    - [영문 입숨](https://loremipsumgenerator.com/)

### 오후
- 스튜디오밀 유준모 개발자님 강의
- HTML
  - 시맨틱 태그는 한 페이지에 각 요소가 무조건 한번씩 사용되는 것이 아닌, 내용에 따라 여러번 사용되기도 한다.
  - `viewport`는 모바일환경과 대응할 때, 유용하게 사용된다. 모바일 환경이 실제로는 더 높은 필셀을 가지고 있을 경우, 디자인된 페이지의 픽셀을 기본으로 비율을 맞추어준다. (예를 들면, 스마트폰이 실제 1024픽셀이지만 모바일웹이 375픽셀로 나오면 1024픽셀을 375픽셀 처럼 동작하도록 만든다.)
  - Conditional Comment
    - `<!--[If lt IE9]> code <![endif]-->`
    - 조건의 경우를 만족할 경우 실행


- CSS
  - id태그 선택자는 문서 내에 단 한번 사용 가능하기 때문에 class 선택자에 비해 조금 빠른 렌더링이 가능하다는 장점이 있으나, class 선택자를 주로사용하는 것이 보편적이다.
  - 기본적인 box-sizing에서 width, height속성은 border, padding, margin이 포함되어 계산되는 것이 아니기 때문에, 100%를 설정하면 스크롤이 생길 수 있다.
  - `http://caniuse.com`에서 다양한 웹 브라우저 별로 특정 CSS속성의 지원여부를 알 수 있다.
  - ResetCSS
    - 웹 브라우저는 기본적으로 `<h1>`태그가 큰 글씨와 두꺼운 필체를 가지고 있듯, 속성이 기본적으로 설정되어 있다.
    - 개발의 편의를 위해 미리 정의된 혹은 직접 제작한 ResetCSS를 통해 모든 CSS속성들을 초기화한다.
      - [에릭마이어의 ResetCSS](http://meyerweb.com/eric/tools/css/reset/)
      - [Normalize.css](https://necolas.github.io/normalize.css/)
  - CSS를 적용할 요소를 선택한 후 속성들을 정의할 때, 속성들의 순서는 개인의 차이이지만 큰 것에서부터 작은것으로 내려가면 보기 좋다.
  - `display: inline`이 적용된 요소들을 생각할 때에는 baseline을 염두해둔다, 이것에 맞추어 정렬이되기 때문이다.
  - `float`속성을 사용하면 `clear`가 필요하다
    - 그렇지 않으면 자식 요소가 다 떠있기 때문에 부모요소의 높이가 0이 되는 경우가 있다.
    - 가상엘리먼트 `::after`를 이용하여 부모 요소가 끝날때, 붙인다.
  - `@media`, 미디어 쿼리를 이용하여 mobile first 형태를 취하여 프론트 개발을 하는것이 이상적이다. 하지만 클라이언트의 요구에 따라 달라질 수 있다.
  - z-index는 설정할때, 중간 값을 여유롭게 하여 나중에 있을 추가에 대비한다.
  - relative 속성은 static 기준의 위치를 기준으로 움직인다.
  - `position: fixed`로 정의될 때에는 width 속성을 정의해야 한다.
  - `position: absolute or fixed` 요소를 이용하여 애니매이션 효과를 사용할때 다른 값들 보다 렌더링이 빠르다.
  - `display: flex`는 레이아웃 잡을때 유용하게 사용된다.
    - `block`처럼 부모요소가 width 100%이다.
    - `inline-flex`는 inline 요소처럼 컨텐츠 길이에 맞추어 width가 줄어든다.
    - 참고 `display: grid`
  - `flex-direction` 배치의 축을 결정한다. 꼬치구이처럼 생각한다. row 는 가로로 꽂혀진 꼬치, column은 세로로 꽂혀진 꼬치와 같이 내용물을 쌓는다
  - `flex-wrap`은 내용이 기본이 `nowrap`으로 내용이 넘칠때 어떻게 할지 정의한다.
    - `wrap`: 밑으로 순서대로 내린다.
    - `wrap-reverse`: 반대로 순서로 내린다.
  - `flex-flow`는 `flex-directon`과 `flex-wrap`설정을 동시에 설정할 수 있다.
  - `justify-content`
    - `space-between` : 요소 사이에 일정한 간격을 넣어 정렬, 양쪽 끝 여백 없음
    - `space-around` : 양쪽끝에도 일정 여백을 만들고 사이사이 빈공간 일정하게 정렬
    - `flex-start` : 기본값 한쪽부터 쌓아나갑니다.
    - `flex-end` : start와 반대 방향에서부터 정렬
    - `center` : 가운데로 정렬
  - `align-items`는 `justify-content`는 메인축에 방향의 정렬이라면, 이것은 메인축에 수직인 정렬이다.
    - 값은 `justify-content`와 같습니다.
  - `flex-grow`는 자식요소에 추가하여 공간을 나누어 갖는 비율을 설정한다.
  - `flex-basis`는 `flex-grow`로 나누는 비율 조절에 도움을 준다.
  - `flex: x x x` 각각 grow, shrink, basis 설정을 한다.
    - `flex: 1` 설정을 하면 컨텐츠 길이에 상관없이 일정 비율로 나누어가진다.
  - `order` 숫자를 지정해주어 숫자가 큰 요소가 뒤로간다.

- JavaScript
  - 자바스크립트에서 전역변수의 사용을 지양한다.
    - 파일이 다른곳에 있어도 공유가 되기 때문이다.
    - 이 변수에는 상태를 담는 경우가 많다, 이는 많이 사용되기 때문에 해당 변수를 전역변수가 아닌상태로 활용하기위해 함수로 감싸 이용한다.
      ```javascript
      (function (){
        //code
        var global_variable = 0;

        function foo(){
          global_variable++
        }
      })();
      ```
  - `this`는 해당 메서드를 실행한 객체를 가리킨다. 다음과 같은 상황에서는 clickHandler를 호출한 element객체가 this가 가리키는 객체가 된다.  

    ```javascript  
    var element = document.querySelector(#foo);

    function clickHandler(e){
      // code
      console.log(this);
    }
    element.addEventListener('click', clickHandler);
    ```
  - `var`를 붙이지 않고 변수를 정의하면 해당 변수는 전역변수가 되어 문제가 생긴다. 따라서 반드시 붙여서 정의하도록 한다.
  - `onclick`메서드 대신 `addEventListener`로 이벤트를 등록하는 것이 최신스펙이기 때문에 권장된다.
  - 성능을 염두해 두는 습관이 좋은 이유는, 기기가 소형화 되면서 성능이 낮아지는 경우 이런 작은 차이가 전체적인 성능에 큰 차이를 만들 수 있다.
  - `Event` 위임
    - 각각의 자식 요소들이 이벤트를 받아 처리하는 것이아닌, 상위 부모 요소가 이벤트 핸들러를 한가지 받아 `this` 의 내용을 토대로 이벤트를 등록할 수 있다.
    - 자식 요소가 많을 경우 for문을 돌면서 여러번 등록해야하는 오버로드를 줄일 수 있다.
  - event 동작을 취소
    - `e.preventDefault()`


---

## 참고
* 에버노트를 통해 블로그에 포스팅과 같은 작업을 가능하게 하는 프로그램이 있다. 개인적인 자료 저장용으로 사용하기에는 안성맞춤임
* 스팀잇이라는 SNS서비스가 있다. 발행하고, 글에 좋아요, 댓글과 같은 활동을 받으면 가상화폐로 보상을 받는다.(https://steemit.com/)


## Reference
* [제주코딩캠프](http://jejucodingcamp.com)
* [빔캠프 - CSS 채널](https://www.youtube.com/channel/UCvx57s_ZBt5VG4fvlStiq2g)
