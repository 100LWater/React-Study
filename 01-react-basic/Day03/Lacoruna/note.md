# Day 3
- props
- create-react-app

## CDN
### CDN이란?
CDN은 Content Delivery Network의 약자로, 전 세계에 분산된 서버들을 통해 빠르고 안정적으로 파일을 전달해주는 시스템이다.
React, jQuery, Bootstrap 같은 라이브러리를 웹사이트에 설치하지 않고 바로 사용하는 방식이 CDN 방식이다.

### 장점
| 장점     | 설명                                          |
| ------ | ------------------------------------------- |
| 빠른 시작  | 설치 없이 `<script>` 태그로 바로 사용 가능               |
| 쉬운 테스트 | 실습용 HTML 파일에 붙여서 바로 실험 가능                   |
| 캐싱 효과  | 여러 사이트에서 같은 CDN을 쓰면 브라우저가 이미 다운로드한 파일을 재사용함 |

### 단점
| 단점        | 설명                                                    |
| --------- | ----------------------------------------------------- |
| 느린 경우 있음  | 외부 서버가 느리거나 차단되면 작동 안 할 수도 있음                         |
| 버전 관리 어려움 | 버전 명시를 안 하면 최신 버전으로 바뀔 수 있음                           |
| 실무 비적합    | 규모가 커지면 로컬 설치 및 번들링이 필요함 (예: npm + webpack + vite 사용) |

## Props
Props(properties)는 컴포넌트에 데이터를 전달하기 위한 객체이다.
함수의 매개변수처럼 부모 → 자식 컴포넌트로 값을 전달한다.

```jsx
// 기본 예시
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

// 구조 분해 방식
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

// 사용
<Greeting name="Lacoruna" />
```

## Props Type 지정 (PropTypes)
React는 기본적으로 타입 검사를 안 하기 때문에, 실수를 방지하려면 prop-types를 사용해서 타입을 지정할 수 있다.

### 설정 방법
- npm 사용 시: `npm install prop-types`
- CDN 방식: `<script src="https://unpkg.com/prop-types/prop-types.min.js"></script>`

### 사용 예시
```jsx
import PropTypes from 'prop-types';

function Greeting({ name, age }) {
  return <h1>{name} is {age} years old</h1>;
}

Greeting.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number,
};
```

## Create React App
Create React App은 **React 프로젝트를 빠르게 시작할 수 있게 해주는 공식 툴(템플릿 생성기)**이다.

### 🛠️ 설치 및 실행 방법
```bash
npx create-react-app my-app
cd my-app
npm start
```
- npx: 설치 없이 실행하는 npm 명령어
- my-app: 생성할 프로젝트 폴더 이름
- npm start: 개발 서버 실행 (http://localhost:3000)

## CSS Modules
CSS Modules는 React에서 CSS 클래스가 컴포넌트마다 겹치지 않도록 하기 위한 방식이다.
보통은 **CSS 클래스 이름이 전역(global)**이라서 충돌이 날 수 있는데, CSS Modules를 쓰면 이 문제를 쉽게 해결할 수 있다.

### 사용 방법 (React 기준)
#### 1. 파일 이름을 모듈형으로 작성

```plaintext
MyComponent.module.css
```

#### 2. JSX에서 불러와서 객체처럼 사용

```jsx
import styles from './MyComponent.module.css';

function MyComponent() {
  return (
    <div className={styles.box}>
      Hello Module CSS!
    </div>
  );
}
```

#### 3. CSS 파일 내부

```css
/* MyComponent.module.css */
.box {
  background-color: tomato;
  color: white;
}
```
이렇게 하면 box 클래스는 자동으로 MyComponent_box__1a2b3 같은 고유한 이름으로 바뀐다.
그래서 다른 컴포넌트의 box 클래스와 충돌하지 않는다.

### 🧠 왜 써야 할까?
| 일반 CSS 문제점          | CSS Module의 해결책   |
| ------------------- | ----------------- |
| 클래스 이름 충돌 가능성       | 자동으로 고유 이름 생성     |
| 전역 스타일 오염           | 파일마다 스코프가 독립적     |
| 큰 프로젝트에서 스타일 관리 어려움 | 컴포넌트별로 깔끔하게 분리 가능 |

