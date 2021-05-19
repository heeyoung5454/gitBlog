---
layout: single
title: "자주 사용하는 javascrpit 내장함수"
categories: javascript
tags: coding
---

자주 자바스크립트 내장함수를 정리해본다.

개발자도구(F12) console창에서 실행해볼 수 있다.

#### foreach

배열 값 출력하기(반복)

```javascript
const array = [1, 2, 3, 4, 5];

array.forEach(function (t) {
  console.log(t);
});

//결과 : 1,2,3,4,5
```

#### Map

기존 배열의 값을 이용하여 새로운 배열을 반환

```javascript
const array = [1, 2, 3, 4, 5];

const map = array.map(function (t) {
  return t * t;
});

console.log(map);

//결과 : [1,4,9,16,25]
```

#### filter1

조건에 만족하는 모든 요소들을 모아 새로운 배열을 반환

```javascript
const array = [1, 2, 3, 4, 5];

//짝수만 반환
const evenFilter = array.filter(function (t) {
  return t % 2 === 0;
});

console.log(evenFilter);

//결과 : [2,4]
```

#### filter2

```javascript
const a = [
  {
    name: "One",
    age: 11,
  },
  {
    name: "Two",
    age: 12,
  },
  {
    name: "Three",
    age: 13,
  },
  {
    name: "Four",
    age: 14,
  },
];

//age로 검색
const ageFilter = a.filter(function (t) {
  return t.age === 14;
});

console.log(ageFilter);

/*결과 :
    [{
        name:'Four',
        age:14,
    }]
*/
```

#### reduce

배열의 각 요소에 대해 리듀서(reducer) 함수를 실행하고 하나의 결과값을 반환
인자로는 리듀서함수와 accumulator 초기값을 받는다. reducer 함수란 정해진 4개의 매개변수가 있다.

accumulator : 누적 되는 매개 변수
currentValue : 현재 순환하는 인덱스의 값
currentIndex : 현재 순환하는 인덱스(생략가능)
array : 호출한 배열을 가르킴(생략가능)

```javascript
const array = [1, 2, 3, 4, 5];

const reduceResult = array.reduce(function (t) {
  return array + reduceResult;
}, 0);

console.log(reduceResult);

//결과 : 15
```

#### sort

배열 요소를 정렬. 기본 정렬 순서는 문자열의 유니코드 포인트를 따른다.

```javascript
const months = ["March", "Jan", "Feb", "Dec"];
months.sort();
console.log(months);
//["Dec", "Feb", "Jan", "March"]

/*****함수로 정렬********/
let numbers = [4, 2, 5, 1, 3];
numbers.sort(function (a, b) {
  return a - b;
});
console.log(numbers);

// [1, 2, 3, 4, 5]
```

#### splice

해당 구간 인덱스의 요소를 다른 요소로 바꾸거나 삭제하고 새로운 배열을 반환

```javascript
const arrayB = [1, 2, 3, 4, 5];
const arrayC = [1, 2, 3, 4, 5];

//0번째부터 2개 삭제
const b = arrayB.splice(0, 2);

//0번째부터 2개 삭제후 10,11 추가
const c = arrayC.splice(0, 2, 10, 11);

console.log(b); // [1,2]
console.log(c); // [1,2]
console.log(array); // [3,4,5]
```

#### shift

배열의 첫번째 요소 제거

```javascript
const array = [1, 2, 3];

array.shift();

console.log(array); //[2,3]
```

#### pop

배열의 마지막 요소 제거

```javascript
const array = [1, 2, 3];

array.pop();

console.log(array); //[1,2]
```

#### unshift

배열의 첫번째 요소에 값 추가

```javascript
const array = [1, 2, 3];

array.unshift(10);

console.log(array); //[10,1,2,3]
```

#### push

배열의 마지막 요소에 값 추가

```javascript
const array = [1, 2, 3];

array.push(10);

console.log(array); //[1,2,3,10]
```

#### indexOf

배열에서 특정값의 인덱스 반환

```javascript
const array = ["첫번째", "두번째", "세번째"];

console.log(array.indexOf("두번째")); // 2
```

#### findIndex

배열에서 조건에 맞는 인덱스 반환

```javascript
const array = [
  { name: "One" },
  { name: "Two" },
  { name: "Three" },
  { name: "Four" },
];
console.log(array.findIndex((ary) => ary.name === "Four")); // 4
```

#### find

배열에서 조건에 맞는 값 반환

```javascript
const array = [
  { name: "One" },
  { name: "Two" },
  { name: "Three" },
  { name: "Four" },
];
console.log(array.find((ary) => ary.name === "Four")); // { name:'Four'}
```

#### join

배열을 문자열로 반환하는데 인자로 넘겨준 값으로 배열의 요소사이에 삽입된다.

```javascript
const array = [1, 2, 3];
console.log(array.join("T")); // 1T2T3;
```

#### Object.assign

대상객체에 추가적인 객체의 값을 합쳐서 반환

```javascript
const target = { a: 1, b: 2 };
const source = { b: 3, c: 4 };

const returnedTarget = Object.assign(target, source);

console.log(target); // { a: 1, b: 4, c: 5 }

console.log(returnedTarget); // { a: 1, b: 4, c: 5 }
```

#### toString()

문자열로 반환

```javascript
const array = [1, 2, "1a", 3];

console.log(array.toString()); // "1,2,1a,3"
```

#### replace

문자열에서 특정문자를 치환(첫번째 인식된 문자만 치환됨)

```javascript
const p =
  "The quick brown fox jumps over the lazy dog. If the dog reacted, was it really lazy?";

console.log(p.replace("dog", "monkey"));
// The quick brown fox jumps over the lazy monkey. If the dog reacted, was it really lazy?
```
