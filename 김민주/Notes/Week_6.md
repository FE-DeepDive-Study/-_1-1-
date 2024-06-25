## Week_5
#
#
### 17장 - 유틸리티 타입
유틸리티 타입(utility type) : 이미 정의되어있는 타입 구조를 변경하여 재사용하고 싶을 때 사용하는 타입
- 컴파일러 옵션에 ESNext 추가하여 사용
#
##### Pick
특정 타입의 속성을 뽑아서 새로운 타입을 만들어낼 때 사용
```typescript 
interface Profile
{
  id : string;
  address : string;
}

type ProfileId = Pick< Profile, 'id' >;
/*
== type ProfileId = { id : string };
*/

// 여러개 추출도 가능
type ProfileId1 = Pick< Profile, 'id' | 'name' >;
```
#
##### Omit
특정 타입에서 속성 몇개를 제외한 나머지 속성으로 새로운 타입 생성할 때 사용
```typescript 
interface Profile
{
  id : string;
  address : string;
}

type ProfileId = Omit< Profile, 'id' >;
/*
== type ProfileId = { address : string };
*/
```
#
##### Partial
특정 타입의 모든 속성을 모두 옵션 속성으로 변환한 타입 생성
```typescript 
interface todo
{
  id：string；
  title：string;
}

type OptionalTodo = Partial<Todo〉;
/*
== type ProfileId = { id?: string; address?: string; };
*/
```
- 데이터 수정하는 api 호출 또는 이미 정해진 데이터 타입을 다른 곳에서 선택적을 재사용할 때 사용
#
##### Exclude
유니언 타입을 구성하는 특정 타입을 제외할 때 사용
```typescript 
type Languages = 'C' | ']ava' | 'TypeScript' | 'React';
type TrueLanguages = Exclude< Languages, 'React' > ；
```
#
##### Record
타입 1개의 속성을 key로 받고 다른 타입 1개를 value로 받아 객체 타입으로 변환
```typescript 
type PhoneBook = Record<string, string>;
// == type PhoneBook = { [x: string] : string; }
```
#
이 외에도 다양한 유틸리티 타입 많습니다~
#
#
### 18장 - 맵드 타입
- 이미 정의된 타입을 가지고 새로운 타입을 생성할 때 사용하는 타입 문법
- 유틸리티 타입 모두 내부적으로는 맵드 타입 이용해서 구현되어있음
```typescript 
interface Hero
{
  name：string;
  skill：string;
}

type HeroPropCheck =
{
  [H in keyof Hero] : boolean;
};

/*
== type HeroPropCheck =
{
  name : boolean;
  skill : boolean;
}
*/
```
#### 매핑 수정자
- 맵드 타입으로 타입을 변환할 때 속성 성질을 변환할 수 있도록 도와주는 문법
- + - ? readonly
```typescript 
interface Hero
{
  name：string;
  skill：string;
}

type HeroPropCheck =
{
  [H in keyof Hero] ?  : boolean; //> 모두 옵셔널 속성으로 변환
  [H in keyof Hero] -?  : boolean; //> 옵셔널 속성 제거
};
```
#
#
### 19장 - 실전 프로젝트 환경 구성
