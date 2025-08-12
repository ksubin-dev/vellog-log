# 📌 Kotlin 문법 – 리스트와 배열 (`List`, `Array`)

## 1. List

- **`listOf()`** → 불변(Immutable) 리스트 → 값 변경 불가능 (`add`, `remove` 불가)
- **`mutableListOf()`** → 가변(Mutable) 리스트 → 값 추가/삭제 가능
- Java의 `ArrayList`와 비슷

```kotlin
fun main() {
    val nums = listOf(1, 2, 3, 4, 5)
    // nums.add(6) ❌ 변경 불가

    val numsMutable = mutableListOf(1, 2, 3, 4, 5)
    numsMutable.add(6)    // ✅ 추가 가능
    numsMutable.remove(3) // ✅ 값 제거 가능

    println(numsMutable) // [1, 2, 4, 5, 6]
}
```

## 2. Array

- **`arrayOf()`** 로 생성
- `size`, `get(index)`, `set(index, value)` 가능
- Kotlin에서는 일반적으로 `List` 사용을 권장

### arrayOf()에 관하여 추가 사항

- 한 번 생성하면 길이 고정
- 값 변경은 가능하지만
- 요소 추가/삭제는 불가능
- add() 사용불가!!!!

```kotlin
fun main() {
    val arr = arrayOf(1, 2, 3, 4, 5)
    println(arr.size) // 5

    arr[0] = 10 // 값 변경
    println(arr[0]) // 10

    try {
        val item = arr[6] // ❌ IndexOutOfBoundsException
    } catch (e: Exception) {
        println("에러: ${e.message}")
    }
}
```

---

## 3. 차이점 정리

| 구분 | List (listOf) | MutableList (mutableListOf) | Array (arrayOf) |
| --- | --- | --- | --- |
| 변경 가능 여부 | ❌ 불가 | ✅ 가능 | ✅ 가능 |
| 크기 변경 | ❌ 불가 | ✅ 가능 | ❌ 불가 |
| 인덱스 접근 | ✅ 가능 | ✅ 가능 | ✅ 가능 |
| 권장 용도 | 읽기 전용 데이터 | 동적으로 변경되는 컬렉션 | 특수한 경우(성능, 호환) |

---

✅ **Tip**

- Kotlin에서는 배열보다는 `List` 사용이 일반적
- 읽기 전용이면 `listOf()`, 변경이 필요하면 `mutableListOf()`
