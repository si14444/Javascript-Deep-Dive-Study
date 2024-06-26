# 15장 let,const 키워드와 블록 레벨 스코프

## var 키워드로 선언한 변수의 문제점

### 변수 중복 선언 허용

```jsx
var x =1;
var x =100;
```

### 함수 레벨 스코프

```jsx
var x =1;
if(true){
	var x = 10;
}
console.log(x); // 10
```

### 변수 호이스팅

```jsx
console.log(foo);
foo = 123;
var foo;
```

## let 키워드

### 변수 중복 선언 금지

- let 키워드로 이름이 같은 변수를 중복 선언하면 문법 에러가 발생한다

```jsx
let foo = 123;
let foo = 234;
// syntaxError: Identifier bar has already been declared
```

### 블록 레벨 스코프

```jsx
let foo = 1;
{
	let foo = 2;
	let bar = 3;
}
console.log(foo);
console.log(bar);
```

### 변수 호이스팅

- 호이스팅이 동작하지 않는 것처럼 동작하지만 호이스팅이 발생한다
- let 키워드로 선언된 변수는 선언 단계와 초기화 단계가 분리되어 진행된다
- 스코프의 시작 지점부터 초기화 시작 지점까지 변수를 참조할 수 없는 구간을 일시적 사각지대(TDZ)라고 부른다

```jsx
console.log(foo)
let foo;
console.log(foo)
foo =1;
console.log(foo);
```

## const 키워드

- const 키워드는 상수를 선언하기 위해 사용한다

### 선언과 초기화

- cosnt 키워드로 선언한 변수는 반드시 선언과 동시에 초기화해야 한다

```jsx
const foo = 1;
const bar // 에러
```

### 재할당 금지

- var 또는 let 키워드로 선언한 변수는 재할당이 자유로우나 const 키워드로 선언한 변수는 재할당이 금지된다

```jsx
const foo =1;
foo = 2;
```

- 상수는 재할당이 금지된 변수를 말한다
- const 키워드로 선언된 변수에 원시 값을 할당한 경우 원시 값은 변경할 수 없는 값이고 const 키워드에 의해 재할당이 금지되므로 할당된 값을 변경할 수 있는 방법은 없다

### const 키워드와 객체

- const 키워드로 선언된 변수에 객체를 할당한 경우 값을 변경할 수 있다

```jsx
const person = {
	name : "Lee"
}

person.name = "Kim:
console.log(person);
```

- const 재할당을 금지할 뿐 불변을 의미하지는 않는다