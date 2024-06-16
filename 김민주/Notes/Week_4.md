## Week_4
#
#
### 11장 - 두 번째 프로젝트: 전화번호부 앱
실습으로 대체
#
#
### 12장 - 타입 추론
- 타입스크립트가 코드를 해석하여 적절한 타입을 정의하는 동작
- 선언하는 시점에 할당된 값 기반으로 추론된다
```typescript
function sum(a : number)
{
  let c = '10';
  return a + c;
  // 이러면 반환 타입 string으로 추론됨 js 내부적으로 숫자를 문자열로 변환
}
```
#
#
### 13장 - 타입 단언
- as
- 타입 스크립트의 타입 추론에 기대지 않고 직접 타입을 명시하여 강제하는 것 -> 에러에 취약
- rhs에만 사용 가능
```typescript
// 컴파일 시 해당 코드의 타입 검사를 하지 않음
let myName = 'minjoo' as string;
```
```typescript
interface Person
{
  name : string;
  age : number;
}

// 이런식으로 선언하는 시점에 정의 가능
// 선언하는 시점에 멤버 속성 정의 하지 않고 추후에 추가할 수 있어짐
var me = {} as Person
me.name = 'minjoo'
me.age = 27;
```
```typescript
// 변수나 함수 호출 결과에도 사용 가능
function GetId(id)
{
//..
  return id;
}

let myId = GetId('minjoo') as number
```
중첩해서도 사용 가능하다
```typescript
// 이런것도 가능은 하다~ 의미는 없음
let num = ( 10 as any ) as number;
```
##### null 아님 보장 연산자 !
```typescript
function shuffleBooks( books : Books | null )
{
  // ! 사용으로 books는 null이 될 수 없다는걸 말해줌 
  let res = books!.shuffle();
  return res;
}
```
타입 관점에서 널이 아닌것을 보장하는거지 실제로 null 들어오면 에러..
