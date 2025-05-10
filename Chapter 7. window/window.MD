다음은 **Chapter 7: window**의 개요를 Chapter 6 (JavaScript Engine V8)과 자연스럽게 연결되도록 설계한 구조입니다.

---

# Chapter 7: `window` – 브라우저의 전역 객체

## 🎯 학습 목표

* `window` 객체가 무엇이고, 어떤 역할을 하는지 이해한다.
* `document`, `location`, `history`, `navigator` 등 **브라우저 API들의 근원이 window라는 점**을 파악한다.
* Chapter 6에서 다룬 **Web API**, **Event Loop**, **setTimeout** 등이 실제로는 window 객체의 메서드라는 것을 이해한다.
* 이후 DOM 조작의 기반이 되는 **글로벌 실행 환경**의 구조를 숙지한다.

---

## 🧭 0. Overview: 왜 `window`인가?

* V8 엔진은 JavaScript를 실행하는 런타임이지만, 브라우저 환경에서 실행될 때 그 런타임은 `window`라는 컨테이너 안에 존재
* 즉, `window`는 브라우저에서 JavaScript 코드가 **실행되는 현실의 공간**이다

---

## 📚 1. `window`와 글로벌 객체

| 개념           | 설명                                   |
| ------------ | ------------------------------------ |
| `window`     | 브라우저 탭(또는 iframe) 하나를 대표하는 최상위 객체    |
| `globalThis` | ES2020 표준 글로벌 객체 (브라우저에선 window와 동일) |
| `self`       | Web Worker나 iframe 등에서도 사용하는 전역 객체   |

* `window === globalThis` (브라우저 환경)
* `var foo = 1` → `window.foo === 1`

---

## 🧱 2. 주요 속성과 API들

| API                                | 설명                             |
| ---------------------------------- | ------------------------------ |
| `window.location`                  | URL 정보 (이동, 검색 쿼리, 새로고침)       |
| `window.history`                   | 브라우저 히스토리 제어                   |
| `window.navigator`                 | 브라우저, 플랫폼 정보                   |
| `window.screen`                    | 해상도, 디스플레이 정보                  |
| `window.setTimeout`, `setInterval` | 비동기 타이머 API (→ Event Loop 연결됨) |
| `alert`, `confirm`, `prompt`       | 사용자 알림 창                       |

> 이들 대부분은 BOM (Browser Object Model)으로도 불렸지만, 현재는 `window`의 속성으로 통합 이해함

---

## 📄 3. `window`와 `document`의 관계

* `document`는 `window.document`로 접근
* DOM 조작은 전부 document를 통해 진행되며, window는 DOM을 **소유**하는 컨테이너
* DOM은 다음 Chapter에서 다룸

```js
console.log(window.document === document); // true
```

---

## ⏰ 4. 이벤트 흐름과 타이밍

| 이벤트                | 발생 시점                 | 설명            |
| ------------------ | --------------------- | ------------- |
| `DOMContentLoaded` | DOM 트리만 준비 완료         | `document` 대상 |
| `load`             | 모든 리소스(이미지 등)까지 준비 완료 | `window` 대상   |
| `beforeunload`     | 페이지 벗어나기 전            | 사용자 이탈 경고     |

---

## 🔍 5. window와 V8 Chapter의 연결 고리

| V8 내용                                   | window에서의 실체                        |
| --------------------------------------- | ----------------------------------- |
| `setTimeout` → Web API → Callback Queue | `window.setTimeout`                 |
| 이벤트 루프의 진입점                             | `window.onload`, `addEventListener` |
| Execution Context Stack                 | 전역 컨텍스트 = window의 scope             |

---

## ✅ 요약

* `window`는 브라우저에서의 전역 객체이며, JavaScript가 실행되는 **컨텍스트이자 API의 진입점**
* document, location, timer, history 등 브라우저의 모든 주요 기능을 포함한다
* 이후 DOM 조작이나 비동기 프로그래밍에서 반드시 이해되어야 하는 핵심

---

이 구조로 Chapter 7을 시작하면, 자연스럽게 Chapter 8(DOM)으로 이어지고, 그 이전의 V8에서 학습한 개념과도 유기적으로 연결됩니다.
필요하시면 위 내용을 바탕으로 실제 텍스트 문서 파일 또는 템플릿 디렉토리 구성도 만들어드릴 수 있어요. 원하시나요?
