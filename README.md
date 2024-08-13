# vue.js로 시작하는 SPA 개발 강의 내용

## 2.1 Hello World로 만나는 Vue
- 유지보수 측면에서 vue가 편함
- plain js VS jquery VS vue.js를 했을 때 속도 측면에서 jquery가 가장 느리고 vue.js는 외부에서 vue.js 파일을 외부에서 가져옴에도 불구하고 plain js와 속도가 비슷하다.

## 3.1 Vue Instance
- Vue Instance는 MVVM 패턴의 View Model에 해당
  - View(DOM)와 Model(Plain Javascript Object) 사이의 통신을 가능하게 해주는 역할
- Vue Instance는 Binder를 가지고 있어, View와 Model을 서로 맞춰줌.(동기화)
- Vue의 구성요소들은 Model의 변화에 반응적
- Virtual Instance

## 3.2 Vue Lifecycle

## 3.3 Instance Properties
- el, data 같은 것들
- Vue Instance가 만들어질 때, Option Object(Properties)를 받을 수 있다.
- Instance의 특성을 지정할 수 있게 해준다.

### Data
- 컴포넌트 안에서 사용할 변수를 생성하고 지정할 수 있다.
  - 단, 한 컴포넌트에서 정의된 Data는 그 컴포넌트에서만 접근 가능하다.
- 컴포넌트가 살아있는 한, 그 변수들은 변경사항들을 모두 반영하고, 접근 가능하다.

### Method
- Vue Instance를 사용하면서 활용 가능한 함수들

### Lifecycle Hooks
- Vue Instance의 Lifecycle Hook을 활용 가능하다.
- 특정 Object의 초기화나 삭제에 유용하다.

### Computed
- 계산된 값을 보여주는 Instance Property
- computed는 Dependency를 가지고 있는 변수의 변화에 따라 Re-render하는 것
- Method는 그것과 상관없이 Re-render할 때마다 계속 바뀌는 것

### Watchers
- 변수의 이전과 이후 상태를 비교해서 필요한 로직을 수행할 수 있다.
  
## 주요 문법
### Template
- Vue.js만의 특수한 문법으로 틀만 짜면, 그 틀은 실제 보여지는 화면을 위한 HTML로 Compile된다.
  - Template이 Virtual DOM Render Function으로 컴파일
  - Reactivity System을 통해 최소한으로 다시 표시해야하는 Component들을 파악
  
### Template Syntax: Interpolation
- 이질적인 것을 (호환되게) 집어 넣는 것
  - Component의 Data를 View에 집어넣어주는 것으로 이해
- 대표적인 종류들
  - Text: 가장 기본적인 것 (Mustache Binding: {{}})
  - Raw HTML, Attributes: ID, Class, Style 같은 속성들 또한 Dynamic하게 적용 가능

### Template Syntax: Directive
- v- 접두어를 가진 특수한 attributes
- Interpoliation만으로는 힘든 각종 효과들을 쉽게 적용할 수 있도록 한 것
  - 조건문, 반복문, (Vue Instance 내에서 인식하는) 이벤트들 
- 인자를 받을 수도 있음.
  - ex) v-bind:href="url"
  - href 를 인자로 받아서 url 이라는 변수를 href에 Binding
  
### Modifiers
- .으로 표시되는 특수한 접미어들
- 해당 Directive가 어떤 상황에서만 적용되도록 할 것인가를 제한하는 것
  - 예) 엔터키를 눌렀을 때만 Callback 함수 호출

### Shorthand
- 단축어
- IDE를 쓰면 자동 완성으로 편하겠지만, 그러지 않는 경우 이런 단축 문법을 참고해 쉽게 코드를 작성할 수 있다.

## Directive
### v-for: 반복문
- vue.js의 style guide에서 :key를 사용하도록 권장함
  - 고유한 key값들을 통해, 항목들이 예측 가능한 순서로 나타내게 하기 위함이라고 한다.
  
### v-if: 조건문
- v-if / v-else-if / v-else

### v-model: (Form Input) Data Binding
Input DOM에 Data Binding을 설정하는 것이다.
- 대부분의 Input Type에서 가능하다.
- Modifier을 이용해서 Input 값들을 다듬을 수 있다.
  - .number: String을 Numeric 값으로 Typecast
  - .trim: 앞뒤 Whitespace들을 정리
  - .lazy: Input DOM에서 포커스가 나갔을 때 값을 Update
    - 연속된 이벤트 발생을 방지