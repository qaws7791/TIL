---
description: javascript에 대한 페이지
---

# ⚙ Javascript

## 프로그래밍 언어란

### 프로그래밍 언어 정의

* 프로그래밍 언어: 컴퓨터 프로그램을 작성하기 위한 언어
* 컴퓨터는 기계어만 이해할 수 있다

### 컴파일 언어 vs 인터프리터 언어

* 컴파일: 소스 코드 -> 기계어로 번역
* 컴파일러: 컴파일을 수행하는 소프트웨어
* 컴파일 언어: C, C++, Java, objective C 등
* 인터프리터 언어: 한 줄마다 기계어로 번역해서 실행하는 프로그래밍 언어
* 인터프리터: 프로그램을 번역해서 실행시키는 소프트웨어

### 프로그래밍 언어 유형

* 절차적 언어
* 객체 지향 언어
* 함수형 언어
* 논리형 언어

### 자바스크립트 특징

#### 인터프리터 언어이다

* 웹 브라우저에 JIT 컴파일러(Just In Time Compiler) 내장으로 빠른 실행 속도

#### 동적 프로토타입 기반 객체 지향 언어이다

* 프로토타입을 상속하는 프로토타입 기반 객체 지향 언어

#### 동적 타입 언어이다

* 프로그램 실행 도중 변수에 저장되는 데이터 타입에 따라 타입이 동적으로 바뀌는 언어

#### 함수가 일급 객체이다

* 자바스크립트의 함수는 객체이다
* 함수에 함수를 인자로 넘길 수도 있다
* 함수형 프로그래밍 가능

#### 함수가 클로저를 정의한다

* 자바스크립트의 함수는 클로저(closure)를 정의
* 클로저를 통해 변수를 은닉하거나 영속성을 보장하는 등의 다양한 기능 구현

#### 자바스크립트의 기술적 요소

**1. ECMAScript(코어 언어)**

**2. 클라이언트 측의 자바스크립트 고유 기술**

웹브라우저의 주요 API

* Window 인터페이스 : 브라우저 및 창 조작
* DOM : HTML 문저 제어
* XMLHttpRequest : 서버와 비동기 통신

HTML5의 주요 API

* Drag and Drop : 드래그와 드롭으로 데이터 전달
* Blob : 이진 데이터 조작
* File : 로컬 파일 시스템 읽기 쓰기
* Web Workers : 여러 프로그램을 멀티 스레드 병렬 처리
* Web Storage : 데이터를 로컬에 저장
* indexed Database : 로컬에 키-값 타입의 관계형 데이터베이스 기능 제공
* WebSockets : 서버와 양방향 통신
* Geolocation : GPS 등의 위치 정보 기능
* Canvas : 2차원, 3차원의 그래픽스 기능

**3.서버 측의 자바스크립트 고유 기술**

* Node.js

## Statements(구문)과 declarations(선언)은 다르다

### declarations

"binding identifiers to values"

> 아래와 같이 단일 문이 필요한 곳에서 사전적 선언은 불가능하다.

```javascript
if (condition) let i = 0; 
// Uncaught SyntaxError: Lexical declaration cannot appear in a single-statement context
```

```javascript
if (condition) var i = 0;
//It is possible;
```

### statements

"carrying out actions"

> 단일 문도 가능하지만, 보통 블록과 함께 사용할 수 있다.

```javascript
for (initialization; condition; afterthought)
  statement
```

```javascript
if (condition)
  statement1
else
  statement2
```

* `var`은 특이 케이스로 `statement`이다.

> 정상적인 어휘적 범위를 가지지 않는다. (전역 변수, 선언 블록 외부 호출 등)
>
> 변수 재선언 가능

### 구문과 선언의 구분

* Control flow
  * `return`
  * `break`
  * `continue`
  * `throw`
  * `if...else`
  * `swich`
  * `try...catch`
* Declaring variables
  * `var`
  * `let` -> **declarations**
  * `const` -> **declarations**
* Functions and classes
  * `function` -> **declarations**
  * `function*` -> **declarations**
  * `async function` -> **declarations**
  * `async function*` -> **declarations**
  * `class` -> **declarations**
* Iterations
  * `do...while`
  * `for`
  * `for...in`
  * `for...of`
  * `for awit...of`
  * `while`
* Others
  * `Empty`
  * `Block`
  * `Expression statement`
  * `debugger`
  * `export` -> **declarations**(모듈 최상단에서만)
  * `import` -> **declarations**(모듈 최상단에서만)
  * `label`
  * `with`

## 조건문

### if 문

* 지정된 `condition`의 값이 `truthy`하면 `statement1`구문을 실행하고,
* `falsy`하면 `statement2` 구문이 실행된다

```javascript
if (condition)
  statement1

// With an else clause
if (condition)
  statement1
else
  statement2
```

* if 문을 중첩할 수 있다.
* `elseif`가 아닌 `else if`로 뛰어쓰기에 주의해야 한다.

```javascript
if (condition1)
  statement1
else if (condition2)
  statement2
else
  statementN
```

### Switch 문

* 표현신을 평가하여 평가된 값이 `case`와 일치하면 그 case의 구문을 실행하고 아래로 이동한다.
* break가 없으면 모든 `case`를 위에서 부터 아래로 검사한다.
* 모든 `case`가 일치하지 않으면 `default`의 구문을 실행한다.

```javascript
switch (expression) {
  case value1:
    //Statements executed when the
    //result of expression matches value1
    [break;]
  case value2:
    //Statements executed when the
    //result of expression matches value2
    [break;]
  ...
  case valueN:
    //Statements executed when the
    //result of expression matches valueN
    [break;]
  [default:
    //Statements executed when none of
    //the values match the value of the expression
    [break;]]
}
```

## 반복문

### break:

* 반복문, `switch`문, `label`문을 종료하고 다음 문으로 이동

### continue:

* 현재 또는 레이블이 지정된 반복문에소 현재 반복을 종료하고 다음 반복을 진행

###

### while 문

* 조건이 참인지 먼저 확인하고, 참이면 구문이 실행된다. 조건이 거짓이 되면 반복이 끝난다.

```javascript
 while (condition)
      statement
```

### do...while

* 조건이 거짓일 때까지 구문을 실행한다.
* while문과 달리 구문이 먼저 실행된다. 따라서 최소 1번 구문이 실행된다.

```javascript
do
  statement
while (condition);

```

### for 문

* 세개의 선택식으로 이루어진 반복문
* `initialization`: 식 또는 변수를 선언
* `condition` : 매 반복될 때마다 평가되는 식. 평가 결과가 참이면 구문을 실행하고, 거짓이면 구문을 나간다.
* `final-expression`: 매 반복된 후 평가할 식.
* 실행 순서: `initialization` -> `condition===true` -> `statement` -> `final-expression`

```javascript
for ([initialization]; [condition]; [final-expression])
	statement

```

### for...in 문

* 객체에서 열거 가능한 속성들을 반복
* 속성에 대한 값은 object\[variable]로 접근 가능

```javascript
for (const variable in object) {
  statement
}
```

### for...of 문

* 반복 가능한 객체에 대해 각 개별 속성값을 반복
* Array, Map, Set, String 등

```javascript
for (variable of iterable) {
  statement
}
```

## 구조적 분해

### 객체 구조 분해

* 구조 분해된 name과 age가 바뀌어도 원래 객체의 값에 영향을 주지 않는다.
* ```javascript
    const user = {
      name: "foo",
      age: 20,
    };
    let { name, age } = user;
    console.log(name, age); // foo 20
    name = "bar";
    age = 24;
    console.log(name, age); // bar 24
  ```
*   객체를 분해하여 인자로 넘기거나, 구조 분해하여 가져올 수 있다.

    ```javascript
    const printName = ({ name }) => {
        console.log(`Name is : ${name}`);
    };
    printName(user);
    ```

    ```javascript
    const user = {
            name: "foo",
            age: 20,
            favorite: {
              sport: "soccer",
              food: "cake",
            },
          };
    
    const printFavoriteSport = ({ favorite: { sport } }) => {
    	console.log(`Favorite sport is ${sport}`);
    };
    printFavoriteSport(user);
    ```

### 배열 구조 분해

```javascript
const arr = [1, 2, 3, 4, 5];
const [first, second] = arr;
const [, , third] = arr;
const [last] = [...arr].reverse();
console.log(first, second, third, last); // 1 2 3 5
```

### 객체 리터럴 개선

```javascript
const name = "foo";
const age = 20;
const favorite = {
    sport: "soccer",
    food: "cake",
};
const printFavoriteSport = ({ favorite: { sport } }) => {
    console.log(`Favorite sport is ${sport}`);
};

const user = { name, age, favorite, printFavoriteSport };
console.log(user);
```

## 스프레드 연산자(...)

spread 프로퍼티를 제외한 iterable 객체 전용

*   기존에 함수의 인수로 배열을 사용하기 위해 썼던 `apply()`를 대체할 수 있다.

    ```javascript
    function sum(x, y, z) {
        return x + y + z;
    }
    const numbers = [1, 2, 3];
    console.log(sum(numbers));
    console.log(sum(numbers[0], numbers[1], numbers[2]));
    console.log(sum(...numbers));
    console.log(sum.apply(null, numbers));
    ```

### 배열 합치기 (배열 리터럴 전개)

```javascript
const numbers = [1, 2, 3];
const numbers2 = [4, 5, 6];
console.log([numbers, numbers2]); // [[1,2,3],[4,5,6]]
console.log([...numbers, ...numbers2]); // [1,2,3,4,5,6]
```

### 문자열을 배열로 분해하기

```javascript
const greeting = "Hello";
const arrayOfChars = [...greeting];
console.log(arrayOfChars); //  ['H', 'e', 'l', 'l', 'o']
```

### 배열 복사

> ❗︎단 1레벨 깊에서만 효과적으로 동작

```javascript
const numbers = [1, 2, 3];
const numbers2 = numbers;
numbers2.push(4);
console.log(numbers); // [1,2,3,4]
console.log(numbers2); // [1,2,3,4]
```

```javascript
const numbers = [1, 2, 3];
const numbers2 = [...numbers];
numbers2.push(4);
console.log(numbers); // [1,2,3]
console.log(numbers2); // [1,2,3,4]
```

### 객체 리터럴 전개

```javascript
const user = {
    name: "foo",
    age: 20,
};
user2 = { ...user };
user2.name = "bar";
console.log(user.name, user2.name); // foo bar
```

## 나머지 매개변수(...args)

함수에서 정해지지 않은 수의 매개변수를 배열로 받을 수 있다.

```javascript
function sum(...theArgs) {
  let total = 0;
  for (const arg of theArgs) {
    total += arg;
  }
  return total;
}

console.log(sum(1, 2, 3));
// expected output: 6

console.log(sum(1, 2, 3, 4));
// expected output: 10
```

* 나머지 매개변수는 매개변수 앞에 `...`을 붙여 사용한다
* 나머지 매개변수를 사용하면 모든 후속 매개변수를 배열에 저장하고
* 마지막 매개변수 하나에만 나머지 매개변수로 설정할 수 있다.

```javascript
function printArgs(first, second, ...moreArgs) {
	console.log(first, second) // 1 2
	console.log(moreArgs) // [3,4,5]
}
printArgs(1,2,3,4,5)
```

### Arguments와 나머지매개변수의 차이점

* `Arguments`는 배열이 아니다 -> \[\[Prototype]]: Object 이다
  * `callee`와 같은 기능도 있다.
  * Array 메서드를 사용하기 위해 변환이 필요하다.
  * 전체 매개변수를 포함한다.
* `나머지매개변수`는 실제 배열이다 -> \[\[Prototype]]: Array 이다
  * 사용자가 정의한 매개변수를 제외한 나머지만을 가진다.

![image-20230110191822853](document/JavaScript/readme.assets/image-20230110191822853.png)

## 클래스

### 프로토타입을 통한 객체 생성

> User.prototype.printName()을 변경하면 참조중인 모든 User 객체의 메서드가 변경됨

```javascript
function User(name, age) {
    this.name = name;
    this.age = age;

    User.prototype.printName = function () {
        console.log(`name: ${name}, age: ${age}`);
    };
}
const foo = new User("foo", 20);
foo.printName();
console.log(foo);

```

### 클래스를 통한 객체 생성

> 이미 생성된 객체는 User를 변경해도 영향을 받지 않음

```javascript
class User {
    constructor(name, age) {
      this.name = name;
      this.age = age;
    }
    printName() {
      console.log(`name: ${this.name}, age: ${this.age}`);
    }
}
const foo = new User("foo", 20);
foo.printName();
```

## ES6 모듈

*   모듈에서 외부로 내보내기

    ```javascript
    export const function_1(args) => {...}
    ```
*   모듈에서 하나만 내보내기

    ```javascript
    const function_2(args) => {...}
    export default function_2;
    ```
*   모듈에서 가져오기

    ```javascript
    import { function_1 } from './module';
    import { function_1 as func_1 } from './module';
    import function_2 from './module';
    ```

### 명령형 프로그래밍

하고자 하는 일에 대해 구문의 관점에서 연산을 설명하는 프로그래밍 방식

달성해야 할 명령에 대채 순차적으로 작성

### 선언적 프로그래밍

어떻게 결과가 나타나야 하는지를 설명하는 프로그래밍 방식

### 불변성

불변성을 위해 데이터의 변경이 필요하다면 복사본을 만들어 사용한다.

### 객체 불변성

* `Object.assign(target,...source)`는 객체를 복사하기 위해 사용되지만
* source값이 참조 값이면 참조 값이 복사되어 얕은 복사가 된다. 따라서 아래의 `obj3`처럼 복사해야 한다.

```javascript
let obj1 = { a: 0, b: { c: 0 } };
let obj2 = Object.assign({}, obj1);
let obj3 = JSON.parse(JSON.stringify(obj1));
obj1.a = 1;
obj1.b.c = 1;
console.log(JSON.stringify(obj1)); // {"a":1,"b":{"c":1}}
console.log(JSON.stringify(obj2)); // {"a":0,"b":{"c":1}}
console.log(JSON.stringify(obj3)); // {"a":0,"b":{"c":0}}
```

### 순수함수를 통한 객체 불변성

* 순수함수의 규칙
  1. 하나 이상의 파라미터를 가진다.
  2. 값이나 함수를 반환한다.
  3. 인자 또는 함수 외부의 변수를 변경하지 않는다.
  4. 입출력을 하지 않는다.

```javascript
const user = {
    name: "foo",
    age: 20,
    auth: {
        canRead: false,
        canWrite: false,
    },
};
const grantAuth = (user) => ({ㅓ
    ...user,
    auth: {
        canRead: true,
        canWrite: true,
    },
});
console.log(grantAuth(user));
console.log(user);
```

### 배열 불변성

```javascript
let arr = [0, 0, 0];
let arr2 = arr;
let arr3 = [...arr];
arr[0] = 1;
arr2[1] = 2;
arr3[2] = 3;
console.log(arr); // [1, 2, 0]
console.log(arr2); // [1, 2, 0]
console.log(arr3); // [0, 0, 3]
```

## 실행 컨텍스트

* 자바스크립트 코드를 실행하기 위한 가상의 환경
* global, function, eval
* 전역 공간(global)은 하나만 가진다.

```javascript
// ---- 1번
var a = 1;
function outer() {
	function inner() {
		console.log(a); //undefined
		var a = 3;
	}
	inner(); // ---- 2번
	console.log(a); // 1
}
outer(); // ---- 3번
console.log(a); // 1
```

![image-20230523120018928](readme.assets/image-20230523120018928.png)

### 실행 컨텍스트의 정보

1. VariableEnvironment -> 식별자 정보, 선언 시점의 LexicalEnvironment 스냅샷
2. LexicalEnvironment -> 실시간 변경사항 저장, 레코드를 수집하여 호이스팅
   1. environmentRecord
   2. outerEnvironmentReference -> 실행될 때의 바깥 환경 정보
3. ThisBinding -> this가 가리키는 객체

### 런타임

* Node에서 전역객체: global
* 브라우저에서 전역객체: window

### Method

* 함수의 this: 함수를 실행하는 전역 환경의 객체가 this가 된다. (전역객체)
* 메서드의 this: 메서드는 객체의 속성인 함수이므로 실행하는 객체가 this가 된다. (객체)
* ❗객체 안이어도 함수로서 실행하면 전역 객체를 this로 받는다.

```javascript
      var obj1 = {
        outer: function () {
          console.log(this); // obj1
          var innerFunc = function () {
            console.log(this); 
          };
          innerFunc() // window
          innerFunc.apply(this); // outer
          var obj2 = {
            innerMethod: innerFunc,
          };
          obj2.innerMethod(); //obj2
        },
      };
      obj1.outer();
```

## 동기와 비동기

**동기**

* 순서대로 작업을 처리하여 작업이 끝나지 않으면 기다리는 방식
* 비동기: 작업을 시작하고 끝날 때까지 다른 작업을 수행할 수 있는 방식
* 콜백지옥과 효율적인 작업 시간 소모를 위해 비동기의 필요성

### 비동기

* 순서를 보장하지 않는다. 작업이 언제 끝날지 알 수 없기 때문이다.
* 따라서 비동기 작업의 동기적 표현이 필요하다

#### Promise

* Promise에는 함수를 전달한다. 이때 함수를 `executor(실행자)`라고 한다.
* 실행자 내부에서는 작업이 종료되면 `resolve`와 `reject` 중 하나를 반드시 호출 해야 한다.
* `resolve(value)` - 작업이 성공적으로 끝났을 때 값과 함께 호출
* `reject(error)` - 작업이 실패했을 때 에러와 함께 호출
* Promise의 3가지 상태
  1. 대기(pending): 초기 상태
  2. 이행(fulfilled): 성공
  3. 거부(rejected): 실패

#### Promise의 3가지 상태

*   Promise.then() 작업이 완료되었을 때와 실패 했을 때 실행할 두 개의 콜백 함수를 받고 Promise를 반환

    ```javascript
    promise.then((value)=>{}, (reason)=>{});
    ```
*   Promise.catch() 작업이 실패 했을 때 실행할 콜백 함수를 받아 실행하고 새로운 Promise를 반환

    ```javascript
    promise.catch((error)=>{})
    ```
*   Promise.finally() 작업이 성공했든 실패했든 최종적으로 실행되는 코드

    ```javascript
    promise.finally(()=>{});
    ```

```javascript
myPromise
.then(response => {
  doSomething(response);
})
.catch(e => {
  returnError(e);
})
.finally(() => {
  runFinalCode();
});
```

```mermaid
stateDiagram-v2
direction LR
    state "(pending) Promise" as start
    state "(settled) .then()" as then
    state "(settled) .catch()" as catch
    start --> then : fulfill
    start --> catch : reject
    state "async actions" as actions
    then --> actions
    state "error handing" as errors
    catch --> errors
    state "(pending) Promise" as end
    then --> end : return
    catch --> end : return
```

```javascript
const myPromise = new Promise((resolve, reject) => {
    if(성공) {
        resolve('성공')
    } else {
        reject("실패")
    }
});
```

```javascript
myPromise
.then((res)=> console.log(res)) // 성공
.catch((error)=> console.log(error)) // 실패

```

