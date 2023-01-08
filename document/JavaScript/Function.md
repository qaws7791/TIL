# 함수

[TOC]



## 함수 생성 및 호출

### 함수 리터럴 방식의  함수 선언

```js
function(x) { return x * x; };
```

### 함수 선언문 방식의 함수 선언

```js
function square(x) { return x * x; };
```

### ❗함수 표현식 방식의 함수 선언

```js
const square = function(x) { return x * x; };
```

### 생성자 함수를 이용한 함수 생성

```js
const square = new Function('x','return x * x'};
```

### 함수 호출

```js
square(3) // 9
```

### 인수

```js
function distance(p,q) {
	var dx = q.x - p.x;
	var dy = q.y - p.y;
	return Math.sqrt(dx*dx+dy*dy);
}
```

### 함수 선언문 호이스팅

- 변수 선언과 마찬가지로 함수 선언문을 프로그램의 첫머리로 끌어올린다
- 함수의 위치에 상관없이 함수 선언문 형태로 생성된 함수는 유효 범위가 코드의 처음부터 시작
- 함수 표현식을 권장

```js
console.log(square(5)) // TypeError
const square = function(x) { return x*x;};
console.log(square(5)) // 25
```



## 함수 특징

### 함수는 객체이다

- 함수 `square(x)`는 `function(x) {return x*x;}` 를 가리키는 일종의 객체
- 리터럴에 의해 생성되는 객체

```js
var sq = square;
console.log(sq(5)); // 25
```

### 함수는 값이다

- 변수, 배열, 프로퍼티 등에 할당 가능하다
- 함수의 인자나 리턴값으로 전달이 가능하다
- 동적 프로퍼티 할당 가능

### 함수가 가지는 기본 프로퍼티

- `length` : 함수가 기대하는 정상적인 인자의 개수
- `prototype`: 객체의 부모를 가리키는 [[Prototype]]과 다름. `constructor` 프로퍼티를 가리킴.  `constructor` 프로퍼티는 함수를 가리킴. `함수(prototype`) ↔ `constructor`

### 값에 의한 호출

- 값의 전달: 인수에 원시 값(여기서는 a = 3)을 넘기면 그 값 자체가 인자에 전달되어
  a의 값은 변하지 않는다

```
function add1(x) { return x = x + 1;}
var a = 3;
var b = add1(a);
console.log("a = " + a + ", b = " + b); // a = 3, b = 4
```

### 참조에 의한 호출

- 참조전달: 인수에 객체(여기서는 a={x:3, y:4})를 넘기면 참조 값을 p에 대입하므로 p를 수정하면 a까지 수정된다

```js
function add1(p) { p.x = p.x + 1; p.y = p.y + 1; return p; }
var a = {x:3, y:4};
var b = add1(a);
console.log(a,b); // Object {x=4, y=5} Object{x=4, y=5}
```

### 변수의 유효 범위(Scope)

**어휘적 범위**: 프로그램의 구문으로 유효 범위 지정

**동적 범위**: 프로그램 실행 중 유효 범위 지정

- 자바스크립트는 어휘적 범위 방식을 채택

**전역 변수**: 함수 바깥에서 선언된 변수. 유효 범위가 전체 프로그램

**지역 변수**: 함수 안에서 선언된 변수와 함수 인자. 유효 범위가 변수가 선언된 함수 내부

- 지역 변수의 유효 범위 안에서는 같은 이름의 전역 변수는 숨겨진다

```js
var a = "global";
function f() {
	var a = "local";
	console.log(a); // local
	return a;
}
f();
console.log(a); // global
```

### 함수 안의 변수 끌어올림

- 함수 안의 변수 선언부는 함수의 첫머리로 끌어올려진다.

### 함수 안에서 변수 선언 생략시 전역 변수

- 함수안에서 변수를 선언하지 않고 값을 대입하면 전역 변수로 선언된다.

```js
function f() {
	a = "loacl";
	console.log(a); // local
	return a;
}
f();
console.log(a); // local
```

### 블록 유효 범위

- let과 const는 ES6부터 추가된 변수 선언자로 '선언된 {...} 안'의 '블록 유효 범위'를 갖는 변수를 선언한다
- **let 선언자**: 블록 유효 범위를 갖는 지역 변수 선언
  - 변수 끌어올림(호이스팅)이 되지 않는다
- **const 선언자**: 블록 유효 범위를 가지면서 한 번만 할당 가능한 상수를 선언
  - 상수 값은 수정 불가능
  - 상수 값이 객체나 배열일 경우 프로퍼티 또는 프로퍼티 값을 수정 가능

### 함수 리터럴로 함수 정의하기

- 함수 리터럴 = 익명 함수 = 무명 함수

```js
var square = function(x) { return x * x;};
```

### 객체의 메서드

- 메서드: 객체의 프로퍼티 중  함수 객체를 값으로 담고 있는 프로퍼티
- 일반적으로 메서드가 속한 객체의 상태를 바꾸거나 이용하는 용도로 사용

```js
var circle = {
	center: { x:1.0, y:2.0 },
	radius: 2.5,
	area: function() {
		return Math.PI * this.radius * this.radius;
	}
};
```

### arguments 객체

- 함수를 호출할 떄 사용된 인자들이 배열 형태로 저장된 유사 배열 객체

```js
const add = function (a, b) {
  console.log(arguments);
  return a + b;
};

console.log(add(1)); // {0: 1} NaN
console.log(add(1, 2)); // {0: 1, 1: 2} 3
console.log(add(1, 2, 3)) // {0: 1, 1: 2, 2: 3} 3
```

### this 바인딩

- 객체 내의 메서드를 호출할 때는 해당 메서드를 호출한 객체로 바인딩
- 브라우저에서 자바스크립트 실행 시 전역 객체에 바인딩 (window 객체)
- 바인딩 하지 않으면 func2, func3의 this는 전역객체를 가리킴

```js
var value = 100;

var myObject = {
  value: 1,
  func1: function () {
    this.value += 1;
    console.log(this.value);

    func2 = function () {
      this.value += 1;
      console.log(this.value);

      func3= function () {
        this.value += 1;
        console.log(this.value);
      }
      func3() // 3. 100+2 = 102
    }
    func2() // 2. 100+1 = 101
  }
}
myObject.func1() // 1. 1+1 = 2
```

```js
var value = 100;

var myObject = {
  value: 1,
  func1: function () {
    var that = this; // this 바인딩
    this.value += 1;
    console.log(this.value);

    func2 = function () {
      that.value += 1;
      console.log(that.value);

      func3= function () {
        that.value += 1;
        console.log(that.value);
      }
      func3() // 3. 4
    }
    func2() // 2. 3
  }
}
myObject.func1() // 1. 2
```

### 생성자 함수 new

- Person() 생성자 함수의 `prototype` ->  Person.prototype 객체
- 생성된 빈 객체의 `[[prototype]]` 을  Person.prototype 객체와 연결
- 생성자 함수 호출 시에는 생성되는 객체에 this가 바인딩 

```js
var person1 = new Person('john');
//person1의 [[prototype]] ->  Person.prototype 객체
```

### 객체 리터럴 방식과 생성자 함수 방식 차이

- 객체 리터럴 방식 `변수 = {...}`은 Object.prototype을 ``__proto__`로 가짐
- 생성자 함수 방식 `변수 = new Person()`은 Person.prototype을 ``__proto__`로 가짐

### call과 apply를 통한 this 바인딩

- thisArg: func()호출에 사용할 this
- call과 apply 차이: call은 인자를 각각 넘기고, apply는 배열 형태로 넘긴다.

```js
func.call(thisArg[, arg1[, arg2[, ...]]])
func.apply(thisArg, [argsArray])
```

## 프로토타입 체이닝

- 해당 객체에 메서드나 프로퍼티가 존재하지 않으면 
  `[[Prototype]]`링크를 따라 올라가면서 프로토타입 객체에서 검색

### 객체 리터럴 방식으로 생성된 객체의 프로토타입 체이닝

- `hasOwnProperty()`는 myObject의 prototype -> Object.prototype의 메서드

```js
var myObject = {
	name: 'foo'
}
console.log(myObject.hasOwnProperty('name')); // true
```

### 생성자 함수로 생성된 객체의 프로토타입 체이닝

- `hasOwnProperty()`는 Person()의 prototype -> Person.prototype -> Object.prototype의 메서드

```js
function Person(name) {
    this.name = name;
}
var foo = new Person('foo')
console.log(foo.hasOwnProperty('name')); // true
```

### 



## 다양한 함수의 형태

### 콜백(callback) 함수

-  특정 조건, 이벤트 발생 시 호출되는 함수 (이벤트리스너)
-  함수의 인자로 넘겨져 코드 내부에서 호출되는 함수

### 즉시 실행 함수 표현 (IIFE)

- 정의와 동시에 즉시 실행되는 함수

```js
(function (x) {
    console.log(x*x);
})(5); // 25
```

### 내부 함수

- 함수 내부에서 함수를 정의
- 변수가 존재하지 않으면 자신의 부모 함수의 변수에 접근
- 내부 함수는 부모 함수 내에서만 호출 가능

```js
function parent() {
  var a = 1;
  var b = 2;
  function child() {
    var b = 3;

    console.log(a,b); 
  }
  child()
}
parent() // child() -> 1,3
child() // ReferenceError: child is not defined
```

- 함수 외부에서 내부 함수를 호출하는 방법

```js
let func_parent = function () {
  var a = 1;
  var b = 2;
  function func_child() {
    var b = 3;

    console.log(a, b);
  }
  func_child();
  return func_child;
};
var inner = func_parent(); // 내부 함수를 리턴값으로 넘겨 받음
console.log(inner); // ƒ func_child() {...}
inner(); // 1,3

```

1. inner() 실행
2. func_child() 호출
3. console.log(a, b);
4. a는 정의되어 있지 않아 부모 함수에 있는지 확인하여 있으면 사용 (클로저)
   b는 정의되어 있음
5. 1,3 출력

### 함수를 리턴하는 함수

```js
var self = function () {
	console.log('a');
	return function () {
		console.log('b');
	}
}
self = self(); // a
self(); // b
```

### 함수 리턴값

1. 리턴 값 미지정 시: 일반 함수, 메서드 -> undefined
2. 리턴 값 미지정 시: 생성자 함수 -> 생성된 객체