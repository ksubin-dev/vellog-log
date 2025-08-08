# Kotlin 문법  – 형변환, 문자열 처리 (`toInt`, `String`)

## 📌 형변환 (Type Casting)

- 코틀린은 **명시적 형변환**을 사용해야 함 (자동 형변환 X)
- `toInt()`, `toLong()`, `toDouble()` 등 메서드 사용
- 변환 대상이 올바른 형식이 아닐 경우 `NumberFormatException` 발생 가능 → 예외 처리 필요

### 💻 예제

```kotlin

fun main() {
    var i = 10
    var l = 20L
    var name = "10"

    i = name.toInt() // String → Int
    l = i.toLong()   // Int → Long
    i = l.toInt()    // Long → Int
}

```

---

## 📌 문자열 (String)

- 문자열은 **문자 배열처럼 인덱스로 접근 가능** (`name[0]`)
- 문자열 내 변수 출력 시:
    - `$변수명` : 변수 바로 사용
    - `${변수명}` : 변수 뒤에 문자나 숫자가 붙을 때 사용 (띄어쓰기 불필요)
- `uppercase()`, `lowercase()` 등 문자열 처리 함수 제공

### 💻 예제

```kotlin

fun main() {
    var name = "subin"

    println(name.uppercase())   // SUBIN
    println(name[0])            // 's'

    println("제 이름은 " + name + "입니다")    // 자바 스타일
    println("제 이름은 ${name}입니다")         // 코틀린 스타일
}

```

---

## 📝 Tip

- 변환 전 값의 **유효성 검사**를 위해 `toIntOrNull()`을 사용하면 예외 없이 `null` 반환

```kotlin

val num = "abc".toIntOrNull() ?: 0
println(num) // 0

```

