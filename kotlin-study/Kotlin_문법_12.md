# Kotlin 문법 - 접근자, 게터/세터 (`getter`, `setter`)

## 학습 요약

- `val` → 읽기 전용(기본적으로 getter만 생성)
- `var` → 읽기/쓰기 가능(getter, setter 모두 생성)
- `private set` → 외부에서 setter 접근 차단 (읽기 전용처럼 사용 가능)
- `get()` → 커스텀 게터 정의 가능 (`field` 키워드를 사용)
- `data class` → `equals`, `hashCode`, `toString` 등을 자동으로 생성하여 객체 비교나 출력에 용이

---

## 실습 코드

```kotlin
fun main() {
    val john = Person("john", 20)
    val john2 = Person("john", 20)

    // 기본 클래스는 서로 다른 인스턴스 → 주소값 출력
    println(john)   // Person@735f7ae5
    println(john2)  // Person@180bc464
    println(john == john2) // false

    // 게터(get) 오버라이드 활용
    println(john.hobby) // "취미 : 축구"

    // 데이터 클래스 사용 시, 값 비교로 동등성 판단
    /*
    data class Person(val name: String, var age: Int)
    println(john == john2) // true
    */
}

class Person(
    val name: String,
    var age: Int,
) {
    var hobby = "축구"
        private set // 외부에서 hobby 변경 불가
        get() = "취미 : $field" // field 키워드 사용하여 backing field 접근

    init {
        println("init") // 객체 생성 시 자동 실행
    }

    fun some() {
        hobby = "야구" // 클래스 내부에서는 변경 가능
    }
}
```

## 정리 포인트

- **기본 getter/setter 자동 생성**
    - `val` → `getter`만 생성
    - `var` → `getter` + `setter` 생성
- **커스텀 getter/setter**
    - `get()` 또는 `set()` 오버라이드 가능
    - `field` → 프로퍼티의 backing field를 가리킴
- **접근 제어**
    - `private set` → 외부에서 값 변경 차단 (읽기 전용처럼 사용)
- **객체 비교**
    - 일반 클래스: 참조(주소) 비교
    - `data class`: 값 비교 (자동으로 `equals/hashCode/toString` 생성)
 
## Backing Field란?
- 프로퍼티를 정의할 때, 코틀린이 자동으로 생성해주는 **실제 값을 저장하는 공간**  
- `getter`/`setter`를 직접 정의할 때 **프로퍼티를 자기 자신으로 참조하면 무한 루프**에 빠질 수 있음 → 이를 막기 위해 `field`라는 키워드를 사용
