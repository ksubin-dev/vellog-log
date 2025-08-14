# Kotlin 문법 - 함수(Function)

## 핵심 개념

- **함수 선언 형식**: `fun 함수명(파라미터): 반환타입 { ... }`
- **반환타입 생략 가능**: 표현식이 한 줄이면 타입 추론이 가능
- **기본값(Default Parameter)**: 파라미터에 기본값을 지정 가능
- **이름 있는 인자(Named Argument)**: 호출 시 파라미터 순서를 바꿔 지정 가능
- **오버로딩 대신 Default Parameter 활용** 가능

---

## 예제 코드

```kotlin
fun main() {
    println(sum(10, 20))          // 기본 사용
    println(sum2(5, 7))           // 한 줄 표현
    println(sumWithDefault(3))    // b는 기본값 사용
    println(sumWithDefault(b = 5, a = 10)) // 순서 변경 가능
}

// 1. 명시적 반환 타입
fun sum(a: Int, b: Int): Int {
    return a + b
}

// 2. 한 줄 함수 + 타입 생략
fun sum2(a: Int, b: Int) = a + b

// 3. 기본값 지정
fun sumWithDefault(a: Int, b: Int = 0) = a + b
```

---

## 사용 팁

| 기능 | 설명 | 예시 |
| --- | --- | --- |
| 기본값(Default) | 인자를 생략해도 사용 가능 | `sumWithDefault(3)` |
| 타입 추론 | 한 줄 표현식이면 타입 생략 | `fun sum(a: Int, b: Int) = a + b` |
| 이름 있는 인자 | 순서 바꿔 호출 가능 | `sumWithDefault(b = 5, a = 10)` |
| 오버로딩 대체 | 같은 기능에 파라미터만 다르면 기본값 사용 | `fun greet(name: String = "Guest")` |

---

✅ **Tip**

- 한 줄 함수에서는 **`=`** 뒤에 바로 식을 쓰면 `return`과 반환 타입을 생략 가능
- 오버로딩보다 기본값을 쓰는 편이 코드 유지보수에 유리
