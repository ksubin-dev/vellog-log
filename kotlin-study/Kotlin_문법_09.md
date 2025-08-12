# Kotlin 문법 정리 - 널 안정성 (Null Safety)

## 핵심 개념

- **`?` (Nullable)** : 해당 타입 변수에 `null` 저장 가능
- **`!!` (Non-null Assertion)** : 강제로 null 여부 체크 해제 (null이면 예외 발생)
- **`?.` (Safe Call)** : null이 아닐 때만 접근/실행
- **`let`** : null이 아닐 때만 블럭 실행
- **`?:` (Elvis Operator)** : null일 경우 기본값을 반환

> ⚠️ !!는 NullPointerException(NPE)을 유발할 수 있으므로,
> 
> 
> 가급적 `if` 문, `?.let`, `?:` 사용을 권장
> 

---

## 예제 코드

```kotlin
fun main() {
    // 1. Nullable 변수 선언
    var name: String? = null
    name = "수빈"

    // 2. Non-null 변수
    var name2: String = ""
    // name2 = null ❌ 불가능

    // 3. !! 사용 (비추천: null이면 예외 발생)
    name2 = name!!

    // 4. if문 null 체크 (추천)
    if (name != null) {
        name2 = name
    }

    // 5. Safe Call + let 사용 (추천)
    name?.let {
        name2 = it
    }

    // 6. Elvis 연산자 (?:) - null이면 기본값 사용
    val finalName = name ?: "기본 이름"
    println(finalName) // name이 null이면 "기본 이름" 출력
}

```

## Null Safety 요약 표

| 연산자 | 의미 | 예시 | 결과 |
| --- | --- | --- | --- |
| `?` | null 허용 타입 | `var a: String?` | `a = null` 가능 |
| `!!` | 강제 non-null | `a!!` | null이면 예외 발생 |
| `?.` | null이 아닐 때만 접근 | `a?.length` | null이면 실행 안 함 |
| `?.let` | null이 아닐 때 블럭 실행 | `a?.let { println(it) }` | 안전하게 코드 실행 |
| `?:` | null이면 기본값 반환 | `a ?: "기본"` | a가 null이면 `"기본"` 반환 |

---

✅ **Tip**

- `!!`는 정말 확실히 null이 아님을 보장할 때만 사용하세요.
- 기본값이 필요한 경우 **엘비스 연산자(`?:`)** 사용이 가장 간단합니다.
- null이 아닐 때만 특정 로직을 실행하려면 `?.let {}` 사용.
