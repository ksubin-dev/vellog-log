# Kotlin 문법 - 고차 함수 및 콜백 함수 (람다 활용)

## 학습 요약

- **고차 함수(Higher-Order Function)**
    - 함수를 인자로 받거나, 함수를 반환하는 함수
    - Kotlin에서 **콜백 함수**를 간단히 구현할 수 있음
- **람다 표현식**
    - `{ parameter -> body }` 형식
    - 파라미터가 하나일 경우 `it` 키워드로 축약 가능
    - 마지막 인자가 함수일 경우, **소괄호 밖으로 빼기 가능**
- **콜백 함수 (Callback)**
    - 특정 시점에 호출되도록 넘겨주는 함수
    - 비동기 처리나 이벤트 처리에 자주 사용됨

---

## 실습 코드

```kotlin
fun main() {
    // 고차 함수 호출 - 콜백 전달
    myFunc {
        println("함수 호출")
    }

    // 매개변수가 두 개일 때 (Int + 콜백)
    myFunc2(5) {
        println("함수 호출 2")
    }

    // 괄호 생략 가능 (마지막 인자가 람다일 경우)
    myFunc() {
        println("괄호 생략 형태")
    }

    // 람다식에서 파라미터가 하나면 it 사용 가능
    repeatAction(3) {
        println("반복 실행 $it 번째")
    }
}

// 콜백을 받는 고차 함수
fun myFunc(callBack: () -> Unit) {
    println("함수 시작")
    callBack()
    println("함수 끝!!")
}

fun myFunc2(a: Int, callBack: () -> Unit) {
    println("함수 시작2, a=$a")
    callBack()
    println("함수 끝!!2")
}

// 콜백에 매개변수를 전달하는 예제
fun repeatAction(times: Int, action: (Int) -> Unit) {
    for (i in 1..times) {
        action(i)  // i를 콜백에 전달
    }
}

```

---

## 추가 정리 포인트

- **`() -> Unit`** : 파라미터 없고 반환값 없는 함수 타입
- **`(Int) -> String`** : Int를 받아서 String을 반환하는 함수 타입
- Kotlin에서는 **익명 함수** 대신 **람다**를 더 많이 활용
- 고차 함수는 **비동기 처리, 이벤트 리스너, DSL** 구현에서 강력하게 쓰임
