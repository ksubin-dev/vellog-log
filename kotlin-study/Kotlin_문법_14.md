# Kotlin 문법 - 타입 확인과 형 변환 (`is`, `as`)

## 타입 확인 (`is`)

- `is` 연산자를 이용해 객체가 특정 타입인지 확인 가능
- `is`가 `true`로 확인되면 스마트 캐스트(Smart Cast) 기능이 적용되어, 별도의 형 변환 없이 해당 타입의 멤버를 바로 사용 가능
- `!is` 를 사용하면 반대(특정 타입이 아닌 경우) 확인 가능

---

## 타입 변환 (`as`)

- `as` 연산자를 사용하면 강제 타입 캐스팅 수행
- 잘못된 타입으로 변환 시 런타임 오류(`ClassCastException`) 발생
- 안전한 캐스팅을 위해 `as?` 연산자 사용 가능
→ 캐스팅 실패 시 `null` 반환

---

## 실습 코드

```kotlin
fun main() {
    val dog: Animal = Dog()
    val cat = Cat()

    // 강제 캐스팅 (잘못된 변환 → 런타임 오류 발생)
    // cat as Dog

    // 안전한 캐스팅
    val maybeDog = cat as? Dog
    println(maybeDog) // null

    // 타입 확인
    if (dog is Dog) { // true
        dog.move()   // 스마트 캐스트 적용됨
        dog.draw()
        println("멍멍이")
    }

    if (dog is Animal) { // true
		    //Animal만 통과했기때문에 move만 있고 draw()는 없다.
        dog.move()
        println("멍멍")
    }

    if (dog !is Cat) { // true
        println("이 객체는 고양이가 아님")
    }
}

interface Drawable {
    fun draw()
}

abstract class Animal {
    open fun move() {
        println("이동")
    }
}

class Dog : Animal(), Drawable {
    override fun move() {
        println("후다닥")
    }
    override fun draw() {
        println("그림 그리기")
    }
}

class Cat : Animal() {
    override fun move() {
        println("살금")
    }
}
```

## 정리 포인트

- `is` → 타입 확인, 스마트 캐스트 지원
- `!is` → 특정 타입이 아님을 확인
- `as` → 강제 캐스팅 (잘못된 경우 예외 발생)
- `as?` → 안전한 캐스팅 (실패 시 `null` 반환)
- 자바와 달리 코틀린은 `instanceof` 대신 `is` 사용, 명확하고 간결함
