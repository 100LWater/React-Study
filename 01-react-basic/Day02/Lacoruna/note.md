# Day 2
강의의 3단원 STATE를 시청하며 공부.

## `React.useState()`
React.useState()는 리액트에서 상태(state)를 관리할 수 있게 해주는 가장 기본적인 Hook이다.

```jsx
const [state, setState] = React.useState(initialValue);
```
- state: 현재 상태 값
- setState: 상태를 변경하는 함수
- initialValue: 초기 상태 값

## JSX에서의 HTML 속성 변환
React의 JSX에서는 for과 class 같은 JavaScript 예약어와 겹치는 HTML 속성을 그대로 사용할 수 없다.  
대신에 React에서 특별히 지정한 대체 이름을 사용해야 한다.
| HTML 속성 | JSX에서 사용하는 이름 | 이유                             |
| ------- | ------------- | ------------------------------ |
| `class` | `className`   | `class`는 JS의 예약어               |
| `for`   | `htmlFor`     | `for`도 JS 예약어이며 label과 연결 시 사용 |


## JSX 안에서 주석
### 1. JSX 바깥쪽
JSX 바깥은 그냥 일반 자바스크립트 주석을 사용하면 된다.

### 2. JSX 내부 (태그 사이)
JSX 안에서 주석을 쓸 때는 중괄호 안에 JavaScript 주석({/* */}) 을 넣어야 한다.
```jsx
return (
  <div>
    {/* 이것은 JSX 안의 주석입니다 */}
    <h1>Hello</h1>
  </div>
);
```

## 자바스크립트 함수 인자 전달 방식
| 데이터 타입                                                              | 전달 방식           | 설명                          |
| ------------------------------------------------------------------- | --------------- | --------------------------- |
| **기본형(Primitive)**<br>숫자, 문자열, 불리언, null, undefined, symbol, bigint | **값 복사**        | 새로운 복사본이 함수에 전달됨            |
| **참조형(Reference)**<br>객체, 배열, 함수                                    | **참조값(주소)의 복사** | 객체 자체가 아닌 참조값(주소)을 복사해서 전달됨 |

### 핵심 요약
항상 "값"으로 전달됨
- 기본형: 값 자체 복사
- 참조형: 참조(주소)를 값으로 복사 → 내부 수정은 가능하지만, 참조 변경은 외부에 영향 없음