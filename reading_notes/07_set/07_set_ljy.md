#  👨‍👩‍👧‍👧 07 집합

> 명확한 조건을 만족하는 자료의 모임



- 집합의 요소에는 순서가 없다. `{1,2,3} === {3, 2, 1}`
- 요소의 개수가 무한개 = **무한집합 <-> 유한집합**
- 요소가 하나도 없는 집합 = **공집합** 
- 집합 A의 모든 요소가 집합 B의 요소일 때 => **부분집합** `{1, 2, 3}, {1, 2, 3}`
- 부분집합이면서 집합 A가 집합 B와 같지 않을 때 => **진부분집합** `{1, 2}, {1, 2, 3}`



## [Js] Set 객체

- value들로 이루어진 컬렉션 == 집합
- Array와 다르게 Set은 같은 value를 2번 포함할 수 없음.
- 그래서 Set에 이미 존재하는 값을 추가하려고 하면 아무 일도 없다.
- has()는 indexOf()보다 빠르다. 다만 index가 존재하지 않기 때문에 index로 value에 접근할 수 없다.

```javascript
const a = new Set();
const	b = new Set().add('a').add('b');

b.add('c');
console.log(b.has('a'));
// true

b.delete('c');
b.clear();
console.log(b.size);
// 0
```



### set 메서드

- `add()` : 요소 추가
- `delete()` : 요소 삭제
- `has()` : 요소 유무 확인 
- `clear()` : 모든 요소 삭제



### set 프로퍼티

- `size` : 요소의 수



### set을 배열로 바꾸기

- sperad 연산자 (`...`) 사용

```javascript
const a = new Set();
a.add('Elsa').add('Anna');

console.log(a);
// Set { 'Elsa', 'Anna' }

console.log([...a.values()]);
// [ 'Elsa', 'Anna' ]

console.log([...a]);
// [ 'Elsa', 'Anna' ]
```



### 참고 자료

[자바스크립트 ES6 — Set에 대해 알아보자 🎉 - Hyeokwoo Alex Kwon - Medium]([https://medium.com/@khwsc1/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-es6-set%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90-9b7294dfba99](https://medium.com/@khwsc1/자바스크립트-es6-set에-대해-알아보자-9b7294dfba99))

[[JS #5] ES6 Map(), Set() - Kevin Hong - Medium](https://medium.com/@hongkevin/js-5-es6-map-set-2a9ebf40f96b)