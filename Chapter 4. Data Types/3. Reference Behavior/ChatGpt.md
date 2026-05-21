📁 Chapter 4. Data Types
 └─ 📁 3. Reference Behavior
     ├─ Primitive vs Reference
     ├─ 얕은 복사 vs 깊은 복사
     ├─ 구조 분해와 참조 유지
     └─ React/Vue의 불변성 문제 요약.md



React에서 말하는 \*\*“불변성(immutability)”\*\*은 \*\*primitive type의 `const` 같은 *값 상수성*이 아니라, object/array의 *참조 불변성(reference immutability)*을 말합니다.**

---

## ✅ 정리: React의 불변성은 “참조 불변성”

### 📌 primitive 불변성 (값 자체 고정)

```js
const a = 1;
a = 2; // ❌ Error — primitive 상수
```

> 이건 일반적인 자바스크립트 문법에서의 “값이 바뀌지 않음”이고,
> **React의 리렌더링 트리거와는 무관**합니다.

---

### 📌 React의 불변성 (참조가 바뀌어야 리렌더됨)

```js
const [state, setState] = useState({ count: 0 });

// ❌ 이렇게 직접 변경하면 리렌더링 안 됨
state.count++;
setState(state); // 같은 참조 → React는 변경 안 된 것으로 판단

// ✅ 새로운 객체로 참조 변경
setState({ ...state, count: state.count + 1 });
```

> React는 `Object.is(prevState, nextState)` 또는 **shallow compare** 방식으로
> **참조가 변경되었는지**를 기준으로 리렌더링을 결정합니다.

---

## 🧠 핵심 개념 요약

| 구분                           | 의미           | React에서 리렌더링 발생? |
| ---------------------------- | ------------ | ---------------- |
| primitive 상수 (`const a = 1`) | 값 자체가 바뀌지 않음 | ❌ 상관 없음          |
| 참조 불변성 유지 (`obj1 === obj2`)  | 같은 메모리 참조    | ❌ 변화 없음으로 간주     |
| 참조 불변성 깨뜨리기 (`{ ...obj }`)   | 새로운 메모리 참조   | ✅ 변화 감지됨         |

---

## ✅ 결론

> ❝ React에서 말하는 불변성은 **객체의 값이 바뀌었는지가 아니라, “참조가 바뀌었는가”를 기준으로 한다.** ❞
> 즉, **“불변성을 지켜라” = 참조를 바꿔라.**

Vue의 Proxy-based reactivity는 내부 값이 바뀌어도 감지되지만,
React는 **값을 바꾸는 게 아니라 객체를 바꾸는 게 핵심**입니다.

필요하다면 이 내용을 기반으로 Chapter 4에 "Immutability" 챕터를 구조화해드릴까요?
