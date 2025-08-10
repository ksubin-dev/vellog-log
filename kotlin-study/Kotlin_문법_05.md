# 📌 Kotlin 문법 – 키보드 입력

## 1. `Scanner` 사용

- Java 방식과 유사하지만, **`System.in`** 을 Kotlin에서 사용 시 **`in`** 이 예약어라서 **백틱(`)으로 감싸야 함**.
- 숫자, 문자열 모두 입력 가능.

```kotlin
import java.util.Scanner

fun main() {
    val reader = Scanner(System.`in`)

    print("숫자 입력: ")
    val num = reader.nextInt()

    print("문자열 입력: ")
    val text = reader.next()

    println("입력한 숫자: $num")
    println("입력한 문자열: $text")
}
```

## 2. `readLine()` 사용 (간단한 방법)

- Kotlin에서 자주 쓰이는 **표준 입력 함수**.
- 기본적으로 **문자열(String)** 로 입력 받음 → 필요 시 형변환(`toInt()`, `toDouble()`) 해야 함.

```kotlin
fun main() {
    print("문자열 입력: ")
    val text = readLine()

    print("숫자 입력: ")
    val num = readLine()?.toInt()

    println("입력한 문자열: $text")
    println("입력한 숫자: $num")
}
```

---

✅ **정리**

- Java 스타일: `Scanner(System.`in`)`
- Kotlin 스타일: `readLine()` → 더 간단, 문자열 입력 전용
- 숫자 입력 시 `readLine()` → 형변환 필수
