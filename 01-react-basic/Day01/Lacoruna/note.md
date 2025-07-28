# Day 1

## React 사용을 위한 설정
```html
    <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
```
- react는 리액트의 컴포넌트 구성, JSX 처리, 상태 관리, 훅(hooks) 등의 핵심 기능을 제공한다.
- react-dom은 react로 만든 컴포넌트를 브라우저의 실제 DOM에 렌더링하는 역할을 한다.

## React
리엑트는 JS로 HTML을 생성하도록 해준다.

## JSX
JSX는 JavaScript XML의 약자이다.
JavaScript 안에서 HTML처럼 보이는 코드를 작성할 수 있게 해주는 문법을 확장한 것이다.
JSX에서 리액트는 *소문자*로 시작하는 태그는 *HTML 태그*로, *대문자*로 시작하는 태그는 *사용자 정의 컴포넌트*로 인식.
```jsx
const element = React.createElement('h1', null, 'Hello, world!');
const element = <h1>Hello, world!</h1>;
```

## Babel
Babel은 JSX처럼 브라우저가 이해하지 못하는 최신 자바스크립트 문법을 변환해주는 도구이다.
```jsx
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

<script type="text/babel">
  const App = () => <h1>Hello</h1>;
</script>
```


## 컴포넌트 렌더링 3가지 방식
### 1. React.createElement
가장 기본적인 React의 사용 방식으로, React.createElement를 통해 직접 DOM 요소를 생성하는 방법.
```jsx
const h3 = React.createElement("h3", {
  id: "asdf",
  style: { color: "red" },
  onMouseEnter: () => console.log("mouse enter"),
}, "hahaha");

const btn = React.createElement("button", {
  onClick: () => console.log("clicked")
}, "Click me");

const container = React.createElement("div", null, [h3, btn]);
```

### 2. JSX 사용 (HTML처럼 작성)
JSX는 JavaScript 문법 안에서 HTML처럼 UI를 작성할 수 있게 해주는 문법을 확장한 것.
브라우저는 JSX를 이해하지 못하기 때문에 Babel을 통해 React.createElement로 변환됨.
```jsx
const Title = (
  <h3 id="title" onMouseEnter={() => console.log("mouse enter")}>
    Title
  </h3>
);

const Btn = (
  <button
    style={{ backgroundColor: "tomato" }}
    onClick={() => console.log("jsx clicked!!")}
  >
    Click me!!!
  </button>
);

const container = React.createElement("div", null, [Title, h3, btn, Btn]);
```

### 3. JSX + 함수형 컴포넌트
JSX를 함수형 컴포넌트로 추상화하면, 재사용이 가능하고 코드 구조가 더 깔끔해짐.
함수형 컴포넌트를 사용하기 위해선 태그의 첫 글자가 대문자여야 함.

```jsx
const Title = () => (
  <h3 id="title" color="red" onMouseEnter={() => console.log("mouse enter")}>
    Title
  </h3>
);

const Btn = () => (
  <button
    style={{ backgroundColor: "green" }}
    onClick={() => console.log("jsx clicked!!")}
  >
    Click me!!!
  </button>
);

const Container = (
  <div>
    <Title />
    <Btn />
  </div>
);
```