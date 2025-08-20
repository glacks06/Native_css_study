# CSS 함수형 셀렉터 및 Pseudo-class 보고서



## 1. 개요

CSS 함수형 셀렉터(Functionals Selectors)는 괄호 `()` 안에 여러 선택자 또는 조건을 인자로 받아 동적으로 요소를 선택하는 고급 CSS 선택자입니다. 이런 선택자는 기존의 단순 선택자보다 훨씬 더 유연하고 복잡한 조건을 표현할 수 있으며, 스타일 작성의 가독성과 유지관리를 크게 향상시킵니다.

그리고 CSS Pseudo-class(의사 클래스)는 요소의 특정 상태나 조건에 따라 스타일링할 수 있게 해주는 선택자입니다. 함수형 셀렉터들은 Pseudo-class의 한 종류로 분류되며, 기존 Pseudo-class와 함께 UI 상태 표현에 핵심적으로 활용됩니다.



## 2. 주요 함수형 셀렉터 설명

### 2.1 `:is()`

- 괄호 안에 나열된 여러 선택자 중 하나라도 일치하면 해당 요소를 선택합니다.
- 복잡한 선택자 조합을 간결하게 표현하는 데 효과적입니다.
- 구체성(Specificity)은 괄호 안에 있는 선택자 중 가장 높은 값에 따릅니다.

#### 예시
```css
:is(h1, h2, .title) {
  color: red;
}
```



### 2.2 `:where()`

- `:is()`와 동일하게 동작하지만, 구체성 값이 항상 0으로 적용됩니다.
- 따라서 스타일 우선순위에 영향을 주지 않고, 기본 스타일이나 초기화 스타일에 적합합니다.

#### 예시
```css
:where(h1, h2, .title) {
  margin: 0;
}
```



### 2.3 `:has()`

- 특정 자식 또는 후손 요소의 존재 여부에 따라 부모 요소를 선택할 수 있는 관계형 Pseudo-class입니다.
- 기존 CSS에서 불가능했던 부모 선택자 역할을 수행합니다.

#### 예시
```css
div:has(> img) {
  border: 2px solid blue;
}
```



### 2.4 `:not()`

- 괄호 안에 명시된 선택자를 제외한 요소를 선택합니다.
- 조건부 스타일링과 반대 조건 지정에 필수적입니다.

#### 예시
```css
p:not(.highlight) {
  color: gray;
}
```



## 3. 함수형 셀렉터의 특징

- **괄호 안 인자:** 타입 선택자, 클래스 선택자, ID 선택자, 속성 선택자, 가상 클래스 등 다양한 선택자가 올 수 있습니다.
- **구체성 처리:** `:is()`는 내부 선택자의 가장 높은 구체성 따름, `:where()`는 항상 0 구체성 적용.
- **표현력 강화:** 복잡한 조건과 조합을 단순화해 코드 가독성과 유지 보수를 향상시킵니다.
- **브라우저 처리:** 내부적으로 평면 CSS 선택자로 변환되어 기존 CSS 처리 시스템과 호환됩니다.



## 4. CSS Pseudo-class 전체 범주 및 분류

### 4.1 Pseudo-class 정의

- 요소의 상태, 조건, 관계에 따라 스타일을 적용할 수 있게 하는 선택자로, 콜론(`:`)으로 시작합니다.

### 4.2 주요 Pseudo-class 분류

| 범주         | 예시                                  | 설명                              |
|------------|------------------------------------|---------------------------------|
| 상태 기반     | `:hover`, `:active`, `:focus`, `:visited`, `:link`        | 상호작용에 따른 상태 표현            |
| 입력/폼 상태  | `:checked`, `:disabled`, `:enabled`, `:required`, `:invalid` | 폼 요소의 상태 표현                 |
| 구조 기반     | `:first-child`, `:last-child`, `:nth-child()`, `:only-child`, `:empty`, `:root` | 문서 트리 안 위치 기반 선택          |
| 관계 기반     | `:not()`, `:is()`, `:has()`, `:where()`                 | 조건부 및 관계형 선택               |
| 미디어/상태   | `:playing`, `:paused`, `:fullscreen`, `:modal`, `:open`      | 미디어 재생 및 특수 상태 표현         |
| 기타         | `:lang()`, `:target`, `:focus-within`, `:focus-visible`, `:scope` | 언어, 타겟팅, 포커스 컨텍스트 등      |

### 4.3 Pseudo-class와 Pseudo-element 차이

- Pseudo-class: 요소 상태나 관계로 선택  
- Pseudo-element: 요소 내의 특정 부분이나 가상 요소를 생성해 스타일링


## 5. 실무 활용 예

```css
:is(header, main, footer) :is(h1, h2, .title):hover {
  color: blue;
}

input:required:invalid {
  border-color: red;
}

ul:has(li.active) {
  background-color: #f0f8ff;
}
```



## 6. 결론

함수형 셀렉터 및 Pseudo-class들은 CSS 선택자 문법의 확장판으로서 복잡한 UI 상태와 조건을 효과적으로 표현하게 해줍니다. 이를 적극 활용하면 코드량 감소와 유지 보수성 향상에 큰 도움이 되며, 최신 웹 개발에 필수적인 기술로 자리잡고 있습니다.


