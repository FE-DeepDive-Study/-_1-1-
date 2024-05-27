## Week_2
 
### 4장 - 첫 번째 프로젝트 : 할일 관리 앱

실습으로 대체

#
#
### 5장 - 인터페이스
인터페이스 : 객체 타입 정의

##### 인터페이스로 타입을 정의할 수 있는 부분
- 객체의 속성과 속성 타입
- 함수의 파라미터와 반환 타입
- 합수의 스펙 (파라미터 개수와 반환값 여부 등)
- 배열과 객체를 접근하는 방식
- 클래스

```typescript 
interface User
{
  name:string;
  age:number;
  cntry?:string;
}

function LogAge(user:User)
{
  console/log(user.age);
}

function GetUser(user:User):User
{
  return user;
}

let user:User = {name:'minjoo', age:27};

LogAge(user);

let me = GetUser(user);
let me2 = GetUser({name:'minjoo', age:27});

//인터페이스에서의 타입 지정으로 아래는 에러
let user1:User = {name:'minjoo', age:'27'};

//옵셔널 사용으로 가능
let user2:User = {name:'minjoo', age:27, cntry:'kr'};

```
상속도 가능
```typescript 
interface Amimal
{
  name:string;
  age:number;
}

interface Dog extends Animal
{
  skill:string;
}

let mint:Dog = {name:'mint',age:12,skill:'bark'};

// 인덱싱은 이렇게 가능
console.log(mint['name']); //< mint

```
map처럼 사용
```typescript 
interface AgeMap
{
  [index:string]:number;
}

let ages: AgeMap = {minjoo:27};
let age = ages['minjoo'];
```

#
#
### 6장 - 연산자를 사용한 타입 정의
##### Union : 여러개의 타입중 한개만 사용 |
```typescript 
function LogSomthing(content: string | number)
{
  console.log(content);
}

// 둘 다 가능
LogSomthing(100);
LogSomthing('minjoo');
```
- 중복 코드 줄일 수 있음
- any 사용보다 타입 정확하게 사용 가능
#
인터페이스도 사용 가능 (in, typeof)
```typescript
interface Dog
{
  name:string;
  skill:string;
}

interface Cat
{
  name:string;
  personality:string;
}

function LogSomthing(content : Dog | Cat)
{
  if('skill' in content)
  {
    console.log(content.skill);
  }
  if('personality' in content)
  {
    // typeof 으로 타입 구분 가능
    if(typeof content.personality === 'string')
    {
      console.log(content.personality);
    }
  }
}
```
#
##### Intersection type : 타입2개를 합쳐서 하나로 사용 &
```typescript
interface Dog
{
  skill:string;
}

interface Cat
{
  personality:string;
}

function LogSomthing(content: Dog & Cat)
{
  console.log(content.skill);
  console.log(content.personality);
}

// 이런식으로
LogSomthing(skill:'bark', personality:'outgoing');
```

#
#
### ECT - == / === 차이
- 책 예제에 === 이 사용되어있는데 초면이어서 찾아봄
- JS는 타입이 잘 명시되어있지 않고 동적으로 변하기 때문에 구분
##### == : 느슨한 비교 / === : 엄격한 비교
```typescript
if(1 == '1'); //< true
if(1 === '1'); //< false
```
