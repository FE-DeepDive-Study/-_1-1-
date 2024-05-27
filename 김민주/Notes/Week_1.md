## Week_1
 
### 1장 - 타입스크립트 소개와 배경

##### JS에 비교한 TS
- 장 : 타입 에러 사전 방지 / 자동 완성 지원
- 단 : 컴파일 단계 추가 / 코드 양 증가
#
#### JSDoc
- 자바스크립트 코드에 주석을 달아 타입 에러 사전 방지 가능
- 자동완성 지원

```javascript 
// @ts-check //< 이걸 추가하면

/** 
* @description 설명
* @param {number} a
* @param {number} b
*/
function sum(a,b)
{
return a+b;
}

sum(10,'20'); //에러 방지 가능!
``` 

- 타입스크립트 사용으로 얻는 장점과 동일하지만, 코드 양이 많아져서 타입스크립트 사용하는게 낫다
- 타입스크립트를 바로 적용하기 어려운 상황이면 대체제가 될 수 있음

#
#
### 2장 - 타입스크립트 시작하기
##### Node.js 사용 이유
- node.js 설치 시 NMP(Node Package Manager) 이 함께 설치되는데 이게 필요하다(컴파일시)
#
#
### 3장 - 타입스크립트 기초 : 변수와 함수의 타입 정의
기본적으로 변수/함수 이름 뒤에 : 을 붙여 타입을 표시

기본 타입 9가지
- string / number / boolean / object / Array / tuple / any / null / undefined
```typescript 
var name:string = 'minjoo';

// array는 2가지로 가능
var arr1:Array<string> = ['1','2'];
var arr2:string[] = ['3','4'];

// 이거 되나
var me:object = [name:string = 'minjoo', age:number = 27]

var node:null = null;

var someth:undefined;
// 이거 되나2
someth:number = 4;
``` 

함수도 동일
```typescript 
function sum( a:number , b:number, c?:number) : number
{
return a + b + c;
}

sum(1,2,3);

// optional ? 사용으로 아래도 가능
sum(2,3);

``` 
#
#
### ECT - var / let / const 차이
- var : 전역 또는 함수 범위
- let / const : 전역 또는 블럭 범위
#
- var : 업데이트O 재선언O
- let : 업데이트O 재선언X
- const : 업데이트X 재선언X
#
호이스팅(선언이 맨위로 이동되는 JS의 특징)시
- var : undefined으로 초기화
- let / const : 초기화되지 않음
#
- var / let : 선언 이후 초기화 가능
- const : 선언과 동시에 초기화 필수
