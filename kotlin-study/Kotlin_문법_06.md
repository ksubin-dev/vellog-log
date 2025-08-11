# 📌 Kotlin 문법 – 조건문 (`if`, `when`)과 삼항 연산 대체

## 1. `if` 문

- Kotlin에서는 `if`가 **하나의 "식(Expression)"** 으로 취급됨.
- 따라서 결과 값을 변수에 직접 할당할 수 있음.
- Java의 `if`는 **문(Statement)** 이라 이렇게 못함.

```kotlin
fun main() {
    val i = 7

    val result = if (i > 10) {
        "10보다 크다"
    } else if (i > 5) {
        "5보다 크다"
    } else {
        "5 이하"
    }

    println(result) // 5보다 크다
}

```

## 2. `when` 문

- Java의 `switch`와 비슷하지만 더 강력.
- **값 비교**, **범위 비교**, **조건식**, **타입 검사** 모두 가능

```kotlin
fun main() {
    val i = 7

    val result = when {
        i > 10 -> "10보다 크다"
        i in 6..10 -> "6~10 사이"
        i == 5 -> "5다
        else -> "그 외"
    }

    println(result)
}
```

---

### `when` – 값 기반 비교

```kotlin
val day = 3
val dayName = when (day) {
    1 -> "월요일"
    2 -> "화요일"
    3 -> "수요일"
    else -> "기타"

```

### `when` – 타입 검사

```kotlin
fun checkType(x: Any) = when (x) {
    is String -> "문자열"
    is Int -> "정수"
    else -> "알 수 없음"

```

---

## 3. 삼항 연산 대체

- Kotlin에는 **삼항 연산자(`? :`)** 없음.
- 대신 `if` 식을 한 줄로 작성해 대체.

```kotlin
val i = 7
val isBig = if (i > 10) true else false
println(isBig) // false
```

---

✅ **정리**

- `if` → 값 반환 가능 (표현식)
- `when` → 범위·조건·타입까지 처리 가능
- 삼항 연산자 → `if-else` 한 줄로 대체
