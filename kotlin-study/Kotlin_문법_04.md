# 📌 Kotlin 문법 – `max`, `min`, `Random`

## 1. `max`, `min`

- Kotlin에서는 `max(a, b)`, `min(a, b)`를 **`kotlin.math` 패키지**에서 제공합니다.
- Java처럼 바로 호출하는 것이 아니라, 아래와 같이 **패키지 명시** 또는 **import** 후 사용합니다.

```kotlin
fun main() {
    val i = 10
    val j = 20

    // 패키지 직접 명시
    println(kotlin.math.max(i, j))
    println(kotlin.math.min(i, j))

    // import 사용
    // import kotlin.math.max
    // println(max(i, j))
}
```

## 2. `Random`

- 난수 생성을 위해 **`kotlin.random.Random`** 을 사용합니다.
- `nextInt(start, end)` → **start 이상, end 미만**
- `nextDouble(start, end)` → **실수 난수 생성**

```kotlin
kotlin
복사편집
import kotlin.random.Random

fun main() {
    val randomInt = Random.nextInt(0, 100)      // 0~99 범위
    val randomDouble = Random.nextDouble(0.0, 100.0) // 0.0~99.999... 범위

    println(randomInt)
    println(randomDouble)
}

```

---

✅ **정리**

- `max`, `min` → `kotlin.math` 사용
- `Random` → `kotlin.random.Random` import 필요
- 범위는 **시작값 포함, 끝값 미포함** 규칙을 따른다.
