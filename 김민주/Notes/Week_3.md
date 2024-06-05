## Week_3
 
### 4장 - 첫 번째 프로젝트 : 할일 관리 앱

실습으로 대체

#
#
### 7장 - 타입 별칭
타입 별칭(type alias) : 타입에 의미를 부여해 별도의 이름으로 부르는 것 (using과 동일)

```typescript 
type Name = string;
let myName : Name = 'minjoo';

// 반복되는 타입 코드를 줄일 수 있다
type LogText = string | number;
function Loggin(text : LogText)
{
//..
}

let message : LogText = 'hello';
Loggin(message);
```
##### 타입 별칭과 인터페이스의 차이점
###### 타입 별칭
- 코드 에디터에서 확인 시 미리보기로 확인 가능해 편리
- 주로 일반 / 유니언/ 인터섹션 타입에 이름 짓는데 사용
- 유틸리티/ 맵드 타입은 타입별칭으로만 정의 가능
###### 인터페이스
- 상속 가능 (extends)
- 선언 병합 성질 (동일한 이름으로 인터페이스 생성 시 내용을 합친다)
#
#
### 8장 - 이넘
##### Enum : 상수 집합
```typescript 
enum Class
{
  Witch,
  Destoryer,
  Rogue
}

let myClass = Class.Rogue;
```
문자형 이넘
```typescript
// 모든 속성 값 지정 필요
enum Class
{
  Witch = 'witch',
  Destoryer = 'destroyer',
  Rogue = 'rogue',
  Engineer = 1, //< 숫자와 섞어도 된다
  Swordman = Witch + Destroyer //< 다양한 형태도 가능
}
```
const 이넘
- 결과물의 코드 양을 줄이기 위해서 사용
- 이넘의 속성 이름과 값을 연결해주는 객체를 생성하지 않고 사용되는곳에서 속성값을 바로 연결
```typescript
const enum Class
{
  Witch,
  Destoryer,
  Rogue,
  //Swordman = Witch + Destroyer 대신 이런거 불가능
}
```
문자형 enum 방식이 가장 많이 활용됨
#
#
### 9장 - 클래스
```typescript
class Person
{
// 속성 이름과 타입 정의 필요(typescript)
name : string;
skill : string;

//생성자 함수를 문법 레벨로 끌어올린 것
 constructor(name : string, skill : string)
 {
  this.name = name
  this.skill = skill
 }
}

// 상속 가능
class Developer extends Person
{
 constructor(name, skill)
 {
  super(name, skill);
 }
}

// new 로 생성
let minjoo = new Person('minjoo','fighting'); //< 클래스 인스턴스 (class instance)
let minjoo2 = new Developer('minjoo','coding');
```
##### 클래스 접근 제어자
- public : 어디서든
- private : 클래스 내부에서만 엑세스 가능
- protected : 상속받은 클래스에서까지 엑세스 가능

##### 근데 빨간줄만 띄워주고 실행을 막아주진 못함;
