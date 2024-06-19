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
