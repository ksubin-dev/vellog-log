# Kotlin 문법 - 변수 선언과 상수 (`var`, `val`, `const`)

## ✅ 학습 목표

- Kotlin의 변수 선언 방식 이해 (`var`, `val`)
- 상수 선언 방식(`const val`)과 그 차이점 학습

---

## 📘 학습 요약

### ▶️ 변수 타입 선언

- Kotlin은 **타입 추론**이 가능하므로 별도의 타입 선언 없이도 사용 가능
- 명시하고 싶을 경우 `:` 콜론 뒤에 타입을 지정
    
    → `var age: Int = 10`
    
- 기본 타입은 Java와 다르게 **대문자 시작**
    
    예: `Int`, `Double`, `String` 등
    

---

### ▶️ 변수 vs 상수 차이

| 키워드 | 재할당 가능 여부 | 사용 위치 | 특징 |
| --- | --- | --- | --- |
| `var` | 가능 | 어디서든 가능 | 일반 변수 |
| `val` | 불가능 | 어디서든 가능 | 런타임 상수 (Java의 `final` 비슷 or 동일) |
| `const val` | 불가능 | 클래스/파일 최상단 | 컴파일 타임 상수만 가능 |
- `val`은 **런타임에 결정되는 상수**
- `const val`은 **컴파일 타임에 결정**되어야 하며,
→ **함수 내에서는 사용 불가**!

---

## 💻 실습 코드

```kotlin
// 최상단에서만 선언 가능
const val MAX_COUNT = 100

fun main() {
    var name = "수빈"
    val birthYear = 2000
    var score: Double = 98.5

    name = "명지"        // ✅ var → 값 변경 가능
    // birthYear = 1999  // ❌ val은 재할당 불가 → 오류

    println(name)
    println(score)
}

```

---

## ⚠️ 자주 하는 실수

- `const val`을 **함수 안에서 선언하려고 하면 컴파일 에러 발생**
- `val`은 "값 못 바꾸는 변수"가 아니라 **런타임 상수**라는 점 이해 필요

---

## 💡메모

- `const`는 설정값 등 변하지 않는 값을 저장할 때 좋다.

---

## 🔗 런타임과 컴파일 타임에 대해서 알아보자

- [런타임과 컴파일타임에 대한 개념 정리- velog](https://velog.io/@subin_k/%EB%9F%B0%ED%83%80%EC%9E%84%EA%B3%BC-%EC%BB%B4%ED%8C%8C%EC%9D%BC-%ED%83%80%EC%9E%84%EC%9D%98-%EC%A0%95%EC%9D%98%EC%99%80-%EC%B0%A8%EC%9D%B4)
