##  ⏰ 05 재귀 알고리즘

> 자신을 정의할 때 자기 자신을 재참조하는 알고리즘.

- "메서드 자신"을 호출하는 것보다는 "자기 자신과 똑같은 메서드"를 호출한다고 이해하면 더 자연스럽다.



### 0. 재귀 == 알고리즘?

- 재귀는 단순히 함수가 자신을 참조하는 매커니즘.
- 분할정복이라는 알고리즘이 있는데, 보통 분할정복을 재귀함수로 구현한다.
- 이처럼 다양한 알고리즘의 기본 토대가 되는 개념이 재귀 함수. 알고리즘이라고 할 수는 없지 않나..? (뇌피셜)



> 💡**토막 지식. 분할 정복 알고리즘 (divide and conquer)**
>
> 세분된 작은 문제의 풀이를 결합해 전체 문제를 풀이하는 기법. 보통 재귀 함수로 많이 구현한다. (ex. 하노이, 8퀸 문제) 
>
> 퀵소트, 병합 정렬도 분할 정복 알고리즘이다.



### 1. 재귀 함수 구성요소

- **종료 조건** : `if (나쁜 값이 들어왔다면) { 정지! };`
- **기반 조건** : `if (이런 일이 일어난다면) { 성공! };` // 종료 조건은 모든 나쁜 값을 잡아내지만 기반 조건은 성공하는 조건일 때만 조건문 내 함수를 수행한다는 차이점이 있다.
- **재귀** : 실제 재귀가 일어나는 부분



### 2. 재귀 방법

- **직접 재귀** : 자신과 같은 메서드를 호출
- **간접 재귀** : 메서드 a가 메서드 b를 호출하고, 다시 메서드 b가 메서드 a를 호출하는 식.



### 3. 재귀 알고리즘 분석

#### 하향식 분석

가장 위쪽에 위치한 상자의 메서드 호출부터 시작해 계단식으로 자세히 조사하는 분석 기법

`recur(4) -> requr(3) -> requr(2) -> requr(1)` 

#### 상향식 분석

하향식 분석과 달리 아래쪽부터 쌓아 올리며 분석하는 방법

`recur(1) -> requr(2) -> requr(3) -> requr(4)` 





### 5. 재귀 알고리즘의 비재귀적 표현

#### 재귀함수

```javascript
function requr(n) {
	if (n > 0) {
		requr(n - 1);
		console.log(n);
		requr(n - 2);
	}
}
console.log(requr(4));
```

#### 꼬리 재귀의 제거

```javascript
function requr(n) {
	while (n > 0) {
		requr(n - 1);
		console.log(n);
		n = n - 2;
	}
}
console.log(requr(4));
```

#### 재귀의 제거

```javascript
function requr(n) {
	stack = [];

	while(true) {
		if (n > 0) {
			stack.push(n);
			n = n - 1;
			continue;
		}
		if (stack.length) {
			n = stack.pop();
			console.log(n);
			n = n - 2;
			continue;
		}
		break;
	}
}
console.log(requr(4));
```



### 6. 재귀 알고리즘 예시

#### 1) 팩토리얼 구하기

##### 조건

1. 0이면 = 1
2. n > 0 이면  n * ( n-1 )

##### 코드

```javascript
function factorial(n) {
  // 종료 조건
	if (x < 0)
		return ;
  // 기반 조건
	if (x === 0)
		return 1;
  // 재귀
  return x * factorial(x - 1);
}
console.log(factorial(5));
// 120
```



#### 2) 유클리드 호제법 : 최대공약수 구하기

##### 조건

z = gcd(x, y)인 경우

1. y가 0이면 x
2. 아니라면 gcd(y, x % y)

##### 코드

```javascript
function gcd(x, y) {
	if (y == 0)
		return x;
	else
		return gcd(y, x % y);
}
console.log(gcd(8, 22));
// 매개변수를 22, 8해도 결과는 같다.
```





#### 3) 하노이의 탑

- 원반의 이동 횟수 :  2ⁿ−1 

```javascript
function hanoi(no, x, y) {
	if (no > 1)
		hanoi(no - 1, x, 6 - x - y);
	console.log("원반 [" + no + "]을 " + x + "기둥에서 " + y + "기둥으로 옮김.");
	if (no > 1)
		hanoi(no - 1, 6 - x - y, y);
}
console.log(hanoi(3, 1, 3));
```



#### 4) 8퀸

```javascript
// 모든 경우의 수를 구하는 함수 => 가지 뻗기
let pos = [];
let flag_a = [];
let flag_b = [];
let flag_c = [];
function set(i) {
	for (let j = 0; j < 8; j++) {
		if (Boolean(flag_a[j]) == false &&
			Boolean(flag_b[i + j]) == false &&
			Boolean(flag_c[i - j + 7]) == false) {
			pos[i] = j;
			if (i == 7) {
				console.log(flag_b);
			}
			else {
				flag_a[j] = flag_b[i + j] = flag_c[i - j + 7] = true;
				set(i + 1);
				flag_a[j] = flag_b[i + j] = flag_c[i - j + 7] = false;
			}
		}
	}
}
console.log(set(0));
```



------



### 참고 자료

[자바스크립트 재귀(Recursion) 이해하기 - velog](https://velog.io/@jakeseo_me/자바스크립트-개발자라면-알아야-할-33가지-개념-23-자바스크립트-자바스크립트-재귀Recursion-이해하기)

[분할정복과 재귀의 차이를 모르겠습니다. | 코드잇](https://www.codeit.kr/community/threads/5651)

