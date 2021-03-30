## 유닛 테스트 (Jest)

유닛(단위) 테스트란 상태, 메소드, 컴포넌트 등의 정의된 프로그램 최소 단위들이 독립적으로 정상 동작하는지 확인하는 것을 말한다.

이를 통해 프로그램 전체의 신뢰도를 향상하고 코드 리팩토링의 부담을 줄일 수 있다.

### 테스트 이해하기

다음과 같은 함수가 있다고 가정하자
```js
exports.addOne = function (a) {
  return a + 1
}
```
a 를 입력 값으로 받아 1을 더한 뒤 반환하는 함수이다.

이 함수의 경우 숫자를 인수로 입력받아 1을 더해주는 것이 정상적인 작동이 되겠다.

하지만 문자를 인수로 받을 경우 원하지 않는 결과를 반환하게 된다.

```js
console.log(
  addOne(1), // 2
  addOne('1') // '11'
)
```

매번 콘솔 출력을 통해 기댓값을 하나씩 수동 확인하지 않고, 테스트를 통해서 언제든지 다시 검증할 수 있는 상태를 만들어 보자.

Jest를 기준으로 테스트 코드를 작성 할 경우

```js
const { addOne } = require('./calc.js') // 가상의 파일 이름

// Test1
test('인수가 숫자인 경우', () => {
  // expect()의 인수 결과가 .toBe의 인수 값이 되길 기대한다
  expect(addOne(1)).toBe(2)
  expect(addOne(7)).toBe(8)
})

// Test2
test('인수가 문자인 경우', () => {
  expect(addOne('1')).toBe(2)
  expect(addOne('7')).toBe(8)
})
```

테스트를 동작시키면 다음과 같이 `인수가 문자일 경우`에서 테스트가 실패하고 만다.

![unit-test-basic-failed](uploads/335d9638136c4bf0e0779814b40548a5/unit-test-basic-failed.jpg)

위 테스트를 성공시키기 위해 addOne 함수를 수정 해 보도록 하자.

다음과 같이 `parseFloat`을 사용해 문자 데이터인 경우 숫자 데이터로 변환되도록 수정하였다.

```js
exports.addOne = function (a) {
  return parseFloat(a) + 1
}
```

다시 테스트를 실행하면 다음과 같이 테스트가 통과되게 된다.

![unit-test_basic-passed](uploads/b893071c099dcd384bbbabfd55c16c9a/unit-test_basic-passed.jpg)

---

### 테스트 문법

vue 컴포넌트를 테스트 하는 코드를 작성해보자!

```js
import { shallowMount } from '@vue/test-utils'
import HelloWorld from '../HelloWorld'

describe('큰 테스트 단위', () => {
  let wrapper
  beforeEach(() => {
    wrapper = shallowMount(HelloWorld)
  })

  test('작은 테스트 단위', () => {
     expect(wrapper.vm.msg).toBe('Hello World~')
  })
})
```

HelloWorld 컴포넌트를 shallowMount(얇은 마운트) 해서 테스트 한다.

> shallowMount란 컴포넌트를 불러올 때, 해당 컴포넌트에 연결되어 있는 하위 컴포넌트는 연결하지 않겠다는 의미이다.

describe로 큰 테스트 단위를 잡고 그 안에서 test로 작은 단위의 테스트를 진행한다.

wrapper 변수를 지정해서 컴포넌트를 마운트 하여 예상과 같은 작동을 하는지 체크한다.

### 테스트 코드 디렉토리 구조

![test2](uploads/359f14d27be36439752aa9786b0b8bee/test2.png)


test/unit/ 디렉토리 내부에 가상 데이터를 담는 mock 디렉토리와, 실제 테스트 파일을 담는 specs 디렉토리로 나눈다.

specs 내부의 디렉토리 구조는 src/views의 내부 디렉토리 구조와 똑같이 가져간다.

개발하려고 하는 컴포넌트 파일(vue)에 이름과 똑같이 만들고, 그 뒤에 spec.js 확장자로 테스트 코드를 작성하면 된다.

:thumbsup: 

---

참고 - [HEROPY Tech](https://heropy.blog/2020/05/20/vue-test-with-jest/)