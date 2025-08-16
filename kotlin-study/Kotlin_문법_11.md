# Kotlin 문법 - 클래스 선언과 `data class`

## Class

- **클래스 선언 형식**: `class 클래스명(생성자 파라미터) { ... }`
- 생성자 파라미터는 **클래스 이름 옆**에 작성한다. (자바처럼 함수 블록 안이 아님)
- 파라미터 뒤에 **콤마(,)** 를 붙여도 에러가 나지 않는다.
- `val`, `var` 키워드를 붙이면 **자동으로 Getter/Setter** 가 생성된다.
    - `val` → 읽기 전용 (getter만)
    - `var` → 읽기/쓰기 가능 (getter + setter)

### 실습코드

```kotlin
class Person(
    val name: String,  // 읽기 전용
    var age: Int,      // 읽기/쓰기 가능
) {
    fun introduce() = println("안녕하세요, 저는 $name, 나이는 $age살 입니다.")
}

fun main() {
    val person = Person("수빈", 25)
    person.introduce()
    person.age = 26  // var라서 수정 가능
    println("변경된 나이: ${person.age}")
}

```

## Data class

- 데이터를 담기 위한 **전용 클래스**
- `toString()`, `equals()`, `hashCode()`, `copy()` 같은 메서드를 자동으로 생성해준다.
- 생성자 앞에 `private`를 붙이면 외부에서 접근할 수 없는 값으로 만들 수 있다.

### 실습 코드

```kotlin
data class User(
    val id: Int,
    val name: String,
    private val password: String // 외부 접근 불가
)

fun main() {
    val user1 = User(1, "홍길동", "1234")
    val user2 = user1.copy(name = "임꺽정") // copy() 자동 생성됨

    println(user1)  // User(id=1, name=홍길동)
    println(user2)  // User(id=1, name=임꺽정)

    // println(user1.password) // ❌ 접근 불가 (private)
}

```

---

## 핵심 요약

| 구분 | 특징 | 비고 |
| --- | --- | --- |
| `class` | 일반적인 객체 생성, 메서드 작성 가능 | `val/var`로 getter/setter 자동 제공 |
| `data class` | 데이터 저장 전용, `toString()/equals()/copy()` 자동 생성 | `private` 붙이면 외부 접근 차단 |

✅ **Tip**

- 데이터만 담을 용도라면 `data class`를 사용
- 로직(함수)도 함께 포함한다면 `class` 사용
