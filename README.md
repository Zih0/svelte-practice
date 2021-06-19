# Svelte

Front-end Framework
https://svelte.dev/
https://github.com/sveltejs/template

## Write less code

- 높은 가독성 유지
- 개발시간 단축
- 쉬운 리팩토링
- 쉬운 디버깅
- 더 작은 번들 (SPA 최적화)
- 낮은 러닝 커브

## No Virtual DOM

- 차이점 비교 없음
- 오버헤드 없음
- 빠른 퍼포먼스

## Truly reactive

- Framework-less VanillaJS
- Only use devDependencies
  > Svelte가 애플리케이션을 VanillaJS로 컴파일하고 그 결과만 동작하기 때문에, 브라우저(런타임)에서 동작하지 않는 컴파일러라고 할 수 있다.
- 명시적 설계

## 단점

낮은 성숙도( 작은 생태계)
CDN 미제공
IE 미지원

---

컴포넌트는 대문자로 만든다.

`style`태그를 작성할 시, 해당 컴포넌트 범위 내에서 적용이 된다. 컴포넌트마다 hash class를 가진다.

template 다운로드

```
npx degit sveltejs/template project-name
```
