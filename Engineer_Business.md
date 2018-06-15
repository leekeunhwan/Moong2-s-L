# Fastcampus Frontend Dev SCHOOL

## Client Requirements - 미팅 로그

블록체인 거래소를 만들고 싶어한다.

<br>
<br>

질문할 것들!

- 희망 거래소의 형태는 탈중앙화인지 중앙화인지 궁금합니다. - 보안이 우선 (탈중앙화 형식)
  (중앙화는 직접 편리하게 코빗, 빗썸처럼 한번에 구매자들이 간편히 구매, 하지만 보안이 약함, 해킹시 파산각)
  (탈중앙화는 유저가 직접 키값을 관리하여 구매, 전송시 키값을 입력해야함, 해외의 폴로닉스 방식, 해킹시에도 크게 지장이 없을 수도 있음)

- 시세의 변동사항을 시각화 처리 해야하는데 어떤 방식으로 하시고 싶은지? (예를 들어 막대 그래프, 선 그래프등...) 그리고 변동 주기를 어떻게 할 것인지 - crypt 그래프처럼

- 봐두신 레퍼런스가 있는지 - [후오비 : 단순하면서도 깔끔한 우아한]

- 타 블록체인 거래소 보다 안전하게 이용할 수 있도록 대체 형식

- 지갑을 생성해서 전송에 대해서 노터치, 전송간에 수수료는 안받는다.

- 리액트를 썼으면 좋겠다.

- 핸드폰으로도 접속

- 비로그인을 해도 - 크립토 처럼 보여주되 시세정보만 메이저급 코인으로만 보여주기 (CI, 코인명(축약형, 기준통화, 변동률)

- 아이디 10~20

- 이메일 input 창에 유효성 validate 필요

- 보안이 좋아야 하니까 SQL 인젝션, XSS 도 다 방어해야하고

- 비밀번호 -> 20 자리 넘게, 강려크하게

- 세션만료 : 20 분 이상 아무 요청이 없을 경우 로그인되게 (전체적용), OTP 추가

- 순간 동시 접속자 1 초에 2 만명, 가입자수 1 억명 - 비즈니스 요구사항 (잠재적 사용자 / 안전성 vs 확장성)

해보면서 느낀 점 : 생각보다 질문을 해야할 것들이 많았고, 질문이 나에게 독이 될지 득이 될지 잘 감이 안왔다.

<br/>
<br/>

## git, Software Engineering

---

<!--
page_number: true
$size: A4
footer : fastcampus Frontend Dev SCHOOL, Wooyoung Choi, 2018
-->

## Requirements Analysis

---

## Requirements Layer

<img src="./image/layer.png">

---

## Business Requirements

> "Why"

---

## Functional Requirements

> "What"

---

## User Requirements

> "What"

---

## Software Development Lifecycle Process Model

---

## Build-fix Model

![](http://image.slidesharecdn.com/lecture3-softwareprocessmodel-141029064743-conversion-gate02/95/lecture-3-software-process-model-4-638.jpg?cb=1414565646)

---

## Build-fix Model

설계없이 일단 개발, 만족할 때까지 수정

시작이 빠름

계획이 정확하지 않음, 개발 문서가 없고 진행상황 파악이 힘듦

---

## Waterfall Model

![](http://1.bp.blogspot.com/-gxj9EEmaKCc/UXfs6d3D2ZI/AAAAAAAAAzI/dRepueNwWK0/s1600/waterfall-model-sdlc1.jpg)

---

## Waterfall Model

순차적인 개발 모델, 가장 많이 사용됨

정형화된 접근 가능, 체계적인 문서화 가능

직전 단계가 완료되어야 진행 가능

---

## Prototype Model

![](http://shopeemart.weebly.com/uploads/2/9/5/1/29516595/8755334_orig.jpg)

---

## Prototype Model

고객 요구사항을 적극적으로 반영하는 모델

빠른 개발과 고객 피드백을 빠르게 반영할 수 있음

중,대규모 프로젝트에 적용하기 힘듦

---

## Spiral Model

![](http://leansoftwareengineering.com/wp-content/uploads/2008/05/spiral_model_boehm_1988.png)

---

## Spiral Model

대규모 or 고비용 프로젝트

프로젝트의 위험요인을 제거해 나갈 수 있음

각 단계가 명확하지 않음

---

## 이외에도..

- RAD(Rapid Application Development) Model
- Iterative Development Model
- V Model
- Component Based Development

---

## Software Development Process

in Agile

### UP(Unified Process)

- 도입(분석위주), 상세(설계위주), 구축(구현위주), 이행(최종 릴리즈)의 반복

### XP(eXtreme Process)

- 스크럼 마스터가 주도적으로 프로세스를 주도하며, 고객과 개발자 사이의 소통을 중시함
- Product Owner 와 Development Team, Customer 로 롤을 구분하고 각자의 역할에 충실
- TDD 중시 (기능을 테스트할 목적의 코드를 먼저짜고 본 코드를 짜는 것 - 습관을 들여야 한다.)

---

## TDD

### Test Driven Development

- 객체지향적
- 재설계 시간 단축
- 디버깅 시간 단축
- 애자일과의 시너지(사용자 중심적)
- 테스트 문서 대체
- 추가 구현 용이

### TDD 체험 - 계산기 테스팅 코드 작성

```js
class Calculator {
  constructor(num1, num2) {
    this._num1 = num1;
    this._num2 = num2;
  }

  summationTest() {
    return this._num1 + this._num2;
  }
  multiplyTest() {
    return this._num1 * this._num2;
  }
  differenceTest() {
    return this._num1 - this._num2;
  }
  devideTest() {
    return this._num1 / this._num2;
  }
}

function typeError(num1, num2) {
  const cal = new Calculator(num1, num2);
  if (Number.isInteger(num1) && Number.isInteger(num2)) {
    console.log("타입 에러 테스트");
    console.log(`덧셈의 결과는 ${cal.summationTest(num1, num2)}`);
    console.log(`곱셈의 결과는 ${cal.multiplyTest(num1, num2)}`);
    console.log(`뺄셈의 결과는 ${cal.differenceTest(num1, num2)}`);
    console.log(`나눗셈의 결과는 ${cal.devideTest(num1, num2)}`);
    console.log(`아무 문제 없습니다.`);
  } else {
    console.log("type error occured");
  }
}

function normalType(num1, num2) {
  const cal = new Calculator(num1, num2);
  console.log("정상 테스트");
  console.log(`덧셈의 결과는 ${cal.summationTest(num1, num2)}`);
  console.log(`곱셈의 결과는 ${cal.multiplyTest(num1, num2)}`);
  console.log(`뺄셈의 결과는 ${cal.differenceTest(num1, num2)}`);
  console.log(`나눗셈의 결과는 ${cal.devideTest(num1, num2)}`);
}

typeError(5, 2);
console.log(" ");
normalType(5, 2);
```

---

## Software Release Life Cycle

초기 개발단계부터 마지막 출시까지 주기를 나타냄

---

## Testing and development period

### Pre-alpha (개발 초기~중기)

- 테스트 이전까지 진행되는 요구사항 분석, 설계, 개발, 유닛 테스트를 포함
- 핵심 기능이 동작하기 시작한 상태

### Alpha (어느정도 개발이 된 시점)

- 소프트웨어 테스트를 시작하는 첫 단계
- 회사 내부 테스터를 통해 진행하며, 피드백을 통해 소프트웨어를 개선함

---

### Beta (유저들이 참여 - 리포트를 준다.)

- 외부에 직,간접으로 오픈하여 테스트를 진행
- 오픈 베타: 일반 유저에 모두 오픈하여 기능을 제공함.
- 클로즈드 베타: 신청자 중 일부에 접근권한을 부여하고, 테스트를 진행함. (일부 유저에게 선공개 - 주로 매니아틱한 유저들에게 많이 부여)

### RC(Release Candidate)

- 정식 제품이 될 가능성이 있는 베타버전. 심각한 문제가 없다면 이들 중 하나가 정식 버전이 됨.

---

## Release period

### RTM(Release to Manufacturing)

- 소프트웨어를 유저에게 제공될 준비가 완료된 상태

### GA(General Availability)

- 소프트웨어를 유저가 이용 가능한 상태

### 배포단계에서 에러가 날 수 있는 경우

모두 다 같은 환경에서 작업을 하는 것이 아니므로 환경에 대한 문제가 생길 수 있다.

---

## Agile Process

---

## Scrum

- an iterative and incremental agile software development framework for managing product development

---

## Scrum

- The **product owner** represents the stakeholders and is the voice of the customer, who is accountable for ensuring that the team delivers value to the business.(돈을 주는 사람)
- The **development team** is responsible for delivering potentially shippable increments (PSIs) of product at the end of each sprint (the sprint goal).(나)
- facilitated by a **scrum master**, who is accountable for removing impediments to the ability of the team to deliver the product goals and deliverables

---

## Sprint

![](https://upload.wikimedia.org/wikipedia/commons/thumb/5/58/Scrum_process.svg/700px-Scrum_process.svg.png)

product backlog (기능 단위 별로 나누기)<br>
sprint backlog (세분화)<br>
sprint (가공)<br>
-> 제품 완성<br>

---

## Planning Poker

- 애자일 추정을 위해 사용하는 도구
- 모든 팀원이 한가지 과제에 대해 충분히 토론하고 작업시간을 추정하기 위함
- deck 구성
  0, 1/2, 1, 2, 3, 5, 8, 13, 20, 40, 100, ?, 무한대, 커피

- 점수는 단위 작업시간(8 시간)을 의미함

---

## Planning Poker

- 플레이방법 1. 추정할 과제를 가장 잘 아는 사람이 해당 과제에 대해 설명합니다. 2. 다른 사람은 추정에 필요한 정보를 얻기위해 질문과 토의를 합니다. 3. 각자 생각하는 이 과제의 점수를 보이지 않게 내려놓습니다. 4. 점수를 공유하고 가장 낮은 점수, 가장 높은 점수를 낸 팀원이 이 점수를 낸 이유에 대해 설명합니다. 5. 모든 팀원이 같은 점수를 낼 때 까지 3~4 의 반복

---

## 일정 추정 과제

1.  은행 예금 계좌 및 체크카드 발급절차
2.  Fizzbuzz(조건문 반복문으로, map, filter 로)
3.  Profile Porfolio Page

ex)
회차 최소 최대 중간값
1 1 10 5
2 4 8 6
3 5 5 5

---

## Pair Programming

---

## Pair Programming

- 시니어와 주니어가 한 팀을 이뤄 노하우를 전수하거나 같은 과제에 대해 충분한 논의를 함으로써 생산성 향상을 도모
- Navigator 와 Driver 가 한 팀을 이뤄 실시
- Navigator 는 해당 과제에 대해 주도적으로 의견을 제시하고 Driver 는 Navigator 가 지시하는 대로 작업하되, 이해되지 않는 부분이 있다면 이의를 제기
- 약속한 시간이 지나면 Navigator 와 Driver 의 역할 변경
- 과제를 해결할 때 까지 반복

---

## Pair Programming

### So, Let's Try!!

### fizzbuzz 실습

```js
// 반복문

function fizzbuzz() {
  for (let i = 1; i <= 100; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
      console.log(`${i}는 fizzbuzz`);
    } else if (i % 5 === 0) {
      console.log(`${i}는 buzz`);
    } else if (i % 3 === 0) {
      console.log(`${i}는 fizz`);
    } else {
      console.log(`i는 ${i}`);
    }
  }
}

fizzbuzz();

// map

function mapFizzbuzz(n) {
  let arr = [];
  let result;
  for (let i = 1; i <= n; i++) {
    arr.push(i);
  }
  result = arr.map(
    item =>
      item % 15 === 0
        ? "FizzBuzz"
        : item % 5 === 0
          ? "Buzz"
          : item % 3 === 0
            ? "Fizz"
            : item
  );
  return result.join(" ");
}

mapFizzbuzz(100);

// map -2
function fizzbuzz(n) {
  return Array.from(Array(n + 1).keys())
    .slice(1)
    .map(i => (i % 3 ? "" : "fizz") + (i % 5 ? "" : "buzz") || i)
    .join("\n");
}

fizzbuzz(20);

// filter

function fizzbuzz(value) {
  if (value % 3 == 0 && value % 5 == 0) {
    console.log("fizzbuzz");
  } else if (value % 5 === 0) {
    console.log("buzz");
  } else if (value % 3 == 0) {
    console.log("fizz");
  } else {
    console.log(value);
  }
}
function mapFizzbuzz(n) {
  let arr = [];
  let result;
  for (let i = 1; i <= n; i++) {
    arr.push(i);
  }
  result = arr.filter(fizzbuzz);
  return result;
}

mapFizzbuzz(100);
```

---

## Code Review

검토사항

- 요구사항
- 설계요구 충족여부
- 과도한코딩
- 같은 기능
- 함수의 입출력
- 빌딩블록(API, 라이브러리, 자료구조, ..)
- 변수 사용전 초기화

---

## 개발자가 오프라인에서 살아가는 법

---

## Communicate with Co-worker

---

### 상대를 아프게 하지 마세요

---

### 작은 것을 칭찬하세요

---

### 회사는 개발자만 존재하지 않아요

---

<img src="./image/communicate.png">

---

### How 를 생각하기 전 What 과 Why 를 먼저 생각하세요

---

### `404` 보단 `404 - Not Found`

### `안되요` 보단 `시스템에 악영향을 줄 가능성이 있어 다른 방법을 고려하는 것이 좋을 것 같습니다.`

---

## 개발자가 관리해야 할 것

- github
- linkedin
- blog

---

## 개발자가 갖춰야 할 덕목

---

### Geekiness

![](http://www.arghink.com/wp-content/uploads/2015/06/geek_wallpaper____by_bigteddyrawr-d5us99o.png)

---

### Curiosity

![](https://c1.staticflickr.com/9/8205/8162305237_7c5fe5aa8a_b.jpg)

---

### Computational Thinking

![](https://upload.wikimedia.org/wikipedia/commons/1/17/ArtificialFictionBrain.png)

<link href="https://fonts.googleapis.com/css?family=Nanum+Gothic:400,800" rel="stylesheet">
<link rel='stylesheet' href='//cdn.jsdelivr.net/npm/hack-font@3.3.0/build/web/hack-subset.css'>

<style>
h1,h2,h3,h4,h5,h6,
p,li, dd {
font-family: 'Nanum Gothic', Gothic;
}
span, pre {
font-family: Hack, monospace;
}
</style>
