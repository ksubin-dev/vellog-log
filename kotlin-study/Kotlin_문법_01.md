# Kotlin 문법 - 시작과 기본 출력 (`print`, `println`)

## ✅ 학습 목표
- Kotlin에서 `print`, `println`의 차이를 이해한다.
- 세미콜론(`;`) 사용 유무 및 코딩 스타일을 이해한다.

---

## 📘 학습 요약

- Kotlin에서는 **문장 끝에 `;` 세미콜론이 필요 없다.**
  - 써도 되지만 일반적으로 **사용하지 않는 게 컨벤션**이다.
- `print()`는 줄바꿈 없이 출력, `println()`은 출력 후 줄바꿈.
- Java와 달리 main 함수의 형태가 간결하다.
  ```kotlin
  fun main() {
      // entry point
  }
  ```

---

## 💻 실습 코드

```kotlin
fun main() {
    print("Hello")
    print(" Kotlin")
    println(" World")
    println("Welcome!")
}
```

### 출력 결과
```
Hello Kotlin World
Welcome!
```

---

## ⚠️ 자주 하는 실수

- `println`과 `print`의 차이를 모르고 쓰는 경우 (줄바꿈 확인!)
- 세미콜론(`;`)을 자바 습관대로 쓰는 것 → 코틀린에서는 생략이 자연스러움

---

## 💡 느낀 점 / 메모
- main 함수가 Java보다 훨씬 간단하고 가독성이 좋다.
- 줄바꿈 처리 때문에 출력 결과가 예상과 다를 수 있으니 **print/println 차이**를 명확히 이해하는 것이 중요.

---

## 🔗 관련 공식 문서
- Kotlin Output: https://kotlinlang.org/docs/basic-syntax.html#print-to-the-standard-output

---

## 🔗 Velog 링크
- velog : https://velog.io/@subin_k/Kotlin-%EB%AC%B8%EB%B2%95-%EC%8B%9C%EC%9E%91%EA%B3%BC-%EA%B8%B0%EB%B3%B8-%EC%B6%9C%EB%A0%A5-print-println
