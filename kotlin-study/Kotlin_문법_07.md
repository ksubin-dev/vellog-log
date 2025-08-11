# 📌 Kotlin 문법 – 반복 (`for`, `while`)

## 1. `for-in` 반복문

- **컬렉션**이나 **범위(range)** 를 순회할 때 사용.
- `(start..end)` → end 값 포함`(start until end)` → end 값 미포함

```kotlin
val items = listOf(1, 2, 3, 4, 5)

for (item in items) {
    print(item)
}
```

## 2. `forEach` (람다 방식)

- 컬렉션에 포함된 `forEach` 함수를 사용.
- **람다 표현식**으로 간결하게 작성 가능.

```kotlin
items.forEach { item ->
    print(item)

```

---

## 3. 전통적인 for문 (Java 스타일)

- Kotlin에서도 사용 가능하지만, **Kotlin 스타일**이 더 간결함.

```kotlin
//for(int i =0; i<items.length; i++) -> 예시
for (i in 0..items.size - 1) {
    print(items[i])
}
```

---

## 4. 범위(range)와 step/downTo

- `step` → 증가폭 지정
- `downTo` → 감소 순서

```kotlin
// 1부터 10까지 2씩 증가
for (i in 1..10 step 2) {
    print("$i ")
}

// 5부터 1까지 감소
for (i in 5 downTo 1) {
    print("$i ")
}
```

---

## 5. `while` 문

- Java와 동일한 방식.
- 조건이 참일 동안 반복.

```kotlin
var x = 5
while (x > 0) {
    println(x)
    x--
)
```

---

## 6. `do-while` 문

- 조건을 나중에 검사 → 최소 1번은 실행됨.

```kotlin
var y = 0
do {
    println("실행됨: $y")
    y++
} while (y < 3)
```

---

✅ **정리**

- Kotlin은 범위, 컬렉션 순회가 강력하고 간결.
- `forEach` + 람다로 함수형 스타일 작성 가능.
- Java 스타일 for문도 가능하지만 가독성 ↓
