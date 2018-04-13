# 1. Today I Learned

## JavaScript Array

---

## 배열

배열은 JS 에 내장되어 있는 자료구조입니다.<br/>
배열은 객체의 일종이지만, 내부적으로 특별하게 취급되어 일반적인 객체들과는 다른 특징을 갖고 있습니다.<br/>

```js
typeof []; //  'object'
```

배열 안에 들어있는 값들을 요소(element) 혹은 항목(item)이라고 합니다.<br/>

```js
let arr = [1, 2, 3, 4, 5];
```

객체와 배열의 가장 큰 차이점은 배열의 각 요소 간에는 순서가 있다는 점입니다.<br/>
배열은 `Array` 생성자의 인스턴스여서 배열의 프로토타입으로 `Array.prototype` 객체가 지정되어 있습니다.<br/>

<br/><br/>

## 배열 생성하기 - 배열 리터럴

배열은 배열 리터럴을 통해서 생성하는 것이 가장 쉽습니다.<br/>

```js
const empty = []; // 빈 배열
const numbers = [1, 2, 3, 4, 5]; // 숫자가 들어간 배열
const strings = ["가", "나", "다", "라"]; // 문자열이 들어간 배열
const objects = [{ prop: 1 }, { prop: 2 }, { prop: 3 }]; // 객체가 들어있는 배열
const anything = [1, "가", { prop: 3 }, true]; // 다양한 타입의 값들이 들어간 배열
```

<br/><br/>

## 배열 생성하기 - Array 생성자

`Array` 생성자를 이용하여 배열을 생성할 수 있습니다.<br/>
`Array` 생성자는 주어지는 인수에 따라 두 가지 서로 다른 방식으로 동작을 합니다.<br/>

```
1. 수 타입의 인수가 하나 주어질 때는 항상 수 만큼의 길이를 갖는 비어있는 배열을 만들어 냅니다.<br/>
   만약 인수가 양의 정수가 아니라면 에러를 냅니다.<br/>
2. 이 외에 다른 모양으로 인수가 주어지면 그 인수들을 요소로 갖는 배열을 생성합니다.<br/>
```

```js
new Array(1); //  [<1 empty item>]
new Array(1000); //  [<1000 empty item>]

new Array(1, 2, 3); //  [1,2,3]
```

<br/><br/>

## 배열 생성하기 - Array.of

일관적이지 못한 생성자의 동작방식 때문에 ES2015 에서 `Array.of` 정적 메소드가 추가되었습니다.<br/>
이 메소드는 위의 2 번 방식으로만 동작합니다.<br/>
따라서 Array 생성자를 사용할 때에는 1 번 방식만 쓰고,<br/>
2 번 방식의 코드를 작성할 때는 생성자 대신 Array.of 정적 메소드를 사용하도록 합니다.<br/>

```js
new Array(1, 2, 3); // [1,2,3] : 생성자는 이런 방식으로는 사용하지 않도록 합니다.
Array.of(1, 2, 3); // [1,2,3] : 가급적 Array.of로 하도록 합니다.

// Array.of 정적 메소드는 인수가 하나이더라도 그 인수를 요소로 갖는 배열을 갖습니다.
Array.of(1); //  [1]

// 생성자는 이런 용도로만 사용하도록 합니다.
new Array(1000); //  [<1000 empty item>]
```

<br/><br/>

## 배열 생성하기 - Array.form

JS 에서는 유사 배열 객체와 iterable 이라는 개념이 있어서, 이에 해당되는 값들은 Array.form 정적 메소드를 이용하여 쉽게 변환될 수 있습니다.<br/>

```js
//  'string' 타입은 래퍼 객체를 통해 iterable로 다루어질 수 있습니다.
Array.form("hello"); // ["h","e","l","l","o"]
```

<br/><br/>

## 요소 읽기

배열의 각 요소는 인덱스를 이용해 읽어올 수 있습니다.<br/>
인덱스는 객체의 속성 이름과 비슷한 역활을 하지만, 0 이상의 정수만이 배열의 인덱스가 될 수 있습니다.<br/>
배열을 생성하면 배열 안에 들어있는 각 요소는 순서대로 0 부터 시작하는 인덱스를 갖게 됩니다.<br/>
대괄호 표기법에 인덱스를 사용함으로써 원하는 요소를 가져올 수 있습니다.<br/>

```js
const arr = ["one", "two", "three"];

arr[0]; //  'one'
arr[1]; //  'two'
arr[2]; //  'three'
arr[3]; //  undefined
```

인덱스는 0 부터 시작하는 것을 꼭 주의해야합니다.<br/>

<br/><br/>

## 요소 수정하기

객체와 마찬가지로 대괄호 표기법을 이용해서 요소를 수정할 수 있습니다.<br/>

```js
const arr = [0, 1, 3, 3, 4];
arr[2] = 2;
console.log(arr); //  [0,1,2,3,4];
```

한꺼번에 많은 요소를 같은 값으로 바꿔야 할 때는 `fill` 메소드를 사용하면 됩니다.<br/>

```js
const arr = [0, 1, 2, 3, 4];

// 전체를 0으로 채우기
arr.fill(0);
console.log(arr); //  [0.0.0.0.0];

// 인덱스 1과 4사이를 1로 채우기
arr.fill(1, 1, 4); //  배열의이름.fill(채울값, 시작위치(포함), 종료위치(미포함))
console.log(arr); // [0,1,1,1,0];
```

`Array` 생성자와 `fill` 메소드를 사용하면, 큰 배열을 만들고 값을 채워넣는 일을 쉽게 할 수 있습니다.<br/>

```js
new Array(1000); //  [<1000 empty item>]
new Array(1000).fill(5); //  [5,5,5,5,5...]
```

<br/><br/>

## 배열의 끝 부분에서 요소를 추가/제거하기

`push` 메소드와 `pop` 메소드를 사용하면 배열의 끝 부분에서 요소를 추가/제거할 수 있습니다.<br/>

```js
const arr = [];
arr.push("one"); //  1 (요소가 추가된 후의 배열의 길이를 반환함)
arr.push("two", "three"); // 3

console.log(arr); //  ['one', 'two', 'three']

// 배열의 요소 삭제하기

arr.pop(); // 'three' 삭제
arr.pop(); // 'two' 삭제
arr.pop(); // 'one' 삭제
arr.pop(); // undefined (더 이상 배열에서 요소가 남아있지 않으면 'undefined'를 반환합니다.)
```

<br/><br/>

## 배열의 시작 부분에서 요소를 추가/제거하기

반대로 `unshift`, `shift` 메소드를 사용하여 배열의 시작 부분에서 요소를 추가하거나 제거할 수 있습니다.<br/>

```js
const arr = [];
arr.unshift(1); //  1 (요소가 추가된 후의 배열의 길이를 반환함)
arr.unshift(2, 3); //  3

console.log(arr); //  [2,3,1]

// 배열의 요소 삭제하기
arr.shift(); //  2
arr.shift(); //  3
arr.shift(); //  1
arr.shift(); //  undefined (더 이상 배열에서 요소가 남아있지 않으면 'undefined'를 반환합니다.)
```

<br/><br/>

## 요소를 배열 중간에 삽입하기

`splice` 메소드를 사용하면 배열에 속해있는 연속된 여러 요소, 즉 배열의 일부분을 통째로 바꿔버릴 수 있습니다.<br/>

```js
let arr = [1, 2, 3, 4, 5];

// 인덱스 1부터 3개를 바꿔칩니다.
// splice 메소드는 바꿔치기를 통해 제거된 요소를 반환합니다.

arr.splice(1, 3, "이", "삼", "사"); // 배열의이름.splice(인덱스시작지점, 바꿀개수, 바꿀 값)
console.log(arr); // [1, '이', '삼', '사', 5]
```

splice 를 통해 반드시 같은 개수의 요소만 바꿀수 있는 것은 아닙니다.

```js
let arr = [1, 2, 3, 4, 5];

arr.splice(1, 3, "ㅇ");
console.log(arr); // [1,'o',5]
```

splice 의 뒤쪽 인수를 생각하면, 요소를 제거할 뿐 배열에 아무것도 삽입하지 않습니다.

```js
let arr = [1, 2, 3, 4, 5];

arr.splice(1, 3); //  [2,3,4]
console.log(arr); //  [1,5]
```

이렇게 splice 메소드를 배열의 중간 부분에 있는 요소를 바꾸거나 제거할 때 사용할 수 있습니다.<br/>

<br/><br/>

## 배열 뒤집기

배열의 `reverse` 메소드를 호출하면 해당 배열을 거꾸로 뒤집을수 있습니다.<br/>

```js
const arr = [1, 2, 3];

// 'reverse' 메소드는 'arr'을 뒤집은 후, 'arr'을 그대로 반환합니다.
arr.reverse(); //  [3,2,1]
console.log(arr); //  [3,2,1]
```

<br/><br/>

## 배열 정렬하기

배열의 `sort` 메소드를 통해 원하는 방식대로 배열을 정렬할 수 있습니다.<br/>

```js
const arr = [3, 1, 4, 5, 2];

// sort 메소드는 arr을 비교 함수에 따라 정렬한 뒤, arr을 그대로 반환합니다.
arr.sort((a, b) => a - b); // 오림차순 정렬 [1,2,3,4,5];
console.log(arr); //  [1,2,3,4,5]
```

`sort` 메소드의 인수에는 비교함수를 넘겨줘야 합니다.<br/>
비교 함수는 인수를 두 개 받아서, 아래의 조건에 따라 잘 정렬되도록 적절한 값을 반환해줘야 합니다.<br/>

---

<br/>

만약 어떤 두 값 `a`, `b`에 대해서 비교 함수 compare 를 compare(a, b) 와 같이 호출했을 때 :

* 음수를 반환하면, a 가 b 앞에 오도록 합니다. (오름차순)
* 0 을 반환하면, a 와 b 를 같은 순서로 오도록 합니다.
* 양수를 반환하면, b 가 a 앞에 오도록 합니다. (내림차순)

<br/>

---

<br/>

따라서, 어떤 배열을 정렬할 때에는 어떤 값을 기준으로 정렬할 지 생각한 다음, 정렬함수를 만들 때<br/>
오름차순으로 정렬할지, 내림차순으로 정렬할지 생각해보면 됩니다.<br/>
예를 들어, 문자열의 길이를 기준으로 내림차순 정렬을 하고 싶다면 이렇게 하면 됩니다.<br/>

```js
const names = ["moong2", "min_zzz", "jogoogod", "shinyerin"];
names.sort((x, y) => y.length - x.length); //  내림차순이니까 양수를 반환하기 위해 y를 앞에다가 둡니다.
console.log(names); //  [ 'shinyerin', 'jogoogod', 'min_zzz', 'moong2' ]
```

간혹 비교함수를 넘기지 않아도 정렬이 잘 되는 것처럼 보일 수 있습니다.

```js
const arr = [1, 3, 2, 5, 4];
arr.sort(); // [1, 2, 3, 4, 5]
```

하지만 비교 함수를 인수로 넘기지 않을 경우, sort 메소드는 먼저 요소를 전부 문자열로 변환한 후<br/>
유니코드 코드 포인트를 비교하는 방식으로 정렬을 합니다. (대문자보다 소문자가 크다고 계산하기에 오차가 발생할 수 있습니다.)<br/>
반드시 sort 함수를 사용할 때는 비교 함수를 사용하도록 합니다.<br/>

```js
[20, 3, 100].sort(); //  [100, 20, 3] : 큰 수부터 정렬하는 것이 아니라 수의 첫 수를 보고 1,2,3 순으로 정렬이 된 것입니다.
["abc", "DEF", "aBC"].sort(); //  ["DEF", "aBC", "abc"]

[20, 3, 100].sort((x, y) => x - y); //  [3, 20, 100];
["abc", "DEF", "aBC"].sort((x, y) => x.localeCompare(y)); //  ['abc','aBC','DEF']
```

<br/><br/>

## 배열의 길이

배열의 길이는 `length`속성을 통해 쉽게 확인할 수 있습니다.<br/>
배열의 길이가 변함에 따라, length 속성의 값도 자동으로 달라집니다.<br/>

```js
const arr = [];
console.log(arr.length); //  0

arr.push(1, 2, 3);
console.log(arr.length); //  3
```

length 속성에 값을 대입해서 배열의 길이를 늘렸다가 줄였다가 할 수 있지만 권장하지 않습니다.<br/>

```js
const arr = [];

// 배열의 길이 늘이기
arr.length = 10;
console.log(arr); //  [ <10 empty items> ]

// 배열의 길이 줄이기 (줄어든 만큼 뒷쪽에 있는 요소들은 버려집니다.)
arr.fill(1); //  [1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
arr.length = 2;
console.log(arr); //  [1,1]

//이런 코드처럼 왠만하면 하지 않는 걸로
```

<br/><br/>

## 배열 순회하기

배열의 각 요소를 차례대로 돌면서 요소에 대한 작업을 가지고 순회(traverse)라고 합니다.<br/>
배열에 접근하는 방법으로는 여러가지가 있습니다.<br/>

<br/><br/>

## 배열 순회하기 - for

```js
const arr = [1, 2, 3];

for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}
```

전통적으로 많이 썼던 방식이지만 `forEach` 메소드와 `for...of` 구문이 추가되면서 잘 쓰지 않습니다.<br/>

<br/><br/>

## 배열 순회하기 - forEach 메소드

배열에 forEach 메소드를 사용하면, 배열의 각 요소에 대해 함수를 호출할 수 있습니다.<br/>

```js
const str = [1, 2, 3];

arr.forEach(item => {
  consoel.log(`현재 요소 ${item}에 대해 함수가 실행되고 있습니다.`);
});
```

forEach 메소드에 넘기는 함수에는 총 세 개의 인수가 들어옵니다.<br/>

1.  현재 순회중인 배열의 요소
2.  요소의 인덱스
3.  순회중인 배열

```js
const arr = [1, 2, 3];
arr.forEach((item, index, array) => {
  console.log(`현재 ${index + 1}번째 요소에 대해 함수가 실행되고 있습니다.`);
});
```

<br/><br/>

## 배열 순회하기 - for...of 구문

ES2015 에 도입된 `for...of` 구문은, 역시 ES2015 에 도입된 iterable 을 순회하기 위해 사용할 수 있습니다.<br/>
배열 역시 iterable 이므로, for...of 구문을 사용해 순회할 수 있습니다.<br/>

> iterable(순회가능한 객체) : Symbol.iterator 심볼을 속성으로 가지고 있고, 이터레이터 객체를 반환하는 객체를 뜻합니다. (자세히는 나중에 공부하도록 하겠습니다.)

```js
const arr = [1, 2, 3, 4, 5];

for (let item of arr) {
  console.log(item);
}

// for문안에 (const item of arr)에서 const는 루프가 종료되고 다음 루프로 넘어갈때 선언이 날아가기 때문에 const를 써도 괜찮습니다.
const arr = [1, 2, 3, 4, 5];

for (const item of arr) {
  console.log(item);
}
```

어떤 것을 쓰는 게 좋을까요?<br/>

<br/>
단순히 배열을 순회하기 위한 목적이라면 `for...of` 구문을 사용하는 것이 코드의 간결성이나 속도 측면에서 유리합니다.<br/>
다만, 배열을 순회하면서 배열의 인덱스가 필요한 경우에는 `for...of` 구문을 사용할 수 없습니다.<br/>
이 때에는 `forEach` 메소드를 사용하면 됩니다.(forEach는 item, index, array를 모두 인수로 받기 때문입니다)<br/>
코드의 실행속도가 중요할 경우에는 `for` 구문을 쓰는게 좋습니다.<br/>

<br/><br/>

## 배열로부터 새로운 값 생성

배열을 다루다보면 배열로부터 다른 배열, 혹은 다른 값을 계산해내야 하는 작업을 많이 하게 됩니다.<br/>
배열을 순회하는 것만으로도 이런 작업을 할 수 있지만, 배열에 내장된 메소드를 활용하면 훨씬 더 간결한 코드로 같은 작업을 할 수 있습니다.<br/>
아래 메소드들은 모두 원본 배열에 아무런 영향을 미치지 않습니다.<br/>

<br/><br/>

## 배열로부터 새로운 값 생성 - slice

`slice` 메소드는 배열의 일부분에 해당되는 새로운 배열을 반환합니다.<br/>

```js
const arr = [1, 2, 3, 4, 5];

// 인덱스 2부터 인덱스 4 사이의 요소들을 가지고 새로운 배열을 생성
const newArr = arr.slice(2, 4); //  [3,4]

// newArr을 조작해도, 원본에는 아무런 영향을 미치지 않습니다.
newArr[0] = 5;
console.log(newArr); //  [5,4]
consoel.log(arr); //  [1,2,3,4,5]
```

첫 번째 인수의 기본값은 0, 두 번째 인수의 기본값은 배열의 length 속성입니다.<br/>
즉, 인수 없이 호출하면 배열 전체가 복사됩니다.<br/>

```js
const arr2 = arr.slice(); //  [1,2,3,4,5];
```

다만, `slice`는 얕은 복사를 하므로 배열 안에 배열 또는 객체가 들어가 있을 경우에는 주의해야합니다.<br/>

> 얕은 복사란? 객체안에 객체가 들어가 있는 경우에 객체 내부의 객체를 완벽히 복사하지 못하고 참조만 하는 것입니다. (자세히는 나중에 공부하도록 하겠습니다.)

<br/><br/>

## 배열로부터 새로운 값 생성 - map

`map` 메소드는 배열의 각 요소에 함수를 적용해서, 그 반환값을 요소로 갖는 새로운 배열을 만듭니다.<br/>
`forEach`와 비슷해 보이지만, 새로운 배열을 만든다는 점이 다릅니다.<br/>
(forEach 는 배열의 순회만 하지 반환하지 않습니다.)<br/>

```js
const arr = [1, 2, 3, 4, 5];

// arr의 각 요소를 제곱한 값으로 새 배열을 만듭니다.
const newArr = arr.map(item => item ** 2);
console.log(newArr); //  [1,4,9,16,25]
```

map 역시 인수로 들어온 함수를 호출할 떄 세 개의 인수를 넘깁니다. 이는 forEach 와 같습니다.<br/>

```js
arr.map((item, index, array) => {
  return item * index;
}); //  [0,2,6,12,20]
```

<br/><br/>

## 배열로부터 새로운 값 생성 - concat

`concat` 메소드는 여러 배열을 연결해서 새 배열을 만들 떄 사용됩니다.<br/>

```js
const arr = [1, 2];

arr.concat([3, 4], [5, 6], [7, 8]); //  [1,2,3,4,5,6,7,8]
```

<br/><br/>

## 배열로부터 새로운 값 생성 - reduce

`reduce` 메소드는 모든 요소의 값을 종합해서 하나의 값으로 만드는 계산을 할 때 사용합니다.<br/>

```js
const arr = [1, 2, 3];

arr.reduce((acc, item) => acc + item, 0); //  6
```

위 코드에서 일어난 일을 순서대로 써보면 다음과 같습니다.<br/>

```
1. 초기값 0과 배열의 첫 번째 요소인 1을 인수로 하여 함수를 호출합니다. 즉, acc 매개변수에 0이 대입되고,
    item 매개변수에 1이 대입됩니다. 결과값은 1이 됩니다. 이를 누적값이라 합니다.

2. 누적값 1과 배열의 두 번째 요소인 2를 인수로 하여 함수를 호출합니다. 결과값 3이 다시 누적값이 됩니다.
3. 누적값 3과 배열의 세 번째 요소인 3을 인수로 하여 함수를 호출합니다. 결과값은 6입니다.
4. 더 이상 요소가 없으므로 reduce 호출의 결과값은 6이 됩니다.
```

reduce 는 배열에 대한 계산을 하는 만능 도구로 사용 가능합니다.<br/>
실제로 배열의 많은 메소드들이 reduce 를 통해 다시 구현될 수 있습니다. (연습해보기)<br/>
<br/>
`reduce`에 주어지는 함수 역시 `forEach`나 `map`과 마찬가지로 여러 개의 인수를 받는데,<br/>
맨 앞에 누적 값이 추가되어 (누적값, 현재 요소, 인덱스, 배열) 같은 인수를 받습니다.<br/>

```js
const arr = ["one", "two", "three"];

arr.reduce((acc, item, index, array) => {
  return acc + `(${index}: ${item})`;
}, ""); // '(0:one)(1:two)(2:three)'
```

`reduce` 메소드에 초기값 인수를 주지 않으면, 첫 번째 인수가 초기값으로 지정되어 첫 번째 요소와 두 번째 요소에 대한<br/>
계산부터 시작합니다. 즉, 위 두 예제에서 초기값을 생략해도 같은 결과가 나옵니다. 다만 배열의 요소가 하나 밖에 없다면<br/>
계산이 수행되지 않고 첫 번째 요소가 그대로 반환되므로, 초기값은 항상 제공해주는 것이 좋습니다.<br/>

```js
const arr = ["one"];

// 배열안의 요소들의 문자열의 합을 반환하고자 하는데 요소가 하나밖에 없습니다.
// 이런 경우에는 초기값을 안주면 계산할 대상이 자기 자신밖에 없어서 함수가 호출되지 못하고 one을 반환합니다.
arr.reduce((acc, item) => {
  return acc + item.length;
}); // 'one'

// 초기값을 주면 정상적으로 계산이 됩니다.
arr.reduce((acc, item) => {
  return acc + itme.length;
}, 0); //  3
```

계산을 오른쪽부터 수행하고 싶을 경우에는 `reduceRight` 메소드를 사용하면 됩니다.

<br/><br/>

## 배열로부터 새로운 값 생성 - filter

`filter` 메소드를 통해 배열에서 원하는 요소만을 골라서 새로운 배열을 생성할 수 있습니다.<br/>
filter 메소드에는 진리값(boolean)을 반환하는 함수를 주어야 합니다.<br/>
filter 메소드는 함수의 연산을 통해 truthy 면 새로운 배열에 포함되고, flasy 면 새로운 배열에 포함시키지 않습니다.
이처럼 진리값을 반환하는 함수를 predicate 라고 합니다.<br/>

```js
const arr = [1, 2, 3, 4, 5];

// 짝수만 골라내기
arr.filter(item => item % 2 === 0); //  [2,4] : 요소의 값이 2로 나눈 나머지가 0이면 true, 아니면 false를 반환합니다.
```

filter 에 주어지는 함수 역시 `forEach`와 마찬가지로 (현재요소, 인덱스, 배열) 세인수를 받습니다.<br/>

<br/><br/>

## 배열로부터 새로운 값 생성 - join

`join` 메소드는 배열의 요소들을 문자열로 변환 후, 메소드에 주어진 구분자(separator)를 이용해 하나의 문자열로 결합하여 반환합니다.<br/>

```js
const arr = [1, 2, 3];

arr.join("&"); //  '1&2&3'
```

구분자를 넘기지 않을 경우 `,` 문자가 구분자로 사용됩니다.

```js
const arr = [1, 2, 3];

arr.join(); //  '1,2,3'
```

<br/><br/>

## 요소 찾기

`indexOf`와 `lastIndexOf` 메소드를 사용하면 특정 요소가 배열의 몇 번째에 위치하는 지를 알아낼 수 있습니다.<br/>
`indexOf`는 배열의 왼쪽부터, `lastIndexOf`는 오른쪽부터 검색해서 처음 만나는 요소의 인덱스를 반환합니다.<br/>
만약 일치하는 요소가 없을 경우, 두 메소드 모두 `-1`을 반환합니다.<br/>

```js
const arr = ["a", "b", "c", "d", "c"];

arr.indexOf("b"); //  1
arr.lastIndexOf("c"); //  2

arr.indexOf("o"); //  -1
arr.lastIndexOf("s"); //  -1
```

두 메소드 모두 두 번째 인수로 시작 인덱스를 받습니다. 시작 인덱스가 주어지면 해당 인덱스부터 검사를 합니다.<br/>

```js
const arr = ["가", "나", "다", "라", "마", "가"];

arr.indexOf("가", 2); //  5 : 시작인덱스가 2로 주어져서 2(다)부터 검사를 하여 가를 찾았습니다. 값이 5인 이유는 시작인덱스부터 새도 인덱스 값의 기준은 0이며 변하지 않습니다.
arr.lastIndexOf("다", 2); //  2 : 거꾸로 2(라)부터 검사를 하여 다를 찾았습니다. 값이 2인 이유는 lastIndexOf또한 인덱스 값의 기준은 0이기 때문입니다.
```

`find` 메소드와 `findIndex` 메소드를 사용하면 특정 조건을 만족하는 요소를 찾을 수 있습니다.<br/>
두 메소드 모두 predicate(진리값 반환하는 함수)를 이용해 왼쪽부터 검사해서 처음 만나는 요소를 찾습니다.<br/>
`find`는 요소 자체를 반환하며, `findIndex`는 요소의 인덱스를 반환한다는 차이점이 있습니다.<br/>
조건을 만족하지 못하면 `find` 는 `undefined` 를 `findIndex` 는 `-1` 을 반환합니다.<br/>
(원하는 조건을 만족하는 요소가 필요할 때는 find, 조건에 만족하는 모든 것을 원할때는 filter, 인덱스가 필요하면 findIndex 를 쓰도록 합니다.)<br/>

```js
const names = ["moong2", "min_zzz", "jogoogod", "shinyerin"];

names.find(item => item.length > 6); //  'min_zzz' : 조건에 만족하는 요소중 왼쪽부터 검사해서 처음 만나는 요소이기 때문!
names.findIndex(item => item.length > 6); //  1 : 조건에 만족하는 요소중 왼쪽부터 검사해서 처음 만나는 요소(min_zzz)의 인덱스를 반환

names.find(item => item.length > 12); //  undefined
names.findIndex(item => item.length < 1); //  -1
```

`forEach`와 마찬가지로, `find`와 `findIndex`에 주어지는 predicate 에는 (현재요소, 인덱스, 배열) 세 인수가 넘겨집니다.

<br/><br/>

## 배열이 특정 조건을 만족하는지 판별하기

배열의 세 메소드 `includes`, `every`, `some`는 모두 배열이 특정 조건을 만족하는 지를 나타내는 진리값을 반환합니다.<br/>
ES2016 에서 도입된 includes 메소드는 배열이 특정 요소를 포함하고 있는지를 판별합니다.<br/>
`indexOf`로도 비슷한 일을 할 수 있지만, `includes`가 진리값을 반환한다는 점에서 조금 더 편합니다<br/>
`includes` 메소드도 역시 시작 인덱스를 인수로 받습니다.<br/>

```js
const arr = ["one", "two", "three"];

arr.includes("one"); // true : 배열안에 일치하는 문자열인 "one"이 있으므로 true
arr.includes("three", 1); //  true : 1번 인덱스를 시작으로 배열안에 일치하는 문자열인 "three"가 있으므로 true
arr.includes("one", 1); // flase : 1번 인덱스를 시작으로 배열안에 일치하는 문자열인 "one"이 없으므로 false
```

`every`는 predicate 을 인수로 받아서, 모든 요소가 조건을 만족하는 지를 검사합니다.

```js
const arr = ["one", "two", "three"];

arr.every(item => item.length > 2); //  true : 모든 요소가 2글자 이상이므로 true
arr.every(itme => item.length < 2); //  false : 모든 요소가 2글자 이상이므로 false
```

`some`은 predicate 을 인수로 받아서, 조건을 만족하는 요소가 하나라도 있는지 검사합니다.

```js
const arr = ["one", "two", "three"];

arr.some(item => item.length > 3); //  true : 조건을 만족하는 요소가 있기 때문에 true
arr.some(itme => item.length > 5); //  false : 조건을 만족하는 요소가 하나도 없기에 false
```

`forEach`와 마찬가지로, `every`와 `some`에 주어지는 predicate 에는 (현재요소, 인덱스, 배열) 세 인수가 넘겨집니다.

<br/><br/>

## 배열인지 아닌지 판별하기

어떤 값이 배열인지 아닌지 판별하기 위해서 `Array.isArray` 정적 메소드를 사용할 수 있습니다.

```js
Array.isArray([]); //  true
Array.isArray({}); //  false : 객체
Array.isArray("hello"); // flase : 문자열
```

<br/><br/>

## 문자열과 배열

문자열은 배열과 유사한 문법을 통해 다뤄질 수 있습니다.<br/>
그리고 문자열의 메소드 중에서 배열의 메소드 중 몇몇과 이름이 같고 완전히 같은 방식으로 동작하는 것들이 있습니다.<br/>

```js
"hello"[0]; //  'h'
"hello".slice(2, 4); //  'll'

for (let c of "hello") {
  console.log(c); // "h","e","l","l","o"
}
```

<br/><br/>

## 다차원 배열 (multidimensional array)

JS 에서는 표 형태의 자료를 간단히 나타내기 위해 배열을 요소로 갖는 배열을 사용할 수 있습니다.<br/>

```js
const table = [[1, 2, 3], [4, 5, 6], [7, 8, 9]];
```

이렇게 배열 속에 배열이 중첩되어 있는 자료구조를 가지고 다차원 배열이라고 합니다.<br/>
다차원 배열 속에 있는 요소를 다루기 위해서, 대문자 표기법을 연이어 사용할 수 있습니다.<br/>

```js
table[0][2]; // 3
table[2][1]; // 8
```

<br/><br/>

# 2. Today I Found Out

```
단순히 배열이라고 하면 변수에 대괄호를 열고 값을 입력하면 index형식으로 다룰수 있다고 쉽게 생각하고 있었는데
오늘 공부를 꼼꼼히 하나하나 살펴보고 직접 적용해보면서 공부한 결과 생각했던 것보다 배열에 대해서
공부할 것이 많았고, 무엇보다 저 기능을 활용하면 무언가 만들때 정말 편리하겠다라는 메소드들이
많아서 더욱 흥미로웠던 것 같습니다.
앞으로 계속 써보고 다뤄보면서 더욱 배열과 친해지도록 더 노력해야 할 것 같습니다.
```

<br/><br/>

# 3. refer

> https://helloworldjavascript.net/pages/190-array.html

> https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array

> http://poiemaweb.com/js-array
