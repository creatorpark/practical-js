지금 구성된 JavaScript 강의는 다음과 같은 매우 탄탄한 흐름을 가지고 있습니다:

* Chapter 1\~6: 실행 구조 (script → 모듈 → 타입 → 비동기 → 엔진)
* Chapter 7\~9: 환경 이해 및 API 구조 (`window` → `DOM` → 고급 개념 `Proxy`)
* **Chapter 10: SPA Structure**
  → "지금까지 학습한 JS 문법과 실행 환경의 기반 위에 현대 웹 앱이 어떻게 구성되는지"를 실제 구조와 함께 연결하는 장입니다.

---

## ✅ Chapter 10. SPA Structure: 개요 제안

### 📘 제목: "Single Page Application 구조 이해"

### 🎯 학습 목표

* JS로 구현된 SPA가 **기본적인 웹 페이지와 무엇이 다른지** 이해한다
* **라우팅, 상태관리, 렌더링, 컴포넌트 분리** 등의 SPA 핵심 구조 개념을 익힌다
* Vue, React 같은 프레임워크를 만나기 전에 **SPA의 공통 구조를 언어 독립적으로 파악**한다

---

## 📚 Chapter 10. 목차 구성안

### 0. Overview: SPA란 무엇인가?

* MPA(Multi Page App) vs SPA 비교
* `location.href`가 바뀌지 않는데 페이지가 바뀌는 이유
* CSR(Client Side Rendering) 구조

---

### 1. HTML 구조와 Root 마운트

* HTML 문서는 단 하나 (`index.html`)
* `<div id="app"></div>`와 root component 마운트의 의미
* 왜 Vue/React는 root에만 DOM 삽입하는가?

---

### 2. 라우팅과 화면 전환

* 해시 기반 (`#/page`) vs history API 기반 (`/page`)
* `window.history.pushState` / `popstate` 이벤트 설명
* 미니 라우터 예제: 버튼 클릭 시 내용 교체 + URL 변경

---

### 3. 상태 관리 구조

* 중앙 상태 관리 필요성 (`state`, `store`, `context`)
* 직접 만든 간단한 `store` 예제
* reactive UI를 위한 상태와 View 연결

---

### 4. 컴포넌트 기반 구조

* 하나의 화면을 여러 컴포넌트로 나누는 이유
* 컴포넌트의 구조 (props, template, event)
* 직접 만든 함수형 컴포넌트 구조 예시

---

### 5. 렌더링 전략

* 초기 렌더링과 재렌더링의 차이
* DOM vs Virtual DOM vs Reactive DOM 개념 비교
* 리렌더링 최적화 포인트: key, 이벤트 바인딩

---

## 📌 이후 프레임워크 학습을 위한 연결 고리

| SPA 개념  | Vue/React에서의 실체                            |
| ------- | ------------------------------------------ |
| 컴포넌트 구조 | `<script setup>` or `function Component()` |
| 라우팅     | `vue-router`, `react-router-dom`           |
| 상태 관리   | `pinia`, `redux`, `context`                |
| 렌더링     | Virtual DOM, reactivity system             |

---

## ✨ 확장 제안: Chapter 10에 추가하면 좋은 내용

| 제안 항목                      | 이유                         |
| -------------------------- | -------------------------- |
| **SPA 실습 예제**              | 바닐라 JS로 간단한 라우터 + 상태 변경 구조 |
| **프레임워크 없이 만드는 SPA 흐름도**   | 프레임워크가 어떤 추상화를 감췄는지 드러남    |
| **비교표: MPA vs SPA vs SSR** | 혼란 방지 + SSR 구조로의 확장 기반 마련  |

---

필요하시면 이 개요를 바탕으로 `README.md` 또는 `overview.txt` 형식으로 템플릿 문서를 바로 생성해드릴 수 있어요. 원하시나요?
