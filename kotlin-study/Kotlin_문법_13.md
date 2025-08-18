# Kotlin 문법 - 상속 (`extends`)과 인터페이스 구현

## 상속 (Inheritance)

- 코틀린에서 클래스는 기본적으로 **final** (상속 불가)
- 상속이 필요하다면 클래스 선언 앞에 `open` 키워드를 붙여야 함
- 메소드나 프로퍼티도 기본적으로 오버라이드 불가 → `open` 키워드 필요
- 오버라이드 시 반드시 `override` 키워드 사용

---

## 인터페이스 (Interface)

- `interface` 키워드로 선언
- 여러 개를 동시에 구현 가능 (`class A : B(), C, D`)
- 함수는 기본적으로 추상 메소드이지만, **구현이 포함된 디폴트 메소드**도 정의 가능
- `override` 키워드를 사용해 구현

---

## 실습 코드

```kotlin
fun main() {
    val dog = Dog()
    dog.move() // 후다닥
    dog.draw()

    val cat = Cat()
    cat.move() // 살금
}

interface Drawable { // 인터페이스
    fun draw()
}

abstract class Animal { // 추상 클래스
    open fun move() {
        println("이동")
    }
}

class Dog : Animal(), Drawable {
    // Animal의 move() 오버라이드
    override fun move() {
        println("후다닥")
    }

    // Drawable 인터페이스 구현
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

- **기본 클래스는 상속 불가** → `open` 키워드를 붙여야 상속 가능
- **함수도 마찬가지** → `open`이 없으면 오버라이드 불가
- `abstract class`는 일부 구현만 제공 가능, 객체 생성 불가
- `interface`는 다중 구현 가능 → 클래스는 다중 상속 불가하지만 인터페이스로 보완 가능
- 오버라이드 시 항상 `override` 키워드 필수
