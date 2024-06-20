## Week_5
#
#
### 14장 - 타입 가드
타입 가드(type guard) : 여러개의 타입으로 지정된 값을 틀정 위치에서 원하는 타입으로 구분 ( 넓은 타입 => 좁은 타입 )

```typescript 
function updateInput( textInput : number | string | boolean )
{
  // if문이 타입 가드 역할
  if (typeof textInput === 'number')
  {
    //..
  }
}
```
##### typeof
- js꺼
- 타입을 문자열로 반환
##### instanceof
- js꺼
- 변수가 대상 객체의 프로토타입 체인에 포함되는지 확인하여 불값 반환
```typescript 
function Person(name, age)
{
  this.name = name；
  this.age = age；
}

var captain = new Person('캡틴', 100) ；

captain instanceof Person；// true
```
##### in
- js꺼
- 객체에 속성이 있는지 확인하여 불값 반환
```typescript 
function Person(name, age)
{
  this.name = name；
  this.age = age；
}

var captain = new Person('캡틴', 100) ；

'name' in captain; //true
```
##### 타입 가드 함수
- 타입 가드 역할을 하는 함수
```typescript 
interface Person
{
  name : string;
  age : number;
}

interface Developer
{
  name : string;
  skill : string;
}
function isPerson(someone： Person | Developer)： someone is Person
{
  return (someone as Person).age !== undefined;
}

function greet(someone : Person | Developer)
{
  if( isPerson(someone) )
    console.log(someone.age);
  else
    console.log(someone.skill);
}
```
##### 구별된 유니언 타입
- 유니언 타입을 구성하는 여러개의 타입을 특정 속정의 유무가 아니라 특정 속성 값으로 구분한는 타입 가드 문법
```typescript 
interface Person
{
  name : string;
  age : number;
  industry : 'common';
}

interface Developer
{
  name : string;
  age : string;
  industry : 'tech';
}

function greet(someone : Person | Developer)
{
  if( someone.industry === 'tech' )
  {
    //..
  }
}
```
#
#
### 15장 - 타입 호환
- 서로 다른 타입이 2개 있을 때 특정 타입에 다른 타입이 포함되는지
```typescript 
interface Ironman
{
  name : string;
}

class Avengers
{
  name : string;
}

let i : Ironman;
i  = new Avengers();
// 타입스크립트에서는 이게된다;
```
- => 구조적 타이핑 특성 때문에
##### 구조적 타이핑
- 타입 유형보다는 타입 구조로 호환 여부를 판별하는 언어적 특성
- 타입 스크립트는 해당 타입이 어떤 타입 구조를 갖고있는지로 타입 호환 여부를 판단
###### 이넘 타입은 같은 속성과 값을 가져도 이넘 타입간에는 서로 호환되지 않는다
#
#
### 16장 - 타입 모듈
- 모듈 : 프로그래밍 관점에서 특정 기능을 갖는 작은 단위의 코드
- js 모듈 : 초창기에는 모듈 지원X => Common.js Require.js 대표적인 모듈
##### import / export
```typescript
//math.js
function sum(a,b)
{
  return a + b;
}
// 이렇게 하면 다른 파일에서 불러와서 사용 가능
export(sum);
// default 붙이면 이 파일에서 이거 하나만 내보내겠다는 뜻
export default sum;

//==========================================
import { sum } from './math.js';

// default 면 아래와 같이 임포트
import sum from './math.js';

// as로 함수 이름 변경하여 사용 가능
import { sum as add } from './math.js';

// *로 모두 가져오기 가능
import * as myMath from './math.js';  //< myMath는 namespace같이 사용

console.log(sum(10,20));
```
- import와 import type은 그냥 코딩컨벤션 따라서 결정
##### Barrel
- 여러개의 파일에서 가져온 모듈을 하나의 통처럼 관리
```typescript
// ./hero/index.ts
import { Banner } from './hulk'；
import { Tony } from './ironman'；
import { Steve } from './captain'；

// 이런식으로
export { Banner, Tony, Steve }；
```
